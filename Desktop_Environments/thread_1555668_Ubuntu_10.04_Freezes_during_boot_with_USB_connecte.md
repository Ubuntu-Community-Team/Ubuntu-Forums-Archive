---
title: "Ubuntu 10.04 Freezes during boot with USB connected KVM Keyboard and Mouse"
date: 2010-08-18
forum: Desktop Environments
---

### Post by artieman1 on 2010-08-18
I have been battling this issues for about a year now.  Kind of got tired of dealing with it, but inevitably I go away for vacation or something and I lose power at the fort then the system will not come back up on it’s own.

Every time (100%) I power my system on with the single USB cable connected to it, my system hangs.  It did it on 8.x, 9.x and all versions of 10.x.  I have asked the questions before, but never get anywhere with it.  Finally I have found this Forum and figured out how to ask questions…  Weird, I know…
Anyway.  

The system goes through the BIOS check and gets to the GRUB loader.  If I do nothing, it hangs with a black screen just after it says that it is loading the kernel.
If I change the kernel commands to include the noacpi=apic or most other common fixes for what I have been told, USB, I get to the same place seemingly.

In reading through the forums and a little testing, I find that if I remove the splash and the quiet commands (obviously snicker), I am able to see where it is really stopping, but does not make sense to me.

The last informational text that appears to be processed is one of

“Registered Protocol Family 1”

There is nothing in the SYSLOG, MESSAGES or DMESG at all for this boot.  I would assume that the system is not to a point where we can log this data…

Any guidance???
This is an AMD Phenom II x4 running 10.04 64bit Ubuntu
The USB connected device is an Avocent KVM 4 port with Audio and USB.

Any help would be appreciated.  Even guidance on what to look at up to this point!!!

---

### Post by artieman1 on 2010-08-26
Help anyone?

---

