---
title: "Installing multiple distros"
date: 2005-12-19
forum: General Help
---

### Post by MrChips on 2005-12-19
Is it possible to install more than one Linux distro on one hard drive without too many complications?  

I have AGNULA DeMuDi 1.2.1 and would like to check out all of the music features while still keeping a copy of Ubuntu installed to get updates and perform normal PC routines.

Of course it would be a dual boot.

---

### Post by taurus on 2005-12-19
Of course, you can install more than one distro on your machine, assuming that each OS has it own partition...  GRUB should be able to handle booting all those Oses.

---

### Post by Emerzen on 2005-12-19
It's a snap.  I had Ubuntu, Kubuntu, Debian, and PCBSD all installed at one point on 2 harddrives.  The tricky part is partitioning (it's not that tricky if you have a good partitioning tool like Partition Magic or a Linux one).  The other difficulty is the bootloader...whichever OS you install last will usually have control of the bootloader.  So, if you make changes to your other OSs (add a new kernel for example) you have to remember to go into the master OSs boot file and change it there.

For a dual boot:

Need two large partitions for each OS (use your imagination) and a small partition for SWAP.  If one is Windows, install Windows 1st, then install Ubuntu and use GRUB for booting as it works well with Windows.  If you install Windows second, it's bootloader will install and completely ignore Ubuntu, so you'ld have to fix that (I advise avoiding the problem by following the Windows 1st policy).  

There is are gobs of info about setting up dual boots on the forums and in the Wiki, you should search a bit to see what you come up with.  I think a great many, if not the majority, of users dual boot in some form though.

---

### Post by fannymites on 2005-12-19
I have had up to 6 different distros on one hard drive at one time and there haven't been any problems.
One thing I would recommend is that you decide which you want to be your primary distro and install it's grub to the mbr then on all the other distros install grub to their own partition, eg /dev/hda3 and in your primary grub use entries like this for the other, none primary distros - 

```

title Debian
rootnoverify (hd0,1)
chainloader +1

title Suse
rootnoverify (hd0,2)
chainloader +1

title Fedora Core
rootnoverify (hd0,5)
chainloader +1
```
This way, if a kernel is upgraded in any of the distros and their own grub is updated, you won't have to keep adjusting your primary grub.

---

### Post by MrChips on 2005-12-19
Great!

I'll give it a shot. ;)

My Linux journey continues....

---

### Post by scole on 2005-12-20
I have winxp ubuntu and puppy linux all on a 6gig hdd. For ubuntu you need a partion for it. With many distros they will install to a windows hdd and boot up off a floppy disk. [www.goosee.com/puppy](www.goosee.com/puppy) 55mb distro it will install to the hdd with windows and initiate off of a boot floppy.

---

