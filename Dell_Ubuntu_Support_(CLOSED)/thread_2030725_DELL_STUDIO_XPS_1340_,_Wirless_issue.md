---
title: "DELL STUDIO XPS 1340 , Wirless issue"
date: 2012-07-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ckjaseem on 2012-07-21
I recently installed Ubuntu 11.10 32bit on my DELL laptop which originally cam with Windows VISTA OS. Now I am getting serious issues with the build-in wireless. I can use the internet perfectly with the Ethernet cable, but not with the build-in wireless.

The strange part is that wireless symbol on the top right side of the screen shows connected, but when I tried browsing the net .. it just keep loading forever. Also after booting up it shows Network service discovery disabled .. .local.domain etc. 

Can anyone help me with these problems please. I did searched before posting this and I did find some but I need a step by step solution; coz I don't know much about Ubuntu OS I'm a newbie .. to Ubuntu(linux).  

thnx.

---

### Post by Vakman on 2012-07-21
Someone on an AskUbuntu post said to:

"Edit the following file
/etc/modprobe.d/blacklist.conf
and add this to it:
```
blacklist acer_wmi
```
Then reboot and your wifi should work ;)"

Alternatively, try to use the MadWifi drivers, tutorial by [drpjkurian]("http://ubuntuforums.org/member.php?u=805294") here: [http://ubuntuforums.org/showthread.php?t=1484242](http://ubuntuforums.org/showthread.php?t=1484242)
It is for 10.04 but would likely still be relevant.

---

