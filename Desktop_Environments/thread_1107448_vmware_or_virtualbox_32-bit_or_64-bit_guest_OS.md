---
title: "vmware or virtualbox? 32-bit or 64-bit guest OS?"
date: 2009-03-26
forum: Desktop Environments
---

### Post by shinew on 2009-03-26
Hello, I'm running on 64-bit Ubuntu Intrepid w/ 2.6.29 kernel, Intel 2.6Ghz core 2 quad with 8GB RAM + 150GB Raptor & other 3 internal drives.

I have 2 questions and I'm wondering what will give me the best performance for the VM:
1) virtualbox or vmware?
2) for the guest OS, should I use the 64-bit version of 32-bit version?

thanks.


!!argh.... I'm a moron, posted in the wrong section again. heading to the virtualization section. moderator please delete the message. sorry!

---

### Post by graysky on 2009-03-26
I like virtualbox on my system (X3360/4 gig RAM).  I only have the x86 windows xp installed since I use it so rarely.  How many memory do you want to give the VM?  If the answer is >3.2 gig, then install the 64-bit version.

---

### Post by shinew on 2009-03-26
> **graysky said:**
> I like virtualbox on my system (X3360/4 gig RAM).  I only have the x86 windows xp installed since I use it so rarely.  How many memory do you want to give the VM?  If the answer is >3.2 gig, then install the 64-bit version.

so the decision to go for a 64-bit or 32-bit guest OS is mainly based on memory? most of time I would be able to give more than 3GB, unless I'm running both Windows & OS X as VMs. 

Also which one would have offer better performance for the guest, vista or xp?

---

### Post by andrea000 on 2009-03-26
win xp as guest definitely vista is a resource hog.

---

### Post by shaggy999 on 2009-03-26
You should be aware that there is an issue w/ 64-bit Linux Guests in Virtualbox that makes it impossible to use the "Shared Folders" feature. I banged my head against the monitor for like 5 hours before finally stumbling across a conversation discussing the broken aspect of this feature. 32-bit linux guests work fine.

64-bit linux guests are able to take advantage of some extra features offered by the CPU, however... plus that 4 GB limit. Basically the 64-bit linux will be "aware" of the various cpu extensions available in 64-bit processors.

---

### Post by shinew on 2009-03-27
thanks for the help! I've decided to run vmware & 32-bit XP.

---

