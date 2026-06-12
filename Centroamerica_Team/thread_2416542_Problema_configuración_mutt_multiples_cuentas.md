---
title: "Problema configuración mutt multiples cuentas"
date: 2019-04-11
forum: Centroamerica Team
---

### Post by adroc2 on 2019-04-11
Buenos días, estoy intentando configurar mutt para conectarse a diversas cuentas.

Tengo las configuraciones en distintos archivos, los cuales cargo mediante una macro. No obstante, a pesar de que carga las configuraciones, me sigue mostrando los mensajes de la primera cuenta. Alguna idea de por que?

```
muttrc
--------------------
# Opciones
set mail_check = 600
set imap_keepalive = 900
set ssl_starttls = yes
set send_charset = 'utf-8'
set assumed_charset = 'iso8859-1'
set editor = "vim -c 'set syntax=mail ft=mail enc=utf-8'"
set move = no
set sort = threads
set strict_threads = yes
unset copy
set delete = yes
set followup_to
unset force_name
set include
set mime_forward = ask-yes
set recall = no
set reply_regexp = "^((aw|antw.?|antwort|re|r e|r?f|sv):[ \t]*)*"
unset save_name
unset tilde
set beep_new
set sidebar_visible = yes
set sidebar_width = 30
set sidebar_short_path = yes 
set sidebar_folder_indent
```


```
# Atajos de teclado
bind index G imap-fetch-mail
bind index j sidebar-prev
bind index k sidebar-next
bind index i sidebar-open

```

```
# Cuenta por defecto
source ~/.mutt/gmx/gmx.conf
```


```
# Hooks a cuentas
folder-hook 'Cuenta GMX' ' source ~/.mutt/gmx/gmx.conf'
folder-hook 'Cuenta Gmail' ' source ~/.mutt/gmail/gmail.conf'
```


```
# Macros para cambiar de cuenta
macro index <f2> '<sync-mailbox><enter-command>source ~/.mutt/gmx/gmx.conf<enter><change-folder>!<enter>'
macro index <f3> '<sync-mailbox><enter-command>source ~/.mutt/gmail/gmail.conf<enter><change-folder>!<enter>'
```


```
gmx.conf
--------------------
set imap_user = "xxx@gmx.com"
set imap_pass = "xxx"
set smtp_url = "smtp://xxx@gmx.com@smtp.gmx.com:465/"
set smtp_pass = "xxx"
set from = "xxx@gmx.com"
set realname = "xxx"
set folder = "imaps://imap.gmx.com:993"
set spoolfile = "+INBOX"
set postponed = "+INBOX/Drafts"
set header_cache = ~/.mutt/gmx/cache/headers
set message_cachedir = ~/.mutt/gmx/cache/bodies
set certificate_file = ~/.mutt/gmx/certificates
unset imap_passive


mailboxes "=INBOX"
mailboxes "=INBOX/Importantes"
```




```
gmail.conf
--------------------
set imap_user = "xxx@gmail.com"
set imap_pass = "xxx"
set smtp_url = "smtp://xxx@gmail.com@smtp.gmail.com:465/"
set smtp_pass = "xxx"
set from = "xxx@gmail.com"
set realname = "xxx"
set folder = "imaps://imap.gmail.com:993"
set spoolfile = "+INBOX"
set postponed = "+INBOX/Drafts"
set header_cache = ~/.mutt/gmail/cache/headers
set message_cachedir = ~/.mutt/gmail/cache/bodies
set certificate_file = ~/.mutt/gmail/certificates
unset imap_passive


mailboxes "=INBOX"
```

---

