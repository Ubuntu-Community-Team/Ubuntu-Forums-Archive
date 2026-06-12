---
title: "Autostart X without *DM"
date: 2007-12-07
forum: Desktop Environments
---

### Post by helino on 2007-12-07
Hi,

I was wondering if there's a way to autostart x without using a login manager. Since I'm the only one using my computer, I don't need to type my user/pass everytime it boots.

I think that GDM and KDM are little bit too heavy, and XDM doesn't have autologin.

I found this thread on the gentoo forums:

[http://forums.gentoo.org/viewtopic.php?t=268192](http://forums.gentoo.org/viewtopic.php?t=268192)

Does this solution have any gentoo specific code in it, or is there a smarter way to do this?

Thanks a lot

---

### Post by lswest on 2007-12-07
easiest thing would be just set it up to automatically log in to your account... under system-->administration-->login window
under the security tab just check "enable automatic login" and choose your username.

however, the gentoo thing looks like it would work for ubuntu too, but auto-login would probably be easiest, in case you ever decide to make a second account or so...

---

### Post by helino on 2007-12-07
> **lswest said:**
> easiest thing would be just set it up to automatically log in to your account... under system-->administration-->login window
under the security tab just check "enable automatic login" and choose your username.

however, the gentoo thing looks like it would work for ubuntu too, but auto-login would probably be easiest, in case you ever decide to make a second account or so...

Thanks for replying, but I don't think you understand what I mean. I should have said that I'm using fluxbox as WM, not gnome. The solution you suggested does involve GDM, which is what I want to avoid.

---

### Post by mali2297 on 2007-12-07
One option is to add the following lines at the end of **~/.profile**:
```

# start X on login.
if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
  startx
fi

```
With this, X starts immediately after login.

---

### Post by mali2297 on 2007-12-07
When I read your post again, it seems like you want an automatic login as well. This Howto might help:
[http://ohioloco.ubuntuforums.org/showthread.php?t=303319](http://ohioloco.ubuntuforums.org/showthread.php?t=303319)

---

### Post by lswest on 2007-12-07
yea...i mean...my solution doesn't depend on the WM, and why would you want to avoid gdm? if you want you can use kdm or xdm instead...or just change the theme so it looks different, lots of options there.  Also...the best solution is an auto-login, just the method to achieve it changes in each window manager..

---

### Post by helino on 2007-12-08
> **lswest said:**
> yea...i mean...my solution doesn't depend on the WM, and why would you want to avoid gdm? if you want you can use kdm or xdm instead...or just change the theme so it looks different, lots of options there.  Also...the best solution is an auto-login, just the method to achieve it changes in each window manager..

I know your solution doesn't depend on a specific WM, but it does depend on a login manager, such as GDM, KDM and XDM. I planned to use XDM, but since it doesn't have auto-login, I have to use another solution. The reason for not using a login manager is desribed here: [https://help.ubuntu.com/community/Installation/LowMemorySystems#head-56f5663adabcf5cb466de390ac754d444a05b0a4](https://help.ubuntu.com/community/Installation/LowMemorySystems#head-56f5663adabcf5cb466de390ac754d444a05b0a4)

[QUOTE=mail2297]When I read your post again, it seems like you want an automatic login as well. This Howto might help:
[http://ohioloco.ubuntuforums.org/sho...d.php?t=303319](http://ohioloco.ubuntuforums.org/sho...d.php?t=303319)[/QUOTE]

Tack så mycket :) This seems to be a solution to my problem, thanks for the help

---

### Post by UmbraMalison on 2007-12-10
helino, if your still having problems. I believe the solution i found for myself will work for you.

see it here

[http://ohioloco.ubuntuforums.org/showthread.php?p=3926755#post3926755](http://ohioloco.ubuntuforums.org/showthread.php?p=3926755#post3926755)

---

### Post by helino on 2007-12-13
> **UmbraMalison said:**
> helino, if your still having problems. I believe the solution i found for myself will work for you.

see it here

[http://ohioloco.ubuntuforums.org/showthread.php?p=3926755#post3926755](http://ohioloco.ubuntuforums.org/showthread.php?p=3926755#post3926755)

It isn't working, but since I'm using Gutsy, I don't think I will follow your solution. My boot process stops at "Running local scripts /etc/rc.local", does anyone know what's wrong?

---

### Post by Mr. Electric Wizard on 2007-12-17
helino, I am in exactly the same boat as you.

1)  when I tried to do a 7.10 alternate install for a "low resource" system, mine stopped booting at the same point.  I ended up just using the 6.06 alternate install.  Worked fine.

2)  I too have setup a box with no login manager, but with ICEwm as the desktop manager.
     I will be using this box for VMWare workstations *only*.
     I need this auto login so that when the pc boots up startx runs automatically as well as ./vmware.

Have you found a solution yet to either problem?

---

### Post by macstyle@freeshells.ch on 2007-12-30
[http://ohioloco.ubuntuforums.org/showthread.php?p=3926755#post3926755](http://ohioloco.ubuntuforums.org/showthread.php?p=3926755#post3926755)

---

