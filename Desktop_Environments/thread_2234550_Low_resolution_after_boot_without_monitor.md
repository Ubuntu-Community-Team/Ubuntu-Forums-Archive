---
title: "Low resolution after boot without monitor"
date: 2014-07-15
forum: Desktop Environments
---

### Post by bromol on 2014-07-15
I have XUBUNTU 14.04 system like as "home server" with incoming connection to desktop via [http://www.teamviewer.com/](http://www.teamviewer.com/)

I boot this system with grub 

GRUB_CMDLINE_LINUX=«nomodeset»

and autologin in xfce for this option.


In my other "disconnected monitor" system i am setup resolution in /etc/x11/xorg.conf (content from my xorg.conf this [http://pastebin.com/hKHMPD2N](http://pastebin.com/hKHMPD2N) ) manually, and this work fine!
Check this screen:
[IMG]http://i.imgur.com/QPsDcqf.png[/IMG]

**On a new, similar target system with new hardware this hint does not work!**

After i set GRUB NOMODESET and place my xorg.conf to /etc/X11/ and restart system a have fail boot with this /var/log/Xorg.0.log error


```
[ 26.180] (==) Log file: «/var/log/Xorg.0.log», Time: Mon Jul 14 16:00:32 2014
[ 26.180] (==) Using config file: «/etc/X11/xorg.conf»
[ 26.180] (==) Using system config directory «/usr/share/X11/xorg.conf.d»
[ 26.181] Parse error on line 1 of section InputClass in file /etc/X11/xorg.conf The Section keyword requires a quoted string to follow it.
[ 26.181] (EE) Problem parsing the config file
[ 26.181] (EE) Error parsing the config file
[ 26.181] (EE)
Fatal server error: [ 26.181] (EE) no screens found(EE)
[ 26.181] (EE)
Please consult the The X.Org Foundation support at http://wiki.x.org for help.
[ 26.181] (EE) Please also check the log file at «/var/log/Xorg.0.log» for additional information.
[ 26.181] (EE)
[ 26.181] (EE) Server terminated with error (1). Closing log file.

```


After del /etc/X11/xorg.conf and restart system **i have normal boot with fixed 640x480 low resolution**:

[IMG]http://i.imgur.com/90dqXjI.png[/IMG]

_**What need setup or change to set normal resolution? (May be 1024 or higher)**_

---

### Post by jp734 on 2014-07-15
Did you check what the line below is refering to?
**[SIZE=1][ 26.181] Parse error on line 1 of section InputClass in file /etc/X11/xorg.conf The Section keyword requires a quoted string to follow it.[/SIZE]**

If after editing you're still having some problem, post a copy  of you xorg.conf file

---

### Post by bromol on 2014-07-20
Thanks! This help to solve my problem! I am copy xorg.cof from my old system via ssh and all work normally!

---

### Post by bromol on 2014-07-20
My xorg.conf file on the off-chanse download link [http://rghost.net/56999750](http://rghost.net/56999750)

---

