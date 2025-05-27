- 👋 Hi, I’m @vidacheck-site
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
vidacheck-site/vidacheck-site is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Agendamento VidaCheck</title>
<style>
  body {
    font-family: 'Segoe UI', sans-serif;
    background: #f0f4f8;
    margin: 0; padding: 0;
    display: flex; justify-content: center; align-items: flex-start; padding-top: 40px;
  }
  .container {
    background: white;
    padding: 30px;
    border-radius: 12px;
    box-shadow: 0 4px 15px rgba(0,0,0,0.1);
    width: 100%;
    max-width: 480px;
  }
  .logo {
    text-align: center;
    margin-bottom: 20px;
  }
  .logo img {
    max-height: 70px;
  }
  h1 {
    color: #0f60a5;
    text-align: center;
    margin-bottom: 10px;
  }
  p.intro {
    text-align: center;
    font-size: 14px;
    color: #555;
    margin-bottom: 20px;
  }
  label {
    display: block;
    margin-top: 15px;
    color: #333;
    font-weight: 600;
  }
  input[type="date"], input[type="time"], select {
    width: 100%;
    padding: 10px;
    margin-top: 6px;
    border: 1px solid #ccc;
    border-radius: 6px;
    font-size: 15px;
  }
  .radio-group, .checkbox-group {
    margin-top: 10px;
  }
  .radio-group label, .checkbox-group label {
    display: block;
    margin-bottom: 5px;
    font-weight: normal;
  }
  button {
    margin-top: 25px;
    width: 100%;
    padding: 14px;
    border: none;
    background: #0f60a5;
    color: white;
    font-size: 16px;
    border-radius: 6px;
    cursor: pointer;
    font-weight: bold;
  }
  button:hover {
    background: #094a83;
  }
  .resultado {
    margin-top: 25px;
    background: #e2f1ff;
    padding: 15px;
    border-radius: 6px;
    color: #155fa0;
    display: none;
  }
</style>
</head>
<body>

<div class="container">
  <div class="logo">
    <img src="SUA_LOGO_AQUI.png" alt="Logo VidaCheck" />
  </div>

  <h1>Agendamento de Exames</h1>
  <p class="intro">
    A <strong>VidaCheck</strong> oferece exames rápidos, confiáveis e com o apoio da Inteligência Artificial. Escolha a melhor data, horário e tipo de atendimento.
  </p>

  <form id="formAgendamento">
    <label for="data">Data do exame:</label>
    <input type="date" id="data" name="data" required min="" />

    <label for="hora">Hora do exame:</label>
    <input type="time" id="hora" name="hora" required />

    <label>Local do atendimento:</label>
    <div class="radio-group">
      <label><input type="radio" name="local" value="Domicílio" required /> Atendimento em domicílio</label>
      <label><input type="radio" name="local" value="Laboratório" /> Atendimento no laboratório</label>
    </div>

    <label>Exames rotineiros:</label>
    <div class="checkbox-group">
      <label><input type="checkbox" name="exames" value="Hemograma" /> Hemograma</label>
      <label><input type="checkbox" name="exames" value="Glicemia" /> Glicemia</label>
      <label><input type="checkbox" name="exames" value="Colesterol" /> Colesterol</label>
      <label><input type="checkbox" name="exames" value="Urina" /> Urina</label>
      <label><input type="checkbox" name="exames" value="Triglicerídeos" /> Triglicerídeos</label>
    </div>

    <button type="submit">Agendar Exame</button>
  </form>

  <div class="resultado" id="resultado"></div>
</div>

<script>
  // Define hoje para data mínima do input date
  const dataInput = document.getElementById('data');
  const hoje = new Date().toISOString().split('T')[0];
  dataInput.setAttribute('min', hoje);

  const form = document.getElementById('formAgendamento');
  const resultado = document.getElementById('resultado');

  form.addEventListener('submit', function(event) {
    event.preventDefault();

    const data = dataInput.value;
    const hora = document.getElementById('hora').value;
    const local = form.local.value;
    const exames = Array.from(form.querySelectorAll('input[name="exames"]:checked')).map(e => e.value);

    if (exames.length === 0) {
      alert('Por favor, selecione pelo menos um exame.');
      return;
    }

    resultado.style.display = 'block';
    resultado.innerHTML = `
      <h3>Agendamento Confirmado!</h3>
      <p><strong>Data:</strong> ${data}</p>
      <p><strong>Hora:</strong> ${hora}</p>
      <p><strong>Local:</strong> ${local}</p>
      <p><strong>Exames:</strong> ${exames.join(', ')}</p>
      <p>Obrigado por escolher a <strong>VidaCheck</strong>!</p>
    `;

    form.reset();
    dataInput.setAttribute('min', hoje);
  });
</script>

</body>
</html>
