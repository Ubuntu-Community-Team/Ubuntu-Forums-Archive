---
title: "compiz cant be enabled"
date: 2009-05-02
forum: Desktop Environments
---

### Post by nathang1392 on 2009-05-02
i cant enable compiz on my system. i used a script advised to gather information. here is the output:

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2a02 detected. 

Would you like to know more? (Y/n) y

 Your particular graphics chip may be blacklisted on certain distributions.
 However that does not necessarily mean you will not be able to run Compiz.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N) 

thanks for any help...also, is it advisable to not check for blacklisted chips?

---

### Post by nathang1392 on 2009-05-02
i cant enable compiz on my system. i used a script advised to gather information. here is the output:

Gathering information about your system...

Distribution: Ubuntu 9.04
Desktop environment: GNOME
Graphics chip: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
Driver in use: intel
Rendering method: AIGLX

Checking if it's possible to run Compiz on your system...

Checking for texture_from_pixmap... [ OK ]
Checking for non power of two support... [ OK ]
Checking for composite extension... [ OK ]
Checking for FBConfig... [ OK ]
Checking for hardware/setup problems... [WARN]

Something potential problematic has been detected with your setup:
Warning: PCI ID 8086:2a02 detected.

Would you like to know more? (Y/n) y

Your particular graphics chip may be blacklisted on certain distributions.
However that does not necessarily mean you will not be able to run Compiz.

You can skip this blacklist -- but keep in mind that you did so.
Do not complain if you encounter any problems with Compiz afterwards.

Do you want to skip blacklist checks by Compiz? (y/N)

thanks for any help...also, is it advisable to not check for blacklisted chips?

---

### Post by overdrank on 2009-05-02
> **nathang1392 said:**
> 
Do you want to skip blacklist checks by Compiz? (y/N) 

thanks for any help...also, is it advisable to not check for blacklisted chips?

Have you tried to skip blacklist checks?
You may also look at the link in my signature on the intel graphics.

---

### Post by malditonuke on 2009-05-02
Your graphics card is blacklisted due to a bug.  I have it, too.

Search the terms "ubuntu 9.04 intel blacklist" for plenty of talk about it.  The bug is discussed here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392)

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363821](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363821)


Apparently it's causing issues with full-screen flash playback as well. 

You can run the risk of crashes by overriding the blacklist, revert back to 8.10 until the bug is fixed, or wait for a fix without compiz for a while.

---

### Post by overdrank on 2009-05-02
Please do not create multiple threads on the same issue. Threads merged

---

