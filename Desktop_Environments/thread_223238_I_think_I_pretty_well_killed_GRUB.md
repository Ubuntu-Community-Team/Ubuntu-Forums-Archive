---
title: "I think I pretty well killed GRUB"
date: 2006-07-26
forum: Desktop Environments
---

### Post by Blairboy on 2006-07-26
So, having followed this ([http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855)) guide, I can no longer boot into ubuntu.  
I finally figured out to run fixmbr/fixboot under the windows recover cd so I could at least boot into XP.

I've tried the "alternative install" cd for ubuntu 6.06 and ran the fix a broken boot option, but it just error's out with "exit status 20."  I ran a live cd and mounted the partition and then chrooted into it, to see if I could just reinstall grub with apt, but it tells me something along the lines of "can't find passwd" or "can't find user" or some similar crap.

I also tried running grub-install while chrooted, but it tells me something like "can't find ......." I can't remember the error message honestly.

I even tried using the super grub disk to restore grub correctly, but no dice.  The partition I need to boot with is /dev/hda5.  All files are accounted for, and yes, /boot is still intact.  If anyone knows how to either repair/reinstall grub or actually use the ubuntu cd to boot into my hd partition so I can reinstall grub, it would be helping me out TONS.

Thanks in advance, I know that's a lot of crap to read through.

---

### Post by diepruis on 2006-07-26
Have you tried running grub while chrooted and just setting it up from scratch again?

```

sudo chroot XXX
sudo grub

```

That worked for me.

---

### Post by Blairboy on 2006-07-26
Well, I loaded the live cd, ran mount /dev/hda5 /media/ubuntu, then ran sudo chroot /media/ubuntu.  Then if I try to type sudo anything, it tells me that it doesn't have a password or user file or something along those lines.  I can redo it and get the exact error message if need be.

---

### Post by Blairboy on 2006-07-26
Am I not chrooting correctly?  Also, is there no way to use the ubuntu cd to get just a root console from my /dev/hda5?  Because then I could just install grub with apt.

---

### Post by frikazoyd on 2006-07-26
[http://ubuntuguide.org/wiki/Dapper#How_to_use_Ubuntu_Installation_CD.2C_to_gain_root_user_access](http://ubuntuguide.org/wiki/Dapper#How_to_use_Ubuntu_Installation_CD.2C_to_gain_root_user_access)

---

