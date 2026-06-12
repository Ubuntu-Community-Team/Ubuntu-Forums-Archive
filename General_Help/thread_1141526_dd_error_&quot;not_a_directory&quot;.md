---
title: "dd error &quot;not a directory&quot;"
date: 2009-04-28
forum: General Help
---

### Post by ram_are on 2009-04-28
I'm trying to create an image file of my Ubuntu hard drive and save it to my external USB hard drive. For some reason, it gives me an error saying that the location for my external hard drive does not exists. Here's what I get...

fez@desktopfez:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00074873

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18796   150978838+  83  Linux
/dev/sda2           18797       19457     5309482+   5  Extended
/dev/sda5           18797       19457     5309451   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    c  W95 FAT32 (LBA)
fez@desktopfez:~$ sudo dd if=/dev/sda  of=/dev/sdb/image.img
dd: opening `/dev/sdb/image.img': Not a directory
fez@desktopfez:~$ sudo dd if=/dev/sda  of=/dev/sdb1/image.img
dd: opening `/dev/sdb1/image.img': Not a directory
fez@desktopfez:~$ 



What am I doing wrong?
Thanks

---

### Post by bumanie on 2009-04-28
You really only need to make a back of sda1 as sda2 is only a logical partition containing swap. Also, to ensure the filesystem is a stable state, do the procedure off a live cd.

> sudo mkdir /mnt/backuppartition  makes a place to mount the backup partition > sudo mount /dev/sdb /mnt/backuppartition> cd /mnt/backuppartition> sudo mkdir backup-28-04-2009> cd backup-28-04-2009> sudo dd if=/dev/sda1 of=jaunty_backup_image bs=16384  copies the entire image without compressing or with compression of the image do> sudo dd if=/dev/sda1 bs=16384 | gzip -1 > jaunty_backup_image.gzTo restore the image at a later date > sudo gunzip -c jaunty_backup_image.gz | dd of=/dev/sda1 bs=16384When using compression, you can choose numbers form 1-9, with 1 being 'light' compression and 9 much 'heavier' compression. Hope this works. I have used it before and it worked fine for me. I haved assumed /dev/sdb is your external hard drive name, if not, change to to the appropriate name.

---

### Post by ram_are on 2009-04-28
Thank you bumanie for your reply. I tried exactly what you wrote but now I get an error saying "no space left on the device". I have over 200 GBs left on my drive so I don't know why it's complaining about that.

---

### Post by msniner on 2012-03-04
**Reason:** dd cannot accept an output destination of [FONT=Courier New]/dev/sd##[/FONT] if the destination is a file.
(read on...)

In case you're coming from Google and many of the forums there yield useless answers and off-topic stuff, here's what you need to do to get your hard drive ripped/copied to a disk image such as **IMG** or **ISO**:

(edit) if you are getting permission denied errors, please put "sudo" in front of the command. This will give you very high administrative rights to run this command.

**Step 1:** Find out where your drive is mounted at. To do that very simply, you use the Disk Utility software bundled with Ubuntu. Go click your hard drive, and click the partition that you would like to export into a disk image. Disk Utility will tell you at the bottom of the user interface the mount path. 

In this example assume it's mounted at **/dev/sdb1**

**Step 2:** Find out what mount path is your destination drive is. For example, I plugged in my own USB stick and Ubuntu's Nautilus (its a file explorer) opens and its name is shown on the left side. In this example, assume that my USB stick has the name of "**MyStick**"

**Step 3:** Begin the process! Open Terminal and type this in:

dd if=/dev/sdb1 of=/media/MyStick bs=512

Astute readers may have notice that I used [FONT=Courier New]if=/dev[/FONT].... and [FONT=Courier New]of=/media[/FONT]..., and not both [FONT=Courier New]/dev[/FONT]. Why is "of=" given a different syntax? That's because /dev is only used if you are doing a block level copying. That is, copying to another physical disk.
Because you are copying to a file (an ISO file to be exact), you need to use [FONT=Courier New]/media/[/FONT]... to acheive this.

Hope this helps!

---

### Post by nothingspecial on 2012-03-04
Thanks for the information.

But please don't bump ancient threads to the top.

Closed.

---

