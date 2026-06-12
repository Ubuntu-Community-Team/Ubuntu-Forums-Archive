---
title: "Ubuntu 7.10 blanks screen Nvidia card"
date: 2008-04-28
forum: Desktop Environments
---

### Post by mangus64 on 2008-04-28
On my wife's poweredge sc440, 7.10 turns off her display about 30 minutes after bootup. No ctrl-atl-+ or - works. Remote login reveals X takes up 100% CPU. Last time a kill -9 on the X process would not kill it.
Running VirtualBox in this environment btw.

I commented out the DPMS line in xorg.conf
I added the 
Section "ServerFlags"
 Option "blank time" "0"
 Option "standby time" "0"
 Option "suspend time" "0"
 Option "off time" "0"
 Option "screen blank" "0"
EndSection

section. I've tried xset s off, xset -dpms
chmod -x on the gnome-screensaver process.

Anyone got any ideas?

---

### Post by Vermind on 2008-04-28
Hello,
does this happen when the computer is idle for that long, or after that time anyway? You could try the official nvidia driver instead of the Ubuntu one. I wrote instructions in [another post]("http://ubuntuforums.org/showpost.php?p=4816326&postcount=4"). Check the part starting with "My Nvidia driver".

---

### Post by mangus64 on 2008-04-28
It happens while you are working....really frustrating. Thks for link Ill check it out

---

