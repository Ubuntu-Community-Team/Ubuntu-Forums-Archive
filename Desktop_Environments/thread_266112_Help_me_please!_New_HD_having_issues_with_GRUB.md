---
title: "Help me please! New HD having issues with GRUB"
date: 2006-09-26
forum: Desktop Environments
---

### Post by intelliprompt on 2006-09-26
I can't get into my Linux boot because of some unidentified problem, and I had a new HD coming so I figured I would wait and just reinstall Linux on new partitions on this new HD of mine, but I've discovered that I can't start my computer with windows because there is a GRUB error (error 5, according to GRUB). Is there any way to remove GRUB without being on my Linux boot so that I may configure my new HD to windows and get all of my stuff set up? This is all very frustrating...

P.S. I tried installing Linux on the new HD without having done anything to the HD in windows XP, and it gave me some unmountable message, saying it couldn't mount to partionions because they were invalid or something. My HD is labeled in the Ubuntu partitioner as "unallocated" i believe.

---

### Post by Lin-X on 2006-09-26
Well, I'm a little unclear on your information about which drive we're discussing, but you have to format the drive before you install anything on it and I recommend formatting it as ext3. Just boot the Ubuntu cd; go to the Gparted ap and start it up; it's very user friendly --- explaining it here would be more confusing than just looking at it when you use it.

You should be able to proceed with it from there. May I suggest that, in the near future, you invest in a Knoppix, Damn Small, or Puppy live cd. These have saved my --- er --- ash many times, including yesterday, when I had a problem very similar to what you describe. I solved mine by using a Win98 floppy, typing fdisk/mbr at the prompt, and reinstalling Ubuntu to restore the Grub start. I could have done it from Knoppix just as easily.

Please post again when you solve your problem (you will!) so we all know what finally happened and what you did,

---

### Post by intelliprompt on 2006-09-27
I'm a complete beginner when it comes to Linux, how exactly would I open that application?

Ok, so I ran a search for GParted and I found the executable, then clicked on it and got the error:

Root privileges are required for running GParted
Since GParted can be a weapon of mass destruction only root may run it.

Also, will running GParted make the HD unusable to windows? I bought it mainly for media storage.

---

