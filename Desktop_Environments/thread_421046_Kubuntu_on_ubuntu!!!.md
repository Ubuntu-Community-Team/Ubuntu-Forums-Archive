---
title: "Kubuntu on ubuntu!!!"
date: 2007-04-24
forum: Desktop Environments
---

### Post by mandela on 2007-04-24
yeah its me again..I was just relishing from my efforts when I ran into this. Actually, i just want to know. After installing KDE (which I guess is Kubuntu) on my ubuntu GNOME, I logged in with it and I kinda ran the upgrade thing and now its downloading the kubuntu Feisty 7.04. what i wanna know is this, Will the kubuntu wipe off Ubuntu Edgy that was on my system?

---

### Post by Aetherius on 2007-04-24
nope,

the only difference in kubuntu and ubuntu is the metapackages ubuntu-desktop and kubuntu-desktop

these packages install a load of apps each, kate/gedit, totem/kaffeine, rythymbox/amarok they can all coexist quite peacefully and you can choose which you wan to use at login (click sessions)

Aeth

---

### Post by mandela on 2007-04-24
> **Aetherius said:**
> nope,
these packages install a load of apps each, kate/gedit, totem/kaffeine, rythymbox/amarok they can all coexist quite peacefully and you can choose which you wan to use at login (click sessions)
Aeth
hufffff..i'm so relieved..thanks pal....one more thing though, i'm having some difficulties in installing themes for my desktops. i can even seems to find any.

---

### Post by Aetherius on 2007-04-24
[http://www.gnome-look.org](http://www.gnome-look.org) or [http://www.kde-look.org](http://www.kde-look.org) for themes, you can also check out [http://art.gnome.org](http://art.gnome.org)

metacity themes are the window decorator, ie the frame and whatnot

gtk themes are controls and elements within GUI's

just download the files (usually .tar.gz) open up the theme dialog (System >> Preferences >> Theme) and drag the files onto it to install.

KDE themes are different and I can't really remember how they work at the minute..... I'll get back to ya

---

### Post by mandela on 2007-04-24
> **Aetherius said:**
> just download the files (usually .tar.gz) open up the theme dialog (System >> Preferences >> Theme) and drag the files onto it to install.
KDE themes are different .. I'll get back to ya

you are so so nice...i think you are a genius. your explanations are very clear. thanks a million. i will be waiting.

---

### Post by Aetherius on 2007-04-24
No problem mate

As i said I can't remember much about KDE themes, been a while since i've used KDE. (I much prefer gnome at the moment) but heres a little thing I found at [http://www.KDE-look.org](http://www.KDE-look.org) that might help 

[http://www.kde-look.org/help/index.php?type=40](http://www.kde-look.org/help/index.php?type=40)

EDIT: To install the KDE theme manager just type the following in the terminal

> sudo apt-get install kdetheme

or open up synaptic and look for kdetheme

---

### Post by mandela on 2007-04-24
I said that u r a genius. bang and straight to the point. Have you ever tried to be a lecturer? Give it a try pls. you are simply amazing. it all working according to ur instructions. 

One more thing...after the installation, my system restarted and on the GRUB screen i found all these..are they supposed to be there?

Ubuntu kernel 2.6.20-15 -generic
Ubuntu kernel 2.6.20-15 -recovery mode
Ubuntu kernel 2.6.17-11 -generic
Ubuntu kernel 2.6.17-11 -recovery mode
Ubuntu kernel 2.6.17-10 -generic
Ubuntu kernel 2.6.17-10 -recovery mode
ubuntu memtest 86+
---------------------------
Windows XP 
I normally dual boot but I had the impression that it should have removed the obsolete ubuntu installations right?

---

### Post by Aetherius on 2007-04-24
Each ubuntu entry on the GRUB menu is the same installation but with different kernel versions.

Ubuntu automatically records any updates to the kernel and appends this to the grub menu you see at boot, allowing you to quickly and easily go back to a previous kernel version if the new one causes any problems.

;)

---

### Post by mandela on 2007-04-24
> **Aetherius said:**
> Each ubuntu entry on the GRUB menu is the same installation but with different kernel versions.
yeah..now I get it. thanks a lot.sorry for taking your time.

---

