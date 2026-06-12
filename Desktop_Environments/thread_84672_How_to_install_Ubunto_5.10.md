---
title: "How to install Ubunto 5.10?"
date: 2005-10-31
forum: Desktop Environments
---

### Post by skoen on 2005-10-31
Iv come to the place where i login, it looks like dos.
How do i continiuo after this? iv logedin but what shall i do after that?

---

### Post by Vidar on 2005-10-31
Try entering "startx" (without the quotes). That should bring up the x-server (and with it a shiny graphical user interface).

If that don't work, please post the output of the command here and Im sure somebody will be able to help you.

Problarbly something is wrong with your xorg-config though, since it didn't start X automatically when booting up.

---

### Post by skoen on 2005-10-31
i wrote startx and this is wat came up:


startx

creating authority file /home/greger/.serverauth.9637
/ect/x11/xinit/xserverrc: line2: /usr/bin/x11/x: file or directory dosent exist


(says that 2 times, then:

xinit: Server error.

---

### Post by Remmelas on 2005-10-31
looks like the install was not done as a 'desktop' install.  try ```
sudo apt-get install ubuntu-desktop
```

---

### Post by cstudent on 2005-10-31
Is it possible that he is trying to install Ubuntu Server by mistake?

---

### Post by skoen on 2005-10-31
when i wrote sudo atp-get install ubunto-desktop it says that it couldnt find package with ubunto-desktop.

---

### Post by skoen on 2005-10-31
when it first asked me to write something to start the install from the begining it sad server.

but now iv redone it with linux, and il get back to you if i need help. please stay online here for atleast 1 more hour :D

---

### Post by unclben on 2005-10-31
[QUOTE=skoen]when i wrote sudo atp-get install ubunto-desktop it says that it couldnt find package with ubunto-desktop.[/QUOTE]Check your spelling, skoen. It is 'ubuntu', not 'ubunto'. :)

---

