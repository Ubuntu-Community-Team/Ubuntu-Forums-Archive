---
title: "Changing Home Partition"
date: 2005-12-28
forum: General Help
---

### Post by musther on 2005-12-28
I'm changing my home partition, it's no longer going to be /dev/hdb1, it'll be /dev/hda1, how do I tell ubuntu this?

Also, if I copy everything on my old home, to my new one (including hidden stuff of course), will all be well?

Cheers!

---

### Post by Adrenal on 2005-12-28
*not sure if this is all perfect, could someone please verify(musther, do not follow until this is verified)*
Mornin'.
Firstly, to answer your second question, yeh, do that, it will be all good in the hood.
Secondly, the solve your first probem, do the following:
sudo cp /etc/fstab /etc/fstab.bak
sudo gedit /etc/fstab
Look for the line
/dev/hdb1       /home           ext3    defaults        0       2
replace it with
/dev/hda1       /home           ext3    defaults        0       2

Keep in mind, upon making this change, the partition will instantly be your homefolder. So, in the root of the drive, make a directory called 'Home', then, inside that directory make a folder called '[yourusername], then copy and paste all of your stuff.

---

### Post by Bachstelze on 2005-12-28
It seems well, except two little things

1) The changes will become effective on reboot or on the command sudo mount -a, not instantly.

2) The new partition being the /home directory, the folders in the root of the drive must be the usernames. For example if your soon-to-be /home is currently mounted in /mnt/hda1, you should run

sudo cp -R /home /mnt/hda1
sudo chown -R user /mnt/hda1/user
sudo chmod -R 755 /mnt/hda1/user

---

### Post by Adrenal on 2005-12-29
Thanks for the corrections HymnToLife

---

### Post by chaumurky on 2005-12-29
There are many ways to skin a cat...

I would go

```
 sudo rsync -aS /home/. /mnt/hda1/.
```

nice one liner.

Just out of curiosity, what drive/partition are you booting from? I thought it would be hda1.

---

### Post by bishop on 2006-01-03
[QUOTE=chaumurky]There are many ways to skin a cat...

I would go

```
 sudo rsync -aS /home/. /mnt/hda1/.
```

nice one liner.[/QUOTE]Would this one liner replace ALL of the above code? Or just one part of it? Working from Kubuntu, I screwed up on my first attempt and had to go back to my original configuration, and I haven't tried it again since. But if this is ALL that I would have to do (replacing the appropriate partition information of course), then I think I could probably get this done this evening in a test.

---

### Post by 5-HT on 2006-01-03
[quote=bishop] Would this one liner replace ALL of the above code? Or just one part of it? Working from Kubuntu, I screwed up on my first attempt and had to go back to my original configuration, and I haven't tried it again since. But if this is ALL that I would have to do (replacing the appropriate partition information of course), then I think I could probably get this done this evening in a test.[/quote]Not too familiar with rsync, but I believe (someone please correct me if I'm wrong) that this will copy anything from the old home partition to the new one (given that it resides on hda1).

So you should still need to update /etc/fstab to reflect the new home partition.

---

### Post by bishop on 2006-01-03
Doesn't work for me. 

> rsync: mkdir "/mnt/sda2/." failed: No such file or directory (2)
rsync error: error in file IO (code 11) at main.c(422)
rsync: connection unexpectedly closed (8 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(434)Nothing that I've tried -- having tried just about every method on these forums to the letter -- has been able to move my home directory to the partition that I originally wanted (and was so sure I'd selected properly at installation) for it. I'm on the verge of just giving up on trying. I don't have any problems with my system right now and I'll just save files to the partition and leave my primary /home directory alone. :(

---

### Post by chaumurky on 2006-01-20
have you actually created /mnt/sda2 first? you need to do thet - i.e. [B]sudo mkdir /mnt/sda2

[/B]EDIT: actually, are you trying to do the same thing? Outline what you want to do, for example:

1: determine device of destination partition - e.g. /dev/sda2
2: determine (and create if required) the filesystem
3: make a placeholder for the drive to mount that's easy to recognose e.g. **sudo mkdir /mnt/sda2**
4: mount the partition e.g. [B]sudo mount -t <filesystem_type> -o rw /dev/sda2 /mnt/sda2
[/B]5: synchronize the drives i.e **sudo rsync -aSv /home/. /mnt/sda2/.        **(the 'v' is for verbose mode)
6: change the /etc/fstab to reflect the new partition as the source for /home i.e. /dev/sda2
7: reboot (or log out and log into root to free up /home, then unmount /home, then go **sudo mount -a**)

---

