---
title: "KSystemlog"
date: 2006-04-21
forum: Desktop Environments
---

### Post by bertpatt on 2006-04-21
Ksystemlog has never shown the boot log.
It always says that there is no such file.
If I go into the settings and change the name of the file boot.log to something else it always goes back to boot.log. Yet there is no such file on the computer.
Anyone know how to generate the boot log into a file when the computer boots?

---

### Post by DeadEyes on 2006-04-21
I noticed the same thing on my machine. I wasn't that bothered so didn't do anything about it, but I would imagine that if you created an empty **boot.log** file the KSystemLog should pick it up and append to it. I imagine it goes somewhere like /var/log

---

