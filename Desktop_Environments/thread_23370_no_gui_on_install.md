---
title: "no gui on install"
date: 2005-04-01
forum: Desktop Environments
---

### Post by mikey on 2005-04-01
I've previously tried to install warty and was only succesful with the live cd installation. Now I've tried hoary , thinking maybe the gui issue would be resolved.  the live as well as the hd install  don't yield a gui. just a lot of green and brown static looking lines and in the case of the hd install a black screen just after the music begins. any help would be appreciated
thanks\
mikey

---

### Post by candc540 on 2005-04-01
[QUOTE=mikey]I've previously tried to install warty and was only succesful with the live cd installation. Now I've tried hoary , thinking maybe the gui issue would be resolved.  the live as well as the hd install  don't yield a gui. just a lot of green and brown static looking lines and in the case of the hd install a black screen just after the music begins. any help would be appreciated
thanks\
mikey[/QUOTE]
 Could be a video problem. Try running as root 'killall gdm' then 'dpkg-reconfigure xserver-xfree86'  in warty or 'dpkg-reconfigure xserver-xorg' in hoary. Answer all of the questions particularly the video and monitor sections. Also, it would be nice to know what kind of video card and monitor you have and if this is a notebook or desktop.

---

### Post by alastair on 2005-04-01
Hard to say ..... but some detail of your system/config might help.

If you can, check the X log and config file :

/var/log/Xorg.0.log
/etc/X11/xorg.conf

---

### Post by mikey on 2005-04-02
Dear candc & alastair:
1st thanks for the responses. I have a cloned desktop with a viewsonic pro220f monitor and a kyro 64mg 3d accelerator video card agp4. 
I haven't been able to use your suggestions since I can't log in as root. I never got that far in the installation process and unless there is some generic one I won't be able to. also my skill sets as a newbie are very crude so I will need a lot of clear simplistic instructions if I'm to br able to rectify my problem. look forward to hearing from you
best
mike

---

