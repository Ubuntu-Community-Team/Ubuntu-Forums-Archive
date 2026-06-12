---
title: "Nautilus and fpt connectins"
date: 2005-05-22
forum: Desktop Environments
---

### Post by joehanes on 2005-05-22
Hello,

i would like to use the "connect to server"-feature of nautilus. Unfornunately, I have to do the login in an unusual format:
 > user@domain@ftp.domain

nautilus seems to have a problem with that. It parses the string to: > user%40domain@domain.

This leads to the result, that the username is not accepted by the server.

Is there a way to escape the @?

cheers

Joe

---

### Post by khc on 2005-05-22
This is probably an upstream bug, you should probably file a bug at gnome.org.

---

### Post by joehanes on 2005-05-22
As far as I know, there has already been signed a report.

When enter the ftp-adress directely in the adress bar, nautilus prompts for username  and password. Then it works.

Further I found out, and it has already been posted once or twice, once an ftp connection is established, nautilus offers to edit a file (gedit ect) but the file cannot be saved through the editing program. (e.g gedit opens the file read-only, bluefish crashed while saving).

A workaround I figured out, is to use gFTP and enter (gedit ect) as a default editor. This way, a file can be edited online, which is very useful in web-development. A minor flaw is, that gFtp assigns a new process to every opened file. So to edit 5 files, I have 5 gedit windows opened.

Any other ideas?

cheers

Joe

---

### Post by Sam on 2005-05-22
You have to use the standard URI format:
[ftp://username:password@domain](ftp://username:password@domain)

---

### Post by joehanes on 2005-05-22
Using the standard uri format,
the above described problem occurs.

---

### Post by Sam on 2005-05-22
[QUOTE=joehanes]Using the standard uri format,
the above described problem occurs.[/QUOTE]
Change "Service type" to "Custom location".
It's a bit unsecure, as you password is clearly displayed when you open the remote ftp.

---

### Post by Statik on 2005-08-30
How does one call Bluefish this way so that the file is uploaded when you hit save, not when you close bluefish?

Statik

---

