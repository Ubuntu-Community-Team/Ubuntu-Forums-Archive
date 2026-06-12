---
title: "can someone decipher this startX error?"
date: 2007-11-02
forum: Desktop Environments
---

### Post by t3m17 on 2007-11-02
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux Tim-Desktop-Linux 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov  2 16:19:12 2007
(==) Using config file: "/etc/X11/xorg.conf"
(WW) VESA: No matching Device section for instance (BusID PCI:7:0:0) found
Requesting insufficient memory window!: start: 0xfe900000 end: 0xfe9fffff size 0x10000000
(EE) Cannot find empty range to map base to
(EE) VESA(0): Cannot read V_BIOS (3)
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

2x x1650 PCI express

Thanks

---

### Post by Stemp on 2007-11-02
> PCI:7:0:0

???

Look in your /etc/X11/xorg.conf file the busid parameter (in the device section).

---

### Post by t3m17 on 2007-11-02
Yeah, I was wondering about that, how do I determine what the correct Bus ID is? Does this have anything to do with the fact that there are two video cards in this box?

Thanks

---

### Post by Stemp on 2007-11-02
The BusId parameter is set to PCI:7.0.0 in xorg.conf ? 

What about :
```
lspci | grep VGA
```

---

### Post by NilsHG on 2007-11-02
is SLI or Crossfire possible with Linux?

---

### Post by t3m17 on 2007-11-02
grep VGA
06:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 71c1 (rev 9e)
07:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 71c1 (rev 9e)

---

### Post by t3m17 on 2007-11-02
> **NilsHG said:**
> is SLI or Crossfire possible with Linux?

I'm not trying to do that..at least not yet..I just have two cards for multiple monitors...even though right now I only have 2 plugged into the first card...third monitor should be coming along shortly.

---

### Post by t3m17 on 2007-11-02
anybody? How do I find out what the correct PCI bus ID is?

---

### Post by Stemp on 2007-11-02
7.0.0 seem to be correct.

You have one in 6.0.0 and one in 7.0.0...

---

### Post by t3m17 on 2007-11-03
Alright, I set it to 7.0.0 and all is well...thanks for your help!! I enabled the restriced drivers, and everything seems to be fine, but it won't let me enable normal or extra visual effects....any ideas?

---

### Post by Stemp on 2007-11-03
with fglrx drivers (the restriced drivers) you need to install the xgl server.

package **xserver-xgl**

---

### Post by t3m17 on 2007-11-03
Stemp, thanks so much once again for your quick answers, I'll try that in a second, do you know anything about running extended desktop onto multiple screens? It starts out cloning the same desktop onto both monitors I have, and then  when I start messing with it I always end up with one blank screen and one screen displaying the desktop...

Thanks again Stemp..

---

### Post by Stemp on 2007-11-03
Try to get the visual effects on one monitor, then we will look for extended desktop ;)

Depending on what card you have, it will be nice to look at at the new fglrx driver (no need of xgl anymore) :
[http://ubuntuforums.org/showthread.php?t=593348&highlight=fglrx](http://ubuntuforums.org/showthread.php?t=593348&highlight=fglrx)
nb : this is not trivial and not easy for beginners

---

### Post by t3m17 on 2007-11-03
thanks

---

### Post by t3m17 on 2007-11-03
Stemp..you are a kind kind person....


I have the visual effects set to extra...and it all seems to work fine...

---

