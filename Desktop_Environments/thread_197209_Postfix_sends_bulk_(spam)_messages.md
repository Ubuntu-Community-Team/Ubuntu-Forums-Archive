---
title: "Postfix sends bulk (spam) messages ??"
date: 2006-06-15
forum: Desktop Environments
---

### Post by xpmaniac4ever on 2006-06-15
Hi. Today I installed Postfix mail server on my server and when I use it to send mails to any Yahoo account, they appear in the Bulk folder of the destination, where spam resides. Why does this happen and how can I prevent it ?

---

### Post by pwaldo on 2006-06-15
Does sending mail anywhere else work?

---

### Post by xpmaniac4ever on 2006-06-15
[QUOTE=pwaldo]Does sending mail anywhere else work?[/QUOTE]

It works sending mail, but it`s just that Yahoo puts the mail into the Bulk folder thinking it`s spam, while it`s not. How can I avoid this ?

---

### Post by ranf on 2006-06-16
How is your postfix setup?

If it delivers directly to the yahoo SMTP server, they see that your'e a dialup box and classify your mail as spam.

```
sudo dpkg-reconfigure postfix
```
and choose "Internet site with smarthost". Use your email providers SMTP host.

---

