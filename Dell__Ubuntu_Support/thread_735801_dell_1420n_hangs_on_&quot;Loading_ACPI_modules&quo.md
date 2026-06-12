---
title: "dell 1420n hangs on &quot;Loading ACPI modules&quot;"
date: 2008-03-26
forum: Dell  Ubuntu Support
---

### Post by muzazzi on 2008-03-26
I just got a (brand spanking new) dell 1420n laptop w/ nvidia 8400m gs graphics.   I turn it on, it tries to boot up and hangs when loading /etc/init.d/acpid ("Loading ACPI modules...").   I did some debugging and it appears this is happening on "modprobe -b container", which I suppose is the core acpi stuff.   I can boot if I turn off acpi ("acpi=off noapic ..."), but it seems like a really bad solution on this laptop.  This is on the 2.6.22-14-generic kernel (whatever the default dell installs).   

I'm not too familiar with ACPI, but I've been crawling the ubuntu forums all night and haven't seen a solution.    I ran across one thread [here]("http://ubuntuforums.org/showthread.php?t=394039") that dates back to Feisty, and was resolved by a kernel upgrade (2.6.20-12).   I figured this would have been resolved in gutsy tho. :-\   Anyone else run into this problem and/or have a solution?

Regards.

---

### Post by muzazzi on 2008-03-26
Interesting.   In a fit of rage, I decided to wipe the dell factory install of ubuntu and reinstalled from a semi-fresh gutsy iso.    Now everything seems to be working fine - acpi, nvidia and all.  :)   Although I suppose I'm now missing the dell dvd stuff - I suspect that's not a big loss.    I'm still not sure what the real issue was - I may play around with it this weekend and see if I can isolate the issue.

---

### Post by notwen on 2008-03-26
You say this occurred when booting your machine.  I was wondering if this actually happened when coming back from hibernate or suspend?  There was a bug regarding the 1420n equipped w/ the Nvidia 8400m, see [here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/8400M_Suspend_Hibernate-Failure").

If you wish to re-install again, you can use Dell's custom Gutsy image available [here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Dell_OS_Reinstallation_7.10_DVD_ISO").  You should try to check the [Dell Linux Wiki]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10") every so often for updated bugs/fixes/workarounds and the latest custom Ubuntu images for the Dell N-Series PCs and laptops.  =]

---

### Post by muzazzi on 2008-04-30
I don't believe this was a suspend/resume issue per se (although I haven't tested that extensively).   This was a fresh-out-of-the-box Dell 1420n, with Ubuntu (7.10/gutsy) installed at the factory.   I had to append acpi=off to the kernel params just to get it to boot.

I did reinstall with the Dell's iso (albeit a month ago).   A standard (non-dell) gutsy install worked much better at the time.   Recently, upgrading to hardy made the issues come back, so it's probably some known kernel bug, possibly related to [this open bug]("https://bugs.launchpad.net/ubuntu/hardy/+source/linux-source-2.6.22/+bug/146692").  I tried a bunch of stuff, including blacklisting various modules, installing the latest nvidia drivesr, totally uninstalling the nvidia drivers, etc. with no effect.   It always locks up on loading some acpi module (usually container.ko, but sometimes others if the order changes).   I turned on VERBOSE=yes in /etc/default/rcS and linux started spitting out:
BUG: soft lockup - CPU#0 stuck for 11s!

when doing an insmod of container.ko, and this message just repeated forever until I rebooted the box.

I rebuilt the kernel package on the very recent 2.6.25 sources, and it is now booting up fine. I haven't installed the proprietary drivers yet (for the wireless ipw3945 and nvidia hardware), however.   I think nvidia will work on 2.6.25 with some messing around, but i'm not familiar with the ipw driver.   Probably the easier option is to downgrade from the 2.6.24 kernel, although some builds of 2.6.22 seemed to cause this issue, as noted in that bug report above.  

For sanity sake, I'll point out that I haven't looked very deeply into the bug I linked above yet.   Maybe it's unrelated to the dell and there's some other insidious issue going on here. :)  I can definitely repeat this behavior by using the 2.6.24-16-generic kernel in Hardy though.

---

