---
title: "Discussion - https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk"
date: 2012-06-29
forum: Documentation and Community Wiki Discussions
---

### Post by Elfy on 2012-06-29
Please use this thread for discussion regarding

[https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk)

Support threads should be posted in normal forums.

Thank you.

---

### Post by meark on 2012-08-15
I prefer following version:
(Assuming target size is 10GiB=2621440x4KiB)
```

cat /host/ubuntu/disks/root.disk /dev/zero | dd iflag=fullblock bs=4K count=2621440 of=/host/ubuntu/disks/newroot.disk
fsck -y -f /host/ubuntu/disks/newroot.disk
resize2fs /host/ubuntu/disks/newroot.disk 10G

```
Neither dd nor resize2fs, alone, changes the size of the image , so the concatenation part is mandatory.

---

### Post by bcbc on 2012-10-07
I've updated the wiki for release 1.6 of the script.

There are no specific changes required to support Ubuntu 12.10, but I've added support for grub-legacy users (original install on Ubuntu 9.04 or earlier), and there's some minor cleanup.

I've also added signed checksums of the scripts so that users can verify them before using.

---

### Post by wcypierre on 2012-10-11
For the step 5 of manual resize, there's a missing quote(') at the rsync command(at the end of exclude /home)

> 
rsync -av --exclude '/sys/*' --exclude '/proc/*' --exclude '/host/*' --exclude '/mnt/*' --exclude '/media/*/*' --exclude '/tmp/*' --exclude '/home/*/.gvfs' --exclude **'/home/*/.cache/gvfs'** --exclude '/root/.gvfs' --exclude '/var/lib/lightdm/.gvfs' / /media/newdisk


It didn't worked for me then only I noticed that there's a missing quote and now the rsync works for me

---

### Post by bcbc on 2012-10-11
> **wcypierre said:**
> For the step 5 of manual resize, there's a missing quote(') at the rsync command(at the end of exclude /home)



It didn't worked for me then only I noticed that there's a missing quote and now the rsync works for me

Thanks for pointing that out. I'll fix it!

---

### Post by wcypierre on 2012-10-11
> **bcbc said:**
> Thanks for pointing that out. I'll fix it!

you're welcome :). I was relatively surprised that it wasn't working until I found the missing quote then only I get what it doesn't works :p

---

### Post by bcbc on 2012-10-11
> **wcypierre said:**
> you're welcome :). I was relatively surprised that it wasn't working until I found the missing quote then only I get what it doesn't works :p

Thankfully most people take my advice and use the script which I test on an ongoing basis. 

But I should have rerun the manual commands after each edit so my apologies for that.

---

### Post by nathan73 on 2015-05-10
Why do I have to switch the disk names? if they're copied then they should be identical, right?

---

### Post by bcbc on 2015-05-11
> **nathan73 said:**
> Why do I have to switch the disk names? if they're copied then they should be identical, right?
Grub boots by searching for a file on any partition named /ubuntu/disks/root.disk. It loads the boot menu directly from inside this file (/boot/grub/grub.cfg), and this boot menu also directly refers to it by name (and partition). By switching the disk names it will naturally start using the new copy. If you don't, it will just keep booting the old one.

---

### Post by nathan73 on 2015-05-11
> **bcbc said:**
> Grub boots by searching for a file on any partition named /ubuntu/disks/root.disk. It loads the boot menu directly from inside this file (/boot/grub/grub.cfg), and this boot menu also directly refers to it by name (and partition). By switching the disk names it will naturally start using the new copy. If you don't, it will just keep booting the old one.

I did that, but it doesn't give me any more disk space. I was hoping to keep the old root as a back up, but do I have to delete it anyway? If so, how do I safely delete it? (assuming that the new root is confirmed to be working fine)

---

### Post by bcbc on 2015-05-12
> **nathan73 said:**
> I did that, but it doesn't give me any more disk space. I was hoping to keep the old root as a back up, but do I have to delete it anyway? If so, how do I safely delete it? (assuming that the new root is confirmed to be working fine)
Not sure why it wouldn't give you any more disk space... did you make it bigger than the old one? 
You don't have to delete the old one. 
If you want to delete it, delete it the same way you'd delete any file.

You can copy the root.disk to make a backup - usually I'd do this before some major update (like upgrading to the next release). Then you can just swap it back if something goes wrong. But in general, it's an inefficient way of backing up data because it copies the OS (which can be reinstalled) and even the free space on the virtual disk. So you might have 1 GB of data but you're backing up between 5 and 30 GB of root.disk.

---

