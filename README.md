# fsr_yahyatahiri
A website featuring a student's academic transcript.
[fiche_etudiant_complete.html](https://github.com/user-attachments/files/29356875/fiche_etudiant_complete.html)

<style>
  * { box-sizing: border-box; margin: 0; padding: 0; }
  .page { max-width: 860px; margin: 0 auto; padding: 0 0 2rem; }
  .header {
    display: flex; align-items: center; gap: 16px;
    padding: 16px 24px;
    background: var(--color-background-primary);
    border-bottom: 2px solid #1a5276;
  }
  .header-logo {
    width: 72px; height: 72px; background: #1a5276; border-radius: 50%;
    display: flex; align-items: center; justify-content: center; flex-shrink: 0;
  }
  .header-logo svg { width: 44px; height: 44px; }
  .header-text h1 { font-size: 17px; font-weight: 500; color: #1a5276; line-height: 1.3; }
  .header-text p { font-size: 12px; color: var(--color-text-secondary); margin-top: 2px; }
  .tab-nav {
    display: flex; border-bottom: 0.5px solid var(--color-border-secondary);
    background: var(--color-background-secondary);
  }
  .tab-btn {
    flex: 1; padding: 12px 8px; font-size: 13px; font-weight: 500;
    border: none; background: transparent; cursor: pointer;
    color: var(--color-text-secondary);
    border-bottom: 2px solid transparent; transition: all 0.15s;
  }
  .tab-btn.active { color: #1a5276; border-bottom: 2px solid #1a5276; background: var(--color-background-primary); }
  .section { display: none; padding: 20px; }
  .section.active { display: block; }
  .card {
    background: var(--color-background-primary);
    border: 0.5px solid var(--color-border-tertiary);
    border-radius: var(--border-radius-lg);
    padding: 20px; margin-bottom: 16px;
  }
  .student-top { display: flex; align-items: center; gap: 20px; margin-bottom: 20px; }
  .avatar { width: 88px; height: 88px; border-radius: 50%; border: 2px solid #1a5276; overflow: hidden; flex-shrink: 0; }
  .avatar img { width: 100%; height: 100%; object-fit: cover; object-position: center top; }
  .student-name { font-size: 20px; font-weight: 500; color: var(--color-text-primary); }
  .student-badge { display: inline-block; margin-top: 6px; background: #d6eaf8; color: #1a5276; font-size: 12px; padding: 3px 10px; border-radius: 20px; }
  .divider { height: 0.5px; background: var(--color-border-tertiary); margin: 16px 0; }
  .info-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
  .info-item { display: flex; flex-direction: column; gap: 2px; }
  .info-label { font-size: 12px; color: var(--color-text-secondary); }
  .info-value { font-size: 14px; color: var(--color-text-primary); font-weight: 500; }
  .sem-title { font-size: 15px; font-weight: 500; color: var(--color-text-primary); margin-bottom: 14px; display: flex; align-items: center; gap: 8px; }
  .notes-table { width: 100%; border-collapse: collapse; font-size: 13px; }
  .notes-table thead tr { background: #1a5276; }
  .notes-table thead th { padding: 10px 12px; text-align: center; font-weight: 500; color: white; border: none; }
  .notes-table thead th:first-child { text-align: left; border-radius: 6px 0 0 0; }
  .notes-table thead th:last-child { border-radius: 0 6px 0 0; }
  .notes-table tbody tr:nth-child(even) { background: var(--color-background-secondary); }
  .notes-table tbody tr:nth-child(odd) { background: var(--color-background-primary); }
  .notes-table td { padding: 10px 12px; border-bottom: 0.5px solid var(--color-border-tertiary); color: var(--color-text-primary); text-align: center; }
  .notes-table td:first-child { text-align: left; font-weight: 500; }
  .notes-table tr:last-child td { border-bottom: none; }
  .note-badge { display: inline-block; padding: 3px 10px; border-radius: 20px; font-size: 12px; font-weight: 600; }
  .note-good { background: #eaf3de; color: #2d6a0f; }
  .note-mid  { background: #faeeda; color: #7a4500; }
  .note-fail { background: #fce8e8; color: #a32d2d; }
  .coeff-badge { display: inline-block; background: #eaf0fb; color: #1a5276; padding: 2px 8px; border-radius: 20px; font-size: 12px; font-weight: 600; }
  .footer-row td { background: #1a5276 !important; color: white !important; font-weight: 600; border: none !important; padding: 10px 12px; }
  .moy-box {
    display: flex; justify-content: space-between; align-items: center;
    margin-top: 14px; padding: 14px 18px;
    background: linear-gradient(135deg, #1a5276, #2471a3);
    border-radius: 10px; color: white;
  }
  .moy-label { font-size: 13px; opacity: 0.85; }
  .moy-val { font-size: 22px; font-weight: 700; }
  .mention-box {
    display: flex; justify-content: space-between; align-items: center;
    margin-top: 8px; padding: 10px 18px;
    background: var(--color-background-secondary); border-radius: 10px;
  }
  .mention-label { font-size: 13px; color: var(--color-text-secondary); }
  .mention-val { font-size: 15px; font-weight: 600; color: #1a5276; }
  .annee-box {
    display: flex; justify-content: space-between; align-items: center;
    margin-top: 8px; padding: 14px 18px;
    background: linear-gradient(135deg, #117a65, #1abc9c);
    border-radius: 10px; color: white;
  }
  .annee-val { font-size: 22px; font-weight: 700; }
</style>

<div class="page">
  <div class="header">
    <div class="header-logo">
      <svg viewBox="0 0 44 44" fill="none" xmlns="http://www.w3.org/2000/svg">
        <circle cx="22" cy="14" r="8" fill="white" opacity="0.9"/>
        <rect x="8" y="26" width="28" height="3" rx="1.5" fill="white" opacity="0.8"/>
        <rect x="12" y="31" width="20" height="3" rx="1.5" fill="white" opacity="0.6"/>
        <rect x="16" y="36" width="12" height="3" rx="1.5" fill="white" opacity="0.4"/>
      </svg>
    </div>
    <div class="header-text">
      <h1>Faculté des Sciences de Rabat — Université Mohammed V</h1>
      <p>Espace Étudiant · Relevé de Notes · 2025/2026</p>
    </div>
  </div>

  <div class="tab-nav">
    <button class="tab-btn active" onclick="showTab('infos',event)">👤 Infos personnelles</button>
    <button class="tab-btn" onclick="showTab('s1',event)">📘 Semestre 1</button>
    <button class="tab-btn" onclick="showTab('s2',event)">📗 Semestre 2</button>
  </div>

  <!-- INFOS -->
  <div id="tab-infos" class="section active">
    <div class="card">
      <div class="student-top">
        <div class="avatar">
          <img src="data:image/jpeg;base64,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" alt="Yahya Tahri">
        </div>
        <div>
          <div class="student-name">Yahya Tahri</div>
          <span class="student-badge">Tronc Commun Physique-Chimie · 2025/2026</span>
        </div>
      </div>
      <div class="divider"></div>
      <div class="info-grid">
        <div class="info-item">
          <span class="info-label">🎂 Date de naissance</span>
          <span class="info-value">17 février 2007</span>
        </div>
        <div class="info-item">
          <span class="info-label">📍 Ville</span>
          <span class="info-value">Rabat</span>
        </div>
        <div class="info-item">
          <span class="info-label">🎓 Filière</span>
          <span class="info-value">Tronc Commun PC</span>
        </div>
        <div class="info-item">
          <span class="info-label">📅 Année universitaire</span>
          <span class="info-value">2025 / 2026</span>
        </div>
        <div class="info-item">
          <span class="info-label">✉️ Email</span>
          <span class="info-value">yahya.tahri@etu.um5.ac.ma</span>
        </div>
        <div class="info-item">
          <span class="info-label">🏛️ Établissement</span>
          <span class="info-value">FSR — Rabat</span>
        </div>
      </div>
    </div>
  </div>

  <!-- S1 -->
  <div id="tab-s1" class="section">
    <div class="card">
      <div class="sem-title">📘 Relevé de notes — Semestre 1</div>
      <table class="notes-table">
        <thead>
          <tr>
            <th>Module</th><th>Coeff.</th><th>Session normale</th><th>Note × Coeff.</th><th>Résultat</th>
          </tr>
        </thead>
        <tbody id="s1-body"></tbody>
        <tfoot><tr class="footer-row" id="s1-footer"></tr></tfoot>
      </table>
      <div class="moy-box">
        <span class="moy-label">Moyenne générale S1</span>
        <span class="moy-val" id="s1-moy">—</span>
      </div>
      <div class="mention-box">
        <span class="mention-label">Mention S1</span>
        <span class="mention-val" id="s1-mention">—</span>
      </div>
    </div>
  </div>

  <!-- S2 -->
  <div id="tab-s2" class="section">
    <div class="card">
      <div class="sem-title">📗 Relevé de notes — Semestre 2</div>
      <table class="notes-table">
        <thead>
          <tr>
            <th>Module</th><th>Coeff.</th><th>Session normale</th><th>Note × Coeff.</th><th>Résultat</th>
          </tr>
        </thead>
        <tbody id="s2-body"></tbody>
        <tfoot><tr class="footer-row" id="s2-footer"></tr></tfoot>
      </table>
      <div class="moy-box">
        <span class="moy-label">Moyenne générale S2</span>
        <span class="moy-val" id="s2-moy">—</span>
      </div>
      <div class="mention-box">
        <span class="mention-label">Mention S2</span>
        <span class="mention-val" id="s2-mention">—</span>
      </div>
      <div class="annee-box" id="annee-box">
        <span class="moy-label">Moyenne annuelle (S1 + S2)</span>
        <span class="annee-val" id="annee-moy">—</span>
      </div>
    </div>
  </div>
</div>

<script>
function showTab(id, event) {
  document.querySelectorAll('.section').forEach(s => s.classList.remove('active'));
  document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
  document.getElementById('tab-' + id).classList.add('active');
  event.currentTarget.classList.add('active');
}

function noteBadge(n) {
  const cls = n >= 14 ? 'note-good' : n >= 10 ? 'note-mid' : 'note-fail';
  return `<span class="note-badge ${cls}">${n.toFixed(2)}</span>`;
}

function mention(m) {
  if (m >= 16) return '⭐ Très Bien';
  if (m >= 14) return '✅ Bien';
  if (m >= 12) return '👍 Assez Bien';
  if (m >= 10) return '📋 Passable';
  return '❌ Ajourné';
}

function buildTable(data, bodyId, footerId, moyId, mentionId) {
  let tbody = document.getElementById(bodyId);
  let total = 0, prod = 0;
  data.forEach(r => {
    total += r.coeff; prod += r.coeff * r.note;
    const ok = r.note >= 10;
    tbody.innerHTML += `<tr>
      <td>${r.mod}</td>
      <td><span class="coeff-badge">${r.coeff}</span></td>
      <td>${noteBadge(r.note)}</td>
      <td style="font-size:12px;color:var(--color-text-secondary)">${(r.coeff*r.note).toFixed(2)}</td>
      <td><span class="note-badge ${ok?'note-good':'note-fail'}">${ok?'Validé':'Ajourné'}</span></td>
    </tr>`;
  });
  const moy = prod / total;
  document.getElementById(footerId).innerHTML = `<td>Total</td><td>${total}</td><td></td><td style="color:white;font-size:13px">${prod.toFixed(2)}</td><td></td>`;
  document.getElementById(moyId).textContent = moy.toFixed(2) + ' / 20';
  document.getElementById(mentionId).textContent = mention(moy);
  return { moy, total };
}

const s1 = [
  { mod: 'Analyse 1',       coeff: 5, note: 10.23 },
  { mod: 'Algèbre 1',       coeff: 5, note: 15.27 },
  { mod: 'Atomistique',     coeff: 5, note: 18.10 },
  { mod: 'MDP',             coeff: 5, note: 11.63 },
  { mod: 'Thermodynamique', coeff: 4, note: 15.93 },
  { mod: 'Thermochimie',    coeff: 3, note: 10.52 },
  { mod: 'MTU',             coeff: 3, note: 17.74 },
];

const s2 = [
  { mod: 'Analyse 2',          coeff: 4, note: 13.81 },
  { mod: 'Algèbre 2',          coeff: 4, note: 14.29 },
  { mod: 'Optique géométrique',coeff: 4, note: 13.44 },
  { mod: 'Chimie en solution', coeff: 5, note: 13.89 },
  { mod: 'Liaison chimique',   coeff: 5, note: 16.72 },
  { mod: 'Électricité',        coeff: 5, note: 9.38  },
  { mod: 'Digital Skills',     coeff: 3, note: 17.23 },
];

const r1 = buildTable(s1, 's1-body', 's1-footer', 's1-moy', 's1-mention');
const r2 = buildTable(s2, 's2-body', 's2-footer', 's2-moy', 's2-mention');

// Moyenne annuelle pondérée
const totalCoeff = r1.total + r2.total;
const moyAnnuelle = (
  r1.moy * r1.total + r2.moy * r2.total
) / totalCoeff;
document.getElementById('annee-moy').textContent = moyAnnuelle.toFixed(2) + ' / 20  —  ' + mention(moyAnnuelle).replace(/^[^ ]+ /,'');
</script>
