---
title: "i need password root"
date: 2005-06-06
forum: Desktop Environments
---

### Post by aciid on 2005-06-06
i current ubuntu version 5.04, but i dont know password as root. setup installation : default.

---

### Post by Alexander Kirillov on 2005-06-06
[QUOTE=aciid]i current ubuntu version 5.04, but i dont know password as root. setup installation : default.[/QUOTE]
 There is no root password by default. Read this:
[http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

---

### Post by iamkmaniam on 2005-06-06
Ubuntu uses the sudo command to gain root privalages. If you need root access use the root terminal and enter the passowrd for the user that you used when you set up
your system. If you truly need a root password type at at a terminal window
"sudo passwd root"  
 without the quations marks, then hit enter it will then ask you for a password and then again to coinfirm the password. from then on you could type su - at the CLI to gain root privalages. There are other steps that are needed to make sure the system remains secure, but this will get you a root password.

---

