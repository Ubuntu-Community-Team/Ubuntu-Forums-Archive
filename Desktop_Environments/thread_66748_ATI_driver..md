---
title: "ATI driver."
date: 2005-09-18
forum: Desktop Environments
---

### Post by snoochems on 2005-09-18
Hi all. 

I'm stuck.  

I can't get my ATI X800XT-PE to work properly.  I'm using the latest Ubuntu build and everything is up to date.  

I've tried a 'guide' that i found on these forums, and i followed it to the letter right up until it said to restart my PC.  

I never saw my desktop again.

So, i just reinstalled, and wondering if there was a proper way to install the ATI driver.

Thanks in advance

---

### Post by cbudden on 2005-09-18
Download this - [http://www2.ati.com/drivers/linux/ati-driver-installer-8.16.20-i386.run](http://www2.ati.com/drivers/linux/ati-driver-installer-8.16.20-i386.run) (50 ish mb) then follow these instructions [http://www2.ati.com/drivers/linux/linux_8.14.13-inst.html#176980](http://www2.ati.com/drivers/linux/linux_8.14.13-inst.html#176980)

---

### Post by snoochems on 2005-09-18
doesn't work.

---

### Post by cbudden on 2005-09-19
[QUOTE=snoochems]doesn't work.[/QUOTE]
 Little bit more info please.

---

### Post by fragmental on 2005-09-19
[QUOTE=cbudden]Little bit more info please.[/QUOTE]
 Exactly.  
If you can get to a console(there's no reason why you shouldn't be able to) type in "cat /var/log/Xorg.0.log | grep EE" and that should give you some idea of what is wrong.  Also "cat /var/log/Xorg.0.log | grep fglrx" should give you some more info.  You can alwasy just look at the Xorg.0.log but that's a lot to sift through.  You can also run "dmesg" or "dmesg | grep fglrx" or "dmesg | grep agpgart".

You should have to reinstall ubuntu after a video driver upgrade.  All you should have to do is change "fglrx" back to "ati" in "/etc/X11/xorg.conf".  You did change ati to fglrx in xorg.conf or run fglrxconfig right?

---

