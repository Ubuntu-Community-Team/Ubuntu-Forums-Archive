---
title: "X server for xubuntu"
date: 2007-02-13
forum: Desktop Environments
---

### Post by CalcProgrammer1 on 2007-02-13
I was installing xubuntu from the Alternate CD, text mode.  After installing base system I installed boot manager and exited, because I wanted to make sure that it had installed after many previous failures.  Now I'm in console and it's working but I can't get XFCE installed.  The machine is P133/64MB RAM, I have a swap as well but I'm not sure of the size (it erased my existing one and made a new one).

---

### Post by scrooge_74 on 2007-02-13
use command df to know the size and free space you have

to install XFCE just type sudo apt-get install xubuntu-desktop

---

### Post by kerry_s on 2007-02-13
Those are some low specs, DSL would be a better choice-> [http://damnsmalllinux.org/](http://damnsmalllinux.org/)

---

### Post by scrooge_74 on 2007-02-13
in fact DSL is very nice I play with it from time to time. Try just to install ICEwm

---

### Post by CalcProgrammer1 on 2007-02-13
I tried to install DSL on the machine.  It installed but booted to console with a dead xserver as well.  I wanted something Debian based, and I used to use Ubuntu on my main desktop a lot and it was great, so I chose Xubuntu for this machine.  I'm now installing the desktop.  Also, I'm using the Recovery mode, because for some odd reason I can't login with the username I had set up during installation.  How can I set up a username?

---

### Post by scrooge_74 on 2007-02-14
sudo adduser user_name 
sudo passwd user_name

[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

---

### Post by CalcProgrammer1 on 2007-02-14
I have the xubuntu-desktop installed now, but for some reason it loads into a very low resolution screen and won't load anything.  I see the mouse running inside the Ubuntu logo thing, then it goes white.  I edited out the xorg.conf file to only use modes "1024x768" "800x600" "640x480".  I'm using startx to start it, but I rebooted normally and when it went to load it, the same thing happened.  However, it went on, then it exited back to the console login screen, then it tried loading again, and then went back to console, and it repeated this.

---

### Post by maxamillion on 2007-02-14
you might want to try something like [Fluxbuntu]("http://fluxbuntu.org/") .... those are low specs, even for Xubuntu.

---

### Post by CalcProgrammer1 on 2007-02-14
fluxbuntu says minimum is 233MHz P2/96MB RAM, I'll try it though

---

