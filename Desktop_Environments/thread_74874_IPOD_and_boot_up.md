---
title: "IPOD and boot up"
date: 2005-10-12
forum: Desktop Environments
---

### Post by greenwom on 2005-10-12
I'm running hoary and my ipod (usb) was mounting fine with the stock install.  
I tried getting it to mount and sync with gtkpod.

Well dummy me I pulled the plug on the Ipod with out mounting it, it locked the system and then I get a file system error at start up when checking root file system runs.  I get pushed to a prompt and it's read only.

I run it in recovery mode and it's still read only.

I followed the instruction to mount it as rw and it worked but I don't know what to change back....

where do I start... :mad:

Edit/update: I mounted the drive and ran fsck per instruction, now my grub is hosed.  Did I just kill my system or just the boot?  (how do I tell)
I'm getting a grub error 17 (there is allot of google info on the error; it looks like what ever the file systm error was that the partition isn;t present.  I guess fsck killed that part of the drive.?

What to do?  Really I'd like to know if the rest of my system is still intact... I just finished getting it all dialed in.

---

### Post by Alexander Kirillov on 2005-10-13
[QUOTE=greenwom]I'm running hoary and my ipod (usb) was mounting fine with the stock install.  
I tried getting it to mount and sync with gtkpod.

Well dummy me I pulled the plug on the Ipod with out mounting it, it locked the system and then I get a file system error at start up when checking root file system runs.  I get pushed to a prompt and it's read only.

I run it in recovery mode and it's still read only.

I followed the instruction to mount it as rw and it worked but I don't know what to change back....

where do I start... :mad:

Edit/update: I mounted the drive and ran fsck per instruction, now my grub is hosed.  Did I just kill my system or just the boot?  (how do I tell)
I'm getting a grub error 17 (there is allot of google info on the error; it looks like what ever the file systm error was that the partition isn;t present.  I guess fsck killed that part of the drive.?

What to do?  Really I'd like to know if the rest of my system is still intact... I just finished getting it all dialed in.[/QUOTE]


You can get the live CD and boot from it, then try manually mounting the hard drive partitions to see if they are intact. Or you can use system rescue CD for similar purposes ( [www.sysresccd.org](www.sysresccd.org) ). It contains partition editor, and it can also be used to reinstall GRUB. Can't provide much detail, though.

---

