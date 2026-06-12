---
title: "Dual-boot problem"
date: 2005-09-02
forum: Desktop Environments
---

### Post by carigada on 2005-09-02
I am relatively experienced with Windows but a newbie when it comes to Linux.  I would really appreciate some help with this problem.

I had a nice dual-boot setup with XP and Kubuntu using GRUB as the boot manager.

I'm not sure what happened, but a few days ago the PC wouldn't boot at all.  If I selected XP I got half a page of 99 99 99 99 etc.  If I selected Kubuntu, I got an error message about the partition not being recognised (Sorry but I didnt write it down).

I used fixmbr and fixboot which allowed me to boot to XP again, but of course GRUB had gone. I can still boot to Kubuntu using a boot floppy. 

I really tried to RTFM but nothing seems to work as it should.  

I tried to re-install GRUB using the install CD along these lines [http://www.ubuntuforums.org/showpost.php?p=242484&postcount=3](http://www.ubuntuforums.org/showpost.php?p=242484&postcount=3) but at the end just got a message saying that the GRUB package had failed to install.  The same happened when I tried to install LILO.

I tried using a hex editor and saving the first 512 bytes on my boot floppy as a linux.bin file for the Windows XP boot loader (something that has worked OK in the past) but that just showed 'GRUB' at the top of the screen and wouldn't go further.  I tried booting into Kubuntu and dumped the first section of the partitions and MBRs on hda and sda using dd if=/dev/*da*of=/mnt/floppy/linux.bin bs=512 count=1 and using these in the Windows bootloader in the vain hope that this would work.  No success,only a flashing cursor.

I have three disks in my machine.  IDE1 Master (hda), IDE1 Slave (hdb) and a SATA, SCSI1 (0,0,0) (sda).  Windows is installed on hda and Kubuntu is installed on sda.

I hope I'm not being really stupid here, but I can't work it out and I need some help.  I don't really want to re-install Kubuntu. 

Thanks in advance.

---

### Post by KPingus on 2005-09-02
Doesn't sound very good, eh.
Could you paste your /etc/fstab here? It might be that something is messed up with the mount points. If you can boot using the floppy (or a live CD or something), I strongly suggest you back up all important data before attempting *anything else*.

Edit: Now that I re-read your message, it might not be the first 512 bytes of the floppy that you want to copy for use in XP, but the first 512 bytes of the root partition instead. If /dev/hdaX is the mount point of / in your fstab, then:

```

dd if=/dev/hdaX of=linuxboot.bin bs=512 count=1

```

then copy that into Windows (using mcopy and *not* cp).

---

### Post by carigada on 2005-09-02
I think this is what you need.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /home           ext3    defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


I did try dumping the first 512 bytes of sda2 already.  I'll have another go and post the results here.....

---

### Post by carigada on 2005-09-02
Just a flashing cursor when I choose kubuntu, using dd if=/dev/sda2 of=linuxboot.bin bs=512 count=1

---

