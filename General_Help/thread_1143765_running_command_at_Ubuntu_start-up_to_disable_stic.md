---
title: "running command at Ubuntu start-up to disable stick-mouse"
date: 2009-04-30
forum: General Help
---

### Post by Bamshad on 2009-04-30
Hi guys,

I found this nice command line which disables my Stick Mouse (the pointer in the middle of my Toshiba Laptop keyboard)  The command line is:** _sudo modprobe -r psmouse_**

Instead of manually typing this in Terminal, I tried making it run automatically, so that every time I log on, the command line would stop my Stick Mouse and let me do the normal mouse stuff with my USB mouse. 

Does anyone know how I can make this command line executable at start-up? I have tried several ways of doing it but since my knowledge is incomplete of such matters in Ubuntu like "sudo", and "executables", and "sessions", I keep bumping in to errors. 

How can I run my command line at start-up and actually have it executed?

Really appreciate your help!! Thanks a lot!

---

### Post by caljohnsmith on 2009-04-30
You could stick that command in /etc/rc.local, and then it will be executed as root on start up after all the other rc.X directories are executed by the system. Since any commands you put in rc.local are executed as root, you don't need the "sudo" in front of it. So to be more specific, you can first open rc.local by doing:
```
gksudo gedit /etc/rc.local
```
And then add:
```
modprobe -r psmouse
```
Before the "exit 0" line at the end of that file. Then reboot, and let me know if that does the trick for you. :)

John

---

