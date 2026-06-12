---
title: "Unable to Set Superblock Flags"
date: 2009-04-08
forum: General Help
---

### Post by st162 on 2009-04-08
OK this has been driving me nuts for about a week now, what I had was a Linux partition of 8GB, and dual boot with XP, everything was going fine for years and I manage to fix any small errors that I come across, but this one has got me.

While I was in XP I decided that I wanted to resize my ext3 partition to 20GB (my / drive which is /dev/sda2) didn't get any errors at all until I then rebooted and got grub error 17, so I reloaded my XP's MBR and then reinstalled grub by booting from the live CD, I can read the entire contents of the drive fine, it resized to 20GB perfectly. 

Grub boots up again, then another error, it couldn't find the kernel(cant mount partition) (hd0,2) etc.. so I booted the live CD and edited my menu.lst and changed it to boot the kernel from hd0,1. then the kernel loaded fine now then half way through loading the kernel, I get a fsck error.

So I was then left with a terminal, then what I did was :
# fsck /dev/sda2

the return I get is:
Group decriptors look bad... Trying backup...
Unable to Set superblock flags on /dev/sda2

i tried a few different switches like -F -o full -m -y, and not getting anywhere. I also tried something else like manually recovering every reference to the backup superblocks and that didn't work either. I've never had this problem before and looks like the drive isn't corrupt and is totally readable from the live CD, i Googled everywhere and cannot find a solution.

I hope I've detailed enough of the problem, but if you guys need any more info, I can provide it, Thank-you so much in advance if you can help me, it is my work PC and need it running :S, XP still boots fine, but it sucks!

---

