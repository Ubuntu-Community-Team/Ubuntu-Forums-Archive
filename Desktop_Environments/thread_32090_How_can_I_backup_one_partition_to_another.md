---
title: "How can I backup one partition to another?"
date: 2005-05-06
forum: Desktop Environments
---

### Post by epb613 on 2005-05-06
I have 2 10gb partitions on my hard drive. One of them contains Ubuntu; the other was made originally to try out a different distro. But I have become happy with Ubuntu and I wanted to know if instead I could use the 2nd partition to backup my first one (the one I'm using). Is this possible? (As an idea, I was thinking maybe it would be using dd? I know dd is used to make iso's which is a disk image, so maybe you could use it to make a copy of one partition to another?)

Thanks in advance!

---

### Post by Xerampelinae on 2005-05-06
I have two hdds in my machine.  I just use cp (and tar and bzip) to back up my /home directories.

Might as well do the same thing here.  Make sure you use the -a flag.


Or, you might try rsync for a more intelligent copy...

---

### Post by epb613 on 2005-05-06
Um, first of all, could use describe the process in more detail for my newbie self?

Second of all, let's say I werent to zip it - then would be possible to make it so I could boot off of either partition?

---

### Post by Xian on 2005-05-06
It would seem to be easier to do this from a LiveCD, but you could try it directly from your root directory. Anway, assuming that your mount point for Ubuntu is "/" and the other is something like "/storage", then just open a terminal and issue this command (replacing the actual points for your box):

$ sudo cp -rpfd /* /storage

---

### Post by epb613 on 2005-05-06
How could I then tell grub to let my boot from my new partition (hda2) as well as my current one (hda4)? Thanks.

---

### Post by kosmic on 2005-05-06
Use partimage is a backup program and is very easy to work with it, if you want to copy the boot menu you have to use the 'dd' comand.

do man dd to see the options


hope it helps

---

### Post by c_dog on 2005-05-06
[QUOTE=epb613]I have 2 10gb partitions on my hard drive. One of them contains Ubuntu; the other was made originally to try out a different distro. But I have become happy with Ubuntu and I wanted to know if instead I could use the 2nd partition to backup my first one (the one I'm using). Is this possible? (As an idea, I was thinking maybe it would be using dd? I know dd is used to make iso's which is a disk image, so maybe you could use it to make a copy of one partition to another?)

Thanks in advance![/QUOTE]

```
sudo rsync -a -v  /source_partition/ /destination_partition/
```

rsync is nice because it keeps all the permissions in place and will freshen only the files that have changed instead recopying everything again.

---

### Post by c_dog on 2005-05-06
[QUOTE=epb613]How could I then tell grub to let my boot from my new partition (hda2) as well as my current one (hda4)? Thanks.[/QUOTE]

You'd need put something like this in your /boot/grub/menu.lst file
```
title linux-default
       root	(hd0,3)
       kernel 	/boot/vmlinuz root=/dev/hda4 ro quiet splash
       initrd	/boot/initrd.img

title linux-new
       root	(hd0,1)
       kernel	/boot/vmlinuz root=/dev/hda2 ro quiet splash
       initrd 	/boot/initrd.img

```

---

### Post by Xerampelinae on 2005-05-06
Yeah, there's some mis-information in this thread.  You don't have to use dd to be able to boot from the partition.  You just have to add the grub entry as described above.

Also, don't use the cp command with /, since it includes /mnt/*  (although you could tell cp to exclude this directory).

A better way is to mount your / partition a second time in say, /mnt/hda4 and your backup partition in /mnt/hda2  (you can make up whatever directories you want in /mnt, in this case I just named them the same as the device names).  Then you would say

```

rsync -rav --delete /mnt/hda4/  /mnt/hda2/
# run this the first time without --delete to make sure it works correctly.

```

The delete command in rsync will delete stuff on your backup partition that have been deleted on your primary partition.  Otherwise your backup partition would keep all the old junk around you've deleted from your primary partition.

---

### Post by jodef on 2005-05-06
Some nice info in this thread I've always used partimage for backing up partitions but rsync looks like a superior option :
> The delete command in rsync will delete stuff on your backup partition that have been deleted on your primary partition. Otherwise your backup partition would keep all the old junk around you've deleted from your primary partition. > rsync is nice because it keeps all the permissions in place and will freshen only the files that have changed instead recopying everything again. Will have to read up on rsync.

Thx guys.

---

