---
title: "Can't restore NV Driver, no GUI"
date: 2009-04-28
forum: General Help
---

### Post by NiGHTSChao on 2009-04-28
*introduction*

Long story short, I installed an update for the nvidia driver on ubuntu 9.04, reboot, now I have no GUI, after doing google searches for 2 hours, trying many different commands and options, I am completely stumped and cannot get ubuntu to load the GUI anymore.

Keep in mind, I am 100% newbie when it comes to linux, so be gentle
Everytime I tried to do the whole /etc/X11/xconfig whatever stuff, it would just tell me there was no display, recovery console didn't do anything for me, etc.

So step by step, what do I need to do to restore my default NV driver for my SLIx2 8800GTS 512 cards?

Keep in mind I will not reply instantly, since I'll be in class :p
Thank you <3

---

### Post by cariboo on 2009-04-28
If you start in recovery mode you should be able to restore the default /etc/X11/xorg.conf by typing 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

at the prompt.

---

### Post by NiGHTSChao on 2009-04-28
> **cariboo907 said:**
> If you start in recovery mode you should be able to restore the default /etc/X11/xorg.conf by typing 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```at the prompt.

Didn't work.
Still stuck at the black screen.

---

### Post by NiGHTSChao on 2009-04-28
> **cariboo907 said:**
> If you start in recovery mode you should be able to restore the default /etc/X11/xorg.conf by typing 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```at the prompt.

Sorry for the bump, but it tells me:
"xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etx/X11/xorg.conf.20090428123024"

Customized is spelled wrong x'3 <3

So where do I go from here?

---

### Post by NiGHTSChao on 2009-04-28
T_T  I even tried older Nvidia drivers and still have the same result...
Please help..

---

