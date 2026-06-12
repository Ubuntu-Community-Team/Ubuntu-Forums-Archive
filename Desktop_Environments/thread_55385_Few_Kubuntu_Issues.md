---
title: "Few Kubuntu Issues"
date: 2005-08-08
forum: Desktop Environments
---

### Post by fmpuk on 2005-08-08
I am trying to do a few things with my new installation of Kubuntu  and i can't help but feel I have a dodgy install? These are the problems I have had:
When I try to add Universe to my software sources I get this error:
```
root@laptop:/home/edd # sudo synaptic
sudo: unable to lookup laptop via gethostbyname()
sudo: synaptic: command not found
```
I also get that error in the middle (unable to lookup laptop..) whenever I run a sudo command. 

Next problem: When I right click the K menu icon, and select Menu Editor, the menu editor flashes for a split second saying it is loading then it just vanishes and nothing loads. 

Another Problem: When I run: 
EDITOR=kwrite sudo visudo
I get the following error:
```
root@laptop:/home/edd # EDITOR=kwrite sudo visudo
sudo: unable to lookup laptop via gethostbyname()
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kwrite: cannot connect to X server :0.0
visudo: sudoers file unchanged
```

What could be causing all these errors? 
Thanks a lot :)
Few points, I used to have Mandriva LE 2005 installed, so I am re using my home partition. I ent sure whether that could effect it, maybe leaving files from Mandriva on the home partition maybe? Just thought I'd mention that in case.

---

### Post by ltmon on 2005-08-08
It seems you have created a root user and logged in as root, which by default will not allow you to run X11 (graphical) programs.  There is a way you can configure around this, but the best way might be to simply go back to your regular user and use sudo when you need admin privileges.  This should fix some of your problems.

L.

---

### Post by fmpuk on 2005-08-08
Ahhh thanks, that did the trick :)

---

### Post by fmpuk on 2005-08-08
[QUOTE=fmpuk]Ahhh thanks, that did the trick :)[/QUOTE]
 Oh, that did solve all but the one problem I mentioned. Does anyone have any idea what is going on with my menu editor?

---

