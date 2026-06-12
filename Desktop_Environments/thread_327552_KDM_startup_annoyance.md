---
title: "KDM startup annoyance"
date: 2006-12-29
forum: Desktop Environments
---

### Post by warden on 2006-12-29
Hi,

I've been using both GNOME and KDE for quite a while. When I get tired of how one looks&feels, I switch to the other one (I kinda like sitting on two chairs, if you know what I mean :cool: ). But recently, because of some problems with gdm and my laptop (Acer 5022WLMi with Radeon X600 - sometimes there's a system freeze when I try to log out), I decided to try to ditch the default gdm login manager (I'm using Ubuntu Dapper) and switch to the kdm one which doesn't seem to have such problems.

So, I ran #dpkg-reconfigure kdm; changed the /etc/X11/default-display-manager to /usr/bin/kdm, checked  the rc dirs to confirm that kdm script is there...

Everything's OK. But, everytime I boot/reboot the system the kdm doesn't start automatically. I get the console login, have to logon as root and start kdm manually :-? 
It runs perfectly (almost, look note below), but it is annoying to have to do that every time the system starts. Any ideas as to what I'm doing wrong?

Sorry for long post,
Cheers

Note: although I can start my ordinary GNOME session normally from kdm login, the switch seems to have somehow messed up the Gnome/Beryl session, which works slooooow, and doesn't load the effects and window borders(Emerald)....

---

### Post by warden on 2006-12-30
bonk...

---

### Post by dominik_ap on 2008-01-31
Hi did somebody help you? I have really the same  problem and i didnt want to create new post, so how is it? How can i repair it? pleaseeee help...

---

### Post by dominik_ap on 2008-02-01
Hey i solved it, i dont know which of these helped me, but try something of this:

```
sudo dpkg-reconfigure xserver-xorg
sudo dpkg-reconfigure kdm
set default-xsomething /usr/bin/kdm
sudo apt-get install kdm kubuntu-desktop

and i checked also if i have KDM in 2-5 runlevels here:
sudo sysv-rc-conf

```

I know these commands are messed, i checked my history now and it was there in this order, so something of this had to help me :)

Bye and tell us if it helped

thank you

---

