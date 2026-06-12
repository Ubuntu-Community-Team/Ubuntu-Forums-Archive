---
title: "screen blank on boot"
date: 2007-07-29
forum: Dell  Ubuntu Support
---

### Post by dougleduck on 2007-07-29
Ive got a inspiron 1100 running feisty, 256MB RAM.

Sporadically when I boot, ubuntu will start and the and gets as far as the login screen but the screen is blank (i.e. doesnt appear to be turned on). I know the boot is succesful as I get the login screen sound.

It means if im careful i can even shut down if i guess where to click. If not then i shut it down and restart and more often that not the problem disappears.

Any idea&#347;.

---

### Post by Rocket2DMn on 2007-07-31
If you are using an onboard video card, you might be short on RAM since your video stuff has to be stored in regular RAM, not on a video card elsewhere.
You can try reconfiguring Xorg if you think it would help, the command is
```
sudo dpkg-reconfigure xserver-xorg
```
A backup of your /etc/X11/xorg.conf file will be created in that directory with a name like xorg.conf.123456 where the numbers represet the current date.

How much RAM do you typically use when you are running in Ubuntu?  If it is close to 256, you may want to consider a lighter environment.  Xfce is a lighter weight desktop environment than GNOME, maybe you should give that a try.  There is also Fluxbox.

---

### Post by dougleduck on 2007-08-07
Im currently trying to upgrade to 512 MB memory cos its a little slow anyway. If I still have problems ill post back here.

---

### Post by 1/0 on 2007-08-07
Check that the graphics card is properly in place. I've had a problem with one of my computers. The graphics card twists in the slot. 

Any errors in /var/log/messages or /var/log/Xorg.0.log ?

---

### Post by dougleduck on 2007-08-07
Its a laptop and doesnt really have proper graphics card, just inbuilt one.

The problem is sporadic so currently nothing in there. Does this wipe clean at every boot?

---

### Post by dougleduck on 2007-11-11
I've started a new thread on [http://ubuntuforums.org/showthread.php?t=609192](http://ubuntuforums.org/showthread.php?t=609192) related to this problem.

---

