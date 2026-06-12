---
title: "GUI Fails to load (past login screen)"
date: 2008-05-13
forum: Desktop Environments
---

### Post by dgersting on 2008-05-13
What I have is the vanilla Ubuntu Server (8.04) with the Xubuntu GUI over it. (I used "sudo apt-get install xubuntu-desktop" to install it)

My system starts up fine and presents the gui login screen. Upon login, it simply opens a terminal window and stops. I can operate within the terminal fine, but I am never presented with a 'normal' desktop with icons and such. Did I miss something in the install? Anyone have any ideas?



Thanks for taking a look!

---

### Post by redman99 on 2008-05-14
Hi,
I also have this problem.
I have tried both the desktop install and the server install and they give me the same issue.

First boot after installing server, and then installing gnome I got through ok.  Then, after rebooting after installing some apps (openOffice, some codecs for movies) i get this same problem.
Terminal is ok.  Just get background.

Tried resetting gnome, but still nothing.  
I would also appreciate any help.

Cheers
Chris

---

### Post by twig43 on 2008-05-14
i have the same problem but im using a desktop edition
i was installing something and my computer shut down and now i cant load my window manager after i login (just shows blank screen with frozen mouse)
im pretty sure something got messed up in the abrupt shutdown

---

### Post by Régis B. on 2008-05-14
Pretty much the same problem here. I installed Xubuntu on a Hardy Kubuntu distribution and cannot access the desktop in any way. The only "graphical command" that works is Alt+F4, which allows me to logout.

I had the same problem with Gutsy but now I do want to solve it, except I don't have a clue how.

---

### Post by redman99 on 2008-05-14
Guys,
I installed the kununtu desktop, and i can get in no problem.
So it looks like its some problem with the gnome session.

Will play around with kubuntu for the time being then...
:)

---

### Post by NightwishFan on 2008-05-14
try:
```
startx
```
(if you can type when get to the terminal upon trying to log in to xfce)

---

### Post by dgersting on 2008-05-17
Sorry for the delay in my response; I am currently in the process of moving, and didn't have access to the system for the past few days.

[QUOTE=redman99]So it looks like its some problem with the gnome session.[/QUOTE]I have tried logging in using all the different sessions available with the same result.



[QUOTE=NightwishFan]try:```
startx
```[/QUOTE]
Tried this with the following results;
```

sudo startx

Fatal server error:
Server is already active for display 0

```

---

### Post by NightwishFan on 2008-05-17
I see not sure. Try to rename the configuration files for xfce4, then reboot and log in again.

Should be a hidden file in your home folder like .xfce4 (i am not exactly sure) Rename to .xfce4backup

---

### Post by jaripetteri on 2008-05-18
I manage to get server kernel and xubuntu-desktop to run by installing xubuntu from desktop installation cd and after successful installation change linux-generic to linux-server. This still doesn't fix the non working xubuntu-desktop installation.

---

### Post by uzi09 on 2008-06-07
similar problem here too.

originally an ubuntu 8.04 hardy heron desktop load, installed xubuntu-desktop through synaptics > select packages by task > xubuntu-desktop.

it worked fine and all, but mines actually crashed a few times on various occasions (a few times while using RealVNC to connect to another machine, another few times while playing an flv in mplayer, and i think a couple times it just went without me even doing anything special).

i would then log into my gnome session, reinstall xubuntu-desktop and then i could log in again.

i don't even get a terminal, once i log in, i just get my arrow, and the blue xfce background

[https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/237248](https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/237248)

---

