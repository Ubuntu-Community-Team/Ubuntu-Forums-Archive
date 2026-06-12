---
title: "Firestarter and Start-up"
date: 2006-09-25
forum: Desktop Environments
---

### Post by tombiz on 2006-09-25
I would like to have Firestarter to load when I boot to Ubuntu. What do I need to do, or what is the command that I need to use to set-up automatic loading of Firestarter.

Thanks.

---

### Post by Monstroxus on 2006-09-25
If you installed Firestarter, it will automatically run by itself. Just have a look at all those lines when you start up Ubuntu, firestarter should be mentioned as well. There will be no icon while running Ubuntu, unless you manually "start" firestarter by clicking the shortcut. (like mentioned before, firestarter should already be running, only when you want to see an icon, which is a red circle with a lightning bold, you have to "start" firestarter by clicking the shortcut.)

---

### Post by tombiz on 2006-09-25
Is there a log file that would show me that Firestarter loads if I don't see it during the boot process?

---

### Post by ChadMMc on 2006-09-25
As far as I can tell, when firestarter is installed your firewall is up once you boot. (tested this with shields up web site, and my system is in full stealth mode).
But if you want the firestarter interface to come up when you boot, I think you would go to 
system->preferences->sessions, and then choose the startup programs tab and add firestarter to the list of programs there. 
Note: Since firestarter is an admin level program the command should be 'gksudo firestarter' and it will ask for your password a second time during the boot.

Hope this helps.

---

### Post by Anduu on 2006-09-26
Just to be clear...Firestarter is not a firewall.It is merely a graphical front-end to Linux' built in firewall aka iptables.

It allows you to modify the firewall's settings.

---

### Post by graigsmith on 2006-09-26
firestarter is basically a front end for the built in firewall in linux called iptables.

you dont need to run firestarter to have it block things.  but if you wanna see what its blocking, you have to have it open.

---

