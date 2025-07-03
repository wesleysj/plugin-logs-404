# 📄 Plugin WordPress: Log de Erros 404 + Notificação Diária

Este plugin registra acessos a páginas 404 do seu site WordPress em um arquivo de log local e envia um **e-mail diário com o resumo** desses acessos para o e-mail do administrador do site.

---

## ✅ Funcionalidades

- Detecta acessos a páginas 404 usando `is_404()`.
- Registra as informações em arquivos de log organizados por data (`/logs/erros-404-YYYY-MM-DD.log`).
- Evita múltiplos registros do mesmo visitante com uso de `cookie` leve (10 minutos).
- Envia um **resumo diário por e-mail** automaticamente via cron.
- Usa o **e-mail do administrador do WordPress** como destinatário.

---

## 📁 Estrutura do plugin

```

/plugin-logs-404/
├── plugin-logs-404.php
└── logs/

```

> A pasta `logs/` será criada automaticamente, mas você pode criá-la manualmente com permissão de escrita (755 ou 775).

---

## ⚙️ Instalação

1. Faça o upload da pasta `plugin-logs-404` para o diretório `/wp-content/plugins/`.
2. Ative o plugin no painel do WordPress (`Plugins → Plugins instalados`).
3. Pronto! O plugin começará a registrar os erros 404 automaticamente.

---

## 📧 Sobre o envio de e-mail

- O e-mail é enviado **uma vez por dia**, contendo todas as URLs 404 acessadas.
- É usado o **sistema de cron do WordPress** (evento diário `log404_cron_diario`).
- O destinatário é obtido via `get_option('admin_email')`.

---

## 🔐 Segurança e desempenho

- Sem uso de sessões (`session_start()`), garantindo compatibilidade com cache.
- Baixo impacto de performance: os registros são feitos com `error_log()` em arquivos locais.
- Os dados são mantidos por apenas 1 dia e apagados após o envio do e-mail.

---

## 🔄 Cron desativado ao desativar o plugin

Ao desativar o plugin, o cron de envio é cancelado automaticamente para evitar tarefas desnecessárias.

---

## 📌 Personalizações futuras

Pretendemos fazer, no futuro:
- Interface de configurações no admin.
- Filtrar bots e crawlers.
- Enviar para múltiplos e-mails ou via Webhooks (Slack, Discord etc).
- Armazenamento dos logs no banco de dados.

---

## 📜 Licença

Este plugin está disponível sob a licença [MIT](LICENSE) — sinta-se livre para modificar, usar e compartilhar.

---

## ✉️ Suporte

Em caso de dúvidas ou sugestões, sinta-se à vontade para abrir uma *issue* ou enviar um PR. 😄
