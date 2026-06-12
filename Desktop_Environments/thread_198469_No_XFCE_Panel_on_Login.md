---
title: "No XFCE Panel on Login"
date: 2006-06-17
forum: Desktop Environments
---

### Post by FoggyMtn on 2006-06-17
Hey Ya'll

I was following some instructions in another post ([http://www.ubuntuforums.org/showthread.php?t=192590](http://www.ubuntuforums.org/showthread.php?t=192590)  ).   They suggested to speed up ubuntu do the following:

Speed up Ubuntu:
select 16bit colours instead of 24bit in /etc/X11/xorg.conf, change
Code:

DefaultDepth 24

to
Code:

DefaultDepth 16



When I did this and restarted, I lost my xfce panels.  There is nothing on the top or bottom of the screen.  I tried strating it manually, using :
xfce4-panel

I starts, but hangs.  I get the panel, but I never get back to my command prompt.  If I do a ctrl-c I get an error 
** (xfce4-panel:6220): CRITICAL **: An item was unexpectedly removed: "Xfce Menu".

I tried copying my ~/.config/xfce4/panel folder from another user to this one, and it still wont show up.  The other users work fine.

Does anyone have anythougts what I've done? Or how to correct it?

I did post about this in the original thread, but I didn't want to hijack it, and thought I might get better results starting my own.  I hope this isn't considered double posting.

Thanks to all
Rob

on edit:  I also ran  sudo dpkg-reconfigure -phigh xserver-xorg as suggested in /etc/X11/xorg.conf.  This moved my original config to a backup, and created a new one.  It didnt help either

---

