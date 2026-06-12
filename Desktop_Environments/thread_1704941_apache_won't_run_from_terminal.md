---
title: "apache won't run from terminal"
date: 2011-03-11
forum: Desktop Environments
---

### Post by edu2004eu on 2011-03-11
hello. i'm pretty new to ubuntu and i can't get apache to run from the terminal, it gives me the "apache2: bad user name ${APACHE_RUN_USER}" error, if i run apache from /etc/init.d/apache and simply by typing apache2 -k restart. however apache automatically starts by itself on boot, which i find weird.

so to fix the username error, i made apache it's very own user and group and then it gave me another error about not being able to bind to [:::]:80 or something like that. just want to mention that i edited the /etc/apache2/apache2.conf file. is that the right one? and how come apache can run at boot-time but not when i want it to?

another thing... is there an apache gui thing where i can start/stop it? (in earlier versions there was the "service control" thing on ubuntu, but now i can't seem to find it.

if anyone could help me answer as many of these questions, that would be much appreciated. thank you.

---

