---
title: "how do I stop Xwindows from starting"
date: 2005-09-05
forum: Desktop Environments
---

### Post by scottie4442 on 2005-09-05
I am a long time user of Linux, but a new user of Ubuntu.  I have gone into /etc/inittab and changed the default runlevel to 3, but I still gui login and gnome still starts.  I do not want xwindows to automatically start, either for login or desktop.  Any help would be appreciated, I am pretty well up on how Linux itself works and have used Debian before, but Ubuntu does things a little bit different than standard Debian, yes I know it comes from standard Debian but the inittab thing works on Debian, just not on Ubuntu.  

Other than this issue I find Ubuntu to be a very good distro and was easy to setup and get running.  

Scott Adams

---

### Post by plb on 2005-09-05
either chmod -x /etc/init.d/something_gdm(look for something with gdm in the name I'm not on my ubuntu box at the moment to look)

or use update-rc.d command

---

### Post by arnieboy on 2005-09-05
[QUOTE=scottie4442]I am a long time user of Linux, but a new user of Ubuntu.  I have gone into /etc/inittab and changed the default runlevel to 3, but I still gui login and gnome still starts.  I do not want xwindows to automatically start, either for login or desktop.  Any help would be appreciated, I am pretty well up on how Linux itself works and have used Debian before, but Ubuntu does things a little bit different than standard Debian, yes I know it comes from standard Debian but the inittab thing works on Debian, just not on Ubuntu.  

Other than this issue I find Ubuntu to be a very good distro and was easy to setup and get running.  

Scott Adams[/QUOTE]
do the following:
```
sudo gedit /etc/inittab
```
and change the following line from:
> id:2:initdefault:
to
> id:3:initdefault
then do the following:
```
sudo chmod 444 /etc/rc3.d/S*gdm
```
and reboot

---

