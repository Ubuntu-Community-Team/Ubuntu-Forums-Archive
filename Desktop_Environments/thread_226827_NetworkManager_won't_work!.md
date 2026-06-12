---
title: "NetworkManager won't work!"
date: 2006-07-31
forum: Desktop Environments
---

### Post by javaJake on 2006-07-31
IGNORE THIS POST - GOTO THIS POST:
[http://ubuntuforums.org/showthread.php?p=1383399#post1383399](http://ubuntuforums.org/showthread.php?p=1383399#post1383399)

---

### Post by javaJake on 2006-07-31
IGNORE THIS POST - GOTO THIS POST:
[http://ubuntuforums.org/showthread.php?p=1383399#post1383399](http://ubuntuforums.org/showthread.php?p=1383399#post1383399)

---

### Post by javaJake on 2006-07-31
IGNORE THIS POST - GOTO THIS POST:
[http://ubuntuforums.org/showthread.php?p=1383399#post1383399](http://ubuntuforums.org/showthread.php?p=1383399#post1383399)

---

### Post by javaJake on 2006-08-01
IGNORE THIS POST - GOTO THIS POST:
[http://ubuntuforums.org/showthread.php?p=1383399#post1383399](http://ubuntuforums.org/showthread.php?p=1383399#post1383399)

---

### Post by javaJake on 2006-08-15
OK guys. This is serious. I'm not getting an answer anywhere. Not on IRC, not on forums, etc. I'm extremely desperate.

Ubuntu apparently has something to do with this. This isn't just an NM issue. It's the way Ubuntu works with it.

Here's my problem re-phrased just in case you didn't understand it:

OK, recompiling from scratch didn't work (view history below if curious).

I am desperate for an answer. If you guys need ANY information please let me know! I am willing to collect it as fast as I can!!!
Let me rephrase the problem:

Network-Manager, compiled from latest version or from any debain repository, will not connect to a network. It sees networks, it knows what type of encryption they have, what the signal strength is, etc, but it just won't work. It will only work if I "enable" or run ifup after telling NM to attempt to connect. NM will pretend like it is doing all the work, but it is really me with ifup.

After starting NM, I have to go into the config, and uncomment the "wireless-essid network" entry after so that ifup will connect to the right one in the paragraph above.. ugh.

Strange? I think so. The network will work if I manually configure it, it's just NM won't work.

The /var/log/syslog output is here (trimmed from the time I told NM to start connecting):
[http://expandapps.org/pages/pastebin.php](http://expandapps.org/pages/pastebin.php)

I have ndiswrapper drivers installed for the WUSB45GS v1 (Linksys Wireless-G USB Adapter with SpeedBooster) device. (See my HOWTO.)

---

