---
title: "kernel update broke wireless"
date: 2007-02-12
forum: Desktop Environments
---

### Post by gwhit918 on 2007-02-12
I just did the update from 2.6.17-10-generic to 2.6.17-11-generic which was suggested by the Update Manager, and my wireless card no longer works.  It was working great (I used it to do the update!), but after a reboot, nothing.  It's a NETGEAR WG511v2, using ndiswrapper and the Win2000 driver.

I suspect that I have to modprobe ndiswrapper something or other, but I don't have time to research the answer right now.  BTW, '$ ndiswrapper -l' still shows "wg511v2 : driver installed", "device (11AB:1FAA) present".  However, when I try to start the Network Connection applet, it just displays "SIOCGIFFLAGS error: No such device".

---

### Post by shareMenaPeace on 2007-02-12
You can boot with another kernel or try to fix it.
Maybe in /var/Xorg.0.log is an error message about a missing module?

---

### Post by gwhit918 on 2007-02-12
thanks for the reply... yes, I'm able to boot into the previous kernel (2.6.17-10) fine and the PCMCIA wireless works fine.  Then, after booting back into 2.6.17-11, I checked /var/log/Xorg.0.log and then syslog, and uncoverered this message:
"loadndisdriver: main(546): version 1.9 doesn't match driver version 1.8" 

I realized I didn't give much background: this is Ubuntu 6.10 on a IBM Thinkpad T21, with a Netgear WG511v2 PCMCIA wireless card.  I downloaded the latest ndiswrapper source and compiled it (ubuntu's version didn't work) and used the Win2000 driver from the CD.

So, I'm looking for the steps which will get me back to where I was pre-kernel-update... namely, a working wireless card--but with the latest Ubuntu kernel.

---

### Post by shareMenaPeace on 2007-02-12
Well i dont know much yet about wireless and this is the desktop forum try post in 
[http://ubuntuforums.org/forumdisplay.php?f=136](http://ubuntuforums.org/forumdisplay.php?f=136) - network and wireless forum than you get a faster answer.

MAybe uninstall ndiswrapper and than reinstall - maybe use synaptic.

---

### Post by Limpan on 2007-02-12
I solved the problem by recompiling ndiswrapper. The first time I installed the wifi drivers I followed these instructions: [http://www.ubuntuforums.org/showthread.php?t=340689]("http://www.ubuntuforums.org/showthread.php?t=340689") I used ndiswrapper version 1.37 and ran the make commands from section C and step 8 again. Read somewhere on the forums about the need to recompile all third party modules or something like that for the -11 update.

---

### Post by gwhit918 on 2007-02-12
Thanks for the helpful post... I recompiled ndiswrapper as you suggested.  However--just as the docs you linked to predicted--I got an 'invalid argument' error on modprobe ndiswrapper.  The link you provided has a solution (under C. 13a.) but I'll have to wait until I can get to a wired connection to try it.

---

### Post by gwhit918 on 2007-02-12
update... still doesn't work after installin gndiswrapper-utils-1.8,  (per step C.13.a. in instructions limpan linked to.  At this point, it seems as if 2.6.17-11 really *did* break the working wireless connection.

---

### Post by Limpan on 2007-02-12
I'm not terribly sure that I know what I'm talking about now as I haven't been an Ubuntu user for that long but... Do you have the latest header files? I'm thinking about what the previously linked guide says in section B.5. You are compiling under the -11 kernel? Unless you are, uname will just tell you it's the old -10 kernel.

---

### Post by wiesiek_h on 2007-02-12
This appears to be a known "feature" of the new kernel, See other thread:
[http://www.ubuntuforums.org/showthread.php?t=358004](http://www.ubuntuforums.org/showthread.php?t=358004)

---

### Post by gwhit918 on 2007-02-13
Love those "features"!  Just to bring this full-circle, I did finally get this WG511v2 working (again) in my Thinkpad T21 with 2.6.17-11.  I started over at the very beginning, making sure to completely remove the existing install of ndiswrapper.

I followed [these directions]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation") at the ndiswrapper site.  Once I'd cracked the ndiswrapper tarball and moved into the resulting folder, I ran "sudo make uninstall" until it came back clean.  I had to "sudo rmdir" one stubborn directory.  

Once ndiswrapper was compiled and installed ('make distclean', 'make', sudo make install'), I followed [these instructions]("http://www.elet.polimi.it/upload/wspinell/website/index.php?sec=20_howto/20_linux_hw&id=00_Netgear%20WG511_on_Ubuntu_6__dot_06") to finish up.  Success!

---

### Post by Julolidine on 2007-03-04
This is why proprietary drivers suck donkey balls.  

If everything was open, these would be incorporated in the official repos (and thus dealt with via apt) with the kernel updates, but surprise surprise the two major things that seem to break with every single kernel upgrade  are nvidia drivers, and wireless cards due to ndiswrapper issues.  Being a non complete purist, I almost half understand closed source code from a business perspective.  Device drivers being closed practically boggle the mind.

---

