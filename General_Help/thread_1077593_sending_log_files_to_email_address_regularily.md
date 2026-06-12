---
title: "sending log files to email address regularily"
date: 2009-02-22
forum: General Help
---

### Post by tudorbob on 2009-02-22
Hi would anyone know how I could send the content of a folder to a predefined email on a regular basis on ubuntu?
tudor

---

### Post by ellgor on 2009-02-23
Hi, 

Take a look at Kontact/Kmail, they have the functions you mention.

Regards, Ellgor.

---

### Post by dcstar on 2009-02-24
> **tudorbob said:**
> Hi would anyone know how I could send the content of a folder to a predefined email on a regular basis on ubuntu?
tudor

Install the **mailx** and **postfix** packages, and then set up a cron job to use the "mail" command to do it.

BTW, the **logcheck** package mails system log files automatically to the root user in its default setup.

---

