---
title: "&quot;startx&quot; question plz reply (does not work)"
date: 2009-10-20
forum: Desktop Environments
---

### Post by Eremis on 2009-10-20
Hi everybody!

I just downloaded debian 5.0, and I am trying to do a custom install with fluxbox as the desktop environment... (I just want to learn in the process)
I have been following this tutorial: [http://www.go2linux.org/installing-a-light-linux-operating-system-debian-fluxbox](http://www.go2linux.org/installing-a-light-linux-operating-system-debian-fluxbox)

First time I ran "startx" nothing happened then I realised I need to install "x-window-system" so I did "sudo apt-get install x-window-system" and it installed it... (BTW yes I have sudo install correctly) but now when I run "startx" the screen turns grayish, and then it exits out with a message (I attached a screenshot to show you the error)... :confused:

Does anybody have any ideas? Plz reply... Any info will be helpfull

Also, I am using VirtualBox to do everything.... while I am running ubuntu 9.04

---

### Post by earthpigg on 2009-10-21
try this:

> xinit

and if you want X to start automatically, consider installing a graphical display manager such as GDM (used by ubuntu) or slim and configuring it to run at boot. <-- one of the first significant changes Ubuntu made from Debian (and most linux distros) was replacing traditional runlevel and init.d stuff with Ubuntu's own 'upstart'.... so the process is likely different.

may want to consider looking into a Debian mailing list or forum. for userland stuff like apt-get, it is very similar.

for low level stuff like daemons and initial system configuration, the two are worlds apart and the ubuntu experience and knowledge many of us have will do you zero good.

---

### Post by Eremis on 2009-10-21
Do you know of any tutorials where it shows how to configure GDM?

---

### Post by earthpigg on 2009-10-21
> **Eremis said:**
> Do you know of any tutorials where it shows how to configure GDM?

in Ubuntu, it configures itself dynamically and instantly upon install, and when new software relevant to the job done by GDM is installed.

---

