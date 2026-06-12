---
title: "Intel 845G 3D problem; extension GLX missing"
date: 2005-09-28
forum: Gaming &amp; Leisure
---

### Post by remick182 on 2005-09-28
What's up everyone?  I've gotta question that I'm hoping someone can help me out with.  I'm pretty new at this Linux thing, so go easy on me, k? ;) 
I've been trying to get my intergrated Intel 845G video card to do its 3D thing.  I read up on how to fix the old 640x480 resolution problem, and have moved on to other areas of configuring.
I've gone to Intel's website and downloaded the _intelgraphics_060704.tar.gz_ file, but can't install because of an error:
[I]The script will now compile the agpgart module and DRM kernel modules
for your machine.
Press ENTER to continue or CTRL-C to exit.
Compiling new agpgart module...
ERROR: AGPGART module did not compile
Compiling DRM module...
ERROR: Kernel modules did not compile
The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.[/I]
I've been trying to search the forums here on what to do, but it seems most of the problems are pertaining to correcting the resolution or refresh rate.  Anyone got some input?  Thanks!

---

### Post by geekchic9 on 2005-09-30
Stupid question, but did you actually  look at the dri.log file on what went wrong? Maybe that would help.

---

### Post by remick182 on 2005-10-02
[LEFT]Yes, I did.  This is what I have:
[/LEFT]
    
[I]make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/dustin/Desktop/dripkg/agpgart-2.0 modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [default] Error 2
Makefile.linux:139: *** Cannot find a kernel config file.  Stop.

[/I]I don't seem to get much information from the dri.log file.  Any ideas?

---

