---
title: "AMD processor need AMD-based apps?"
date: 2006-02-09
forum: Desktop Environments
---

### Post by stepore on 2006-02-09
Hey folks, forgive the ignorance. Long time Linux user, potentially new AMD (64-bit) user. Before i bite the bullet and purchase a PC with an AMD processor i need a few questions answered. I've only ever used intell to this point. Truth be told, i've installed the PPC based distro on an old iMac for fun.

Firstly, I gather (from the download page) that you don't necessarily need the AMD 64-bit distro for all AMD processors, just for the athlon or other 64-bit AMD processors, correct? So, if it's not 64-bit (Athlon) just use the x86-based version, yes?

Secondly, given the first question. if i were to get a 64 bit AMD processor and install the AMD 64-bit distro, will all applications (java, flash, anything really) need an AMD version? For example, could i just go to java.com and install the regular (x86) Sun's java runtime environment or will i have to hunt down an AMD version. Essentially, just because i have a 64-bit processor, do i *need* a 64-bit version of any application, or can i just use/download and install any x86-based application? Furthermore, will all apps in synaptic be set to a special AMD (64-bit) repository, or just use the same repository for any regular x86 processor?

Now, just an aside. I was so used to doing a regular x86 based install of Ubuntu, that i went into auto pilot and installed it onto my best friends bran new Athlon 64 - based HP. And it worked, pretty much perfectly. The only thing i noticed was the network speed wasn't all there all the time, but now i guess i know why. But, everything else seemed to work pretty damn well. Didn't need the 64-bit AMD distro version, what gives?

thanks for any and all responses.

cheers,
jb

---

### Post by RAOF on 2006-02-09
The AMD x86-64 chips also run 32bit code - they're fully x86 compatible (in fact, last time I checked they were faster/cheaper at running 32bit code than the Intel chips).  You can install x86 distributions/apps just fine.

If you install the x86-64 version of Ubuntu, however, you will need to get 64bit apps (mostly).  This isn't an inherent restriction of x86-64, but your system libraries need to be the same width as the binaries that try to link to them.  Ubuntu64 installs 64bit libraries, and some 32bit libraries.  So some 32bit binaries work out of the box, and others (like wine) require a little bit of fiddling before they work.  But all of the packages in the Ubuntu repositories (at least the official/main ones) have 64bit versions, too.

Third-party repos (for example the PLF ones) often don't have 64bit packages.  So it is a bit simpler to install & mess with Ubuntu32 - the 64bit version requires some fiddling.

---

### Post by dcstar on 2006-02-10
[QUOTE=RAOF]The AMD x86-64 chips also run 32bit code - they're fully x86 compatible (in fact, last time I checked they were faster/cheaper at running 32bit code than the Intel chips).  You can install x86 distributions/apps just fine.
......
Third-party repos (for example the PLF ones) often don't have 64bit packages.  So it is a bit simpler to install & mess with Ubuntu32 - the 64bit version requires some fiddling.[/QUOTE]
And use the AMD K7 kernels if you do go the 32bit option.

---

### Post by stepore on 2006-02-10
[QUOTE=dcstar]And use the AMD K7 kernels if you do go the 32bit option.[/QUOTE]

speaking of which, do you use the AMD K7 kernel for any AMD processor, or just the more recent ones? that is, in case i get an older used AMD?

cheers,
jb

---

### Post by dcstar on 2006-02-10
[QUOTE=stepore]speaking of which, do you use the AMD K7 kernel for any AMD processor, or just the more recent ones? that is, in case i get an older used AMD?

cheers,
jb[/QUOTE]
It says "Duron/Athlon", so it should work with old CPUs.

---

