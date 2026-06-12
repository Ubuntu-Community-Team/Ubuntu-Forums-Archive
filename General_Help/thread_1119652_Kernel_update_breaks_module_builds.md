---
title: "Kernel update breaks module builds?"
date: 2009-04-08
forum: General Help
---

### Post by wd5gnr on 2009-04-08
Well I just took the upgrade for 2.6.27-11 (to 2.6.27-11.31). My second sound cards quit working (I have manually brought Alsa up to 1.0.19 to support the motherboard sound which still works). Rebuilding the alsa modules fails. Also installing the new NVidia driver fails in a similar way. It looks like the source and/or headers are hosed since I get a lot of missing items in the kernel headers (BITS_PER_LONG, for example). I have rebuilt the NVidia module many many times and this is the only thing that has changed.

The Alsa build when you do an install puts things in 2.6.27-10 which makes me think something that links the running kernel, the source, and the modules is seriously busted.

Any ideas? Really hate to reinstall. Oh, and I tried to reverse the update but apparently that isn't possible. Tried booting on an older version kernel, but it was unhappy about something else and I decided to punt.

---

### Post by Gentex on 2009-04-08
Having similar issues myself after updating the kernel last night.  Totally borked my video drivers/display settings.  Even after updating the kernel with the restricted drivers I can't get a display better than 800x600.  It's a mess and the couple hours I spent last night mucking with it are about all I'm prepared to give for the moment.  

I'm hoping that updating to jaunty in a few weeks will help resolve the problem.

gentex

---

### Post by frodon on 2009-04-08
Custom/manual install of drivers outside the repositories implies that you must reinstall them again and again after each kernel update as custom drivers installs dissapeared. Everyone compiling or installing drivers manually should be aware of this, ubuntu is not to blame about such issues.

For the OP source and headers are not always automatically updated when kernel updates comes depending on the way you used to install them. If you installed them all one by one then synaptic may have not proposed you the update, in this case just install the missing updated headers they should be available in synaptic.

---

### Post by Gentex on 2009-04-08
Well, I went through synaptic to update the kernel with the nvidia drivers.  So, now the nvidia driver shows up in my list of hardware drivers as functional, but my resolution still won't go beyond 800x600.

Frankly, the "you're stupid and ubuntu didn't do anything wrong" tone of your response frodon isn't very helpful.  I've been through several kernel updates with this install of ubuntu and this is the first time it's caused this much trouble.  

As a reminder, a guide to nvidia driver installation can be found here:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by Yashiro on 2009-04-08
There could be an issue with the headers. A few other people have had issues with module rebuilds.

---

### Post by frodon on 2009-04-08
> **Gentex said:**
> Frankly, the "you're stupid and ubuntu didn't do anything wrong" tone of your response frodon isn't very helpful.  I've been through several kernel updates with this install of ubuntu and this is the first time it's caused this much trouble.  

As a reminder, a guide to nvidia driver installation can be found here:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)I understand your frustration but the tone you describe is not the one used.
What i said is typically related to the kind of guide you linked, using such guide a kernel update will leave you with low resolution mode because of missing drivers and this is independant of ubuntu. I you don't use the repositories nvidia drivers you just have to install your nvidia drivers again and it might be again the case on next kernel update. This is the main disadvantage of manual driver install.

> **Yashiro said:**
> There could be an issue with the headers. A few other people have had issues with module rebuilds.Yep i have noticed a couple of users with strange issues (often with sounds) after this kernel update. Check in launchpad if you can find a bug report related to your header issue, if there isn't any just creates one so that ubuntu dev can be aware of the issue.

---

### Post by wd5gnr on 2009-04-09
Since I am the OP I wanted to point out that YES I understand the ramifications of installing custom drivers. However, the point is that now compiling the modules BREAKS because of what would appear to be a header mismatch. I'm an experienced developer and I do not see any newer installs.

My current attempt is just build a custom kernel (haven't done that in a while) and then see if I can build the modules against that. But that's not a great answer.

---

### Post by frodon on 2009-04-09
Launchpad is the way to go as developers looks more launchpad than the forum, check for existing bug report and add your feedback.
If the problem comes from the update packages it is the faster way to get a solution.

---

### Post by wd5gnr on 2009-04-09
For the record, rebuilding the kernel worked -- sort of. At least modules are recompiling and I have the newest NVidia and both my soundcards work again.

Had to turn off Xen (bug already reported) and turn off Radeon support. Still get a post install error related to NVidia with the kdms stuff runs, but that may be my fault in some way, but the kernel does install and boot and now I can properly build modules again.

I have not had a lot of luck reporting bugs -- have reported several on launchpad. But will try to open a ticket for this one at some point.

---

### Post by wd5gnr on 2009-04-11
I'm not sure if I know how but I did manage to resolve it. I built my own kernel, although that had funny USB issues. While I had that kernel running I removed and reinstalled the "stock" kernel files. That seemed to work except for a few modules being out of whack. I manually unpacked those from the .deb file and now I'm 100% working again with the stock kernel (well I say 100% -- My XFi works again, and I can build the NVidia driver and use it). I did somehow revert to Alsa .17 but since my sound is working ok with it I'm not going to jump back to .19 since that may have been part of my problem to start with.

Anyway... fat dumb and happy now.

---

