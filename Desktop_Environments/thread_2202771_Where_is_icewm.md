---
title: "Where is icewm?"
date: 2014-01-30
forum: Desktop Environments
---

### Post by richardbrucebaxter on 2014-01-30
Hi,

I am new to Ubuntu (long term Redhat user) and am attempting to install icewm. When installing Ubuntu 13.1 on this Ultrabook I was working off the assumption that they supported icewm (eg [https://help.ubuntu.com/community/IceWM](https://help.ubuntu.com/community/IceWM)). Can someone please point me in the right direction? Is there a contact responsible for updating the (universe) repository?

sudo apt-get install icewm

gives "E: Unable to locate package icewm"

Cheers,

Richard

---

### Post by deadflowr on 2014-01-30
You should usually run an package list update first
```
sudo apt-get update
```
then try installing.
The package is there.
You might need to run an upgrade(actually just an update)
```
sudo apt-get upgrade
```
if you get a list of held packages, you could try
```
sudo apt-get dist-upgrade
```
If you get any errors, post them
(use code tags)

---

### Post by richardbrucebaxter on 2014-01-31
Thanks very much Deadflowr, 

It worked fine after running "sudo apt-get update"

Excellent support here...

---

### Post by Bucky Ball on 2014-01-31
We try. ;)

Please mark the thread as solved to help others by following the link in my signature. Thanks.

---

### Post by richardbrucebaxter on 2014-02-03
Thanks BuckyBall

(Note I am still attempting to locate and initialise the bluetooth-applet and gnome-volume-manager applets in Ubuntu icewm; but that will likely require another thread. Yet apart from this and an inability to control the backlight in icewm on this Samsung Series 5 the Ubuntu 13.1 installation has gone very well. Almost entirely positive. The repositories in Ubuntu are very comprehensive).

---

### Post by Bucky Ball on 2014-02-03
Excellent to hear. Yes, post new threads with descriptive titles in the appropriate areas of the forum for maximum impact. ;)

***Desktop Environments*** would be a good start for anything ice-specific.

PS: You could install Bluez. Not sure what Ice uses by default.

---

### Post by richardbrucebaxter on 2014-02-16
Note I found a workaround to the missing gnome applet and brightness configuration problem (installing mate-bluetooth-applet, mate-power-manager and indicator-brightness). Icewm is still not respecting my gnome power manager settings (the lid close action is ignoring all dconf-editor settings and defaulting to "suspend", like before logon), but have requested help for this in another thread ([http://ubuntuforums.org/showthread.php?t=2205979](http://ubuntuforums.org/showthread.php?t=2205979)).

---

