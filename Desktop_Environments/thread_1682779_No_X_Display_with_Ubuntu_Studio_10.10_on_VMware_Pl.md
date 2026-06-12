---
title: "No X Display with Ubuntu Studio 10.10 on VMware Player"
date: 2011-02-06
forum: Desktop Environments
---

### Post by davidg25 on 2011-02-06
I'm running the latest VMware Player On Win 7 Ultimate 64 bit, with Ubuntu Studio 10.10 (32bit version) installed.  

It installed and boots just fine, but only starts up with the shell log on.   VMware recognized the system and used it's 'fast track' automatic install.   I then used the 'apt-get' process to install VMware tools from the command line.

How do I fix this in order to run X (which is the whole point), and then make it the default start-up?  

If this has been covered, I'd appreciate a re-direction !

Many Thanks,
dave

---

### Post by davidg25 on 2011-02-06
Well, duh !   I checked and found that no desktop was installed (referenced in another thread), so I used  "  sudo apt-get install ubuntu-desktop  "  and I can 'startx'  now.  This was supposed to be 'Studio' from the Ubuntu Studio site, i386 iso, but it's coming up in gde as 'generic' with few if any of the studio pgms.

---

### Post by jeffs0214 on 2012-02-15
Please note that I am a linux noob and am slowly learning from forums like these. But it was hard to locate the info for installing Ubuntu Studio 10.04 for the first time.  Maybe it was how or what I searched for.

Anyway, I know this reply is a year late, but hopefully adding it will help someone else.

I installed Ubuntu Studio 10.04 in VMWare Player on my Windows 7 64-bit pc, as well, and learned the first few issues most people had with the install finishing and ending up at the terminal prompt.

The following thread helped me get things going (thank you Thelasko):

(you may need to copy and paste into your address bar)

[http://ubuntuforums.org/showthread.php?t=900676]("http://http://ubuntuforums.org/showthread.php?t=900676")

I will try and post anything I think is helpful here, or may start another thread, but can only imaging how many threads there truly are here.

---

