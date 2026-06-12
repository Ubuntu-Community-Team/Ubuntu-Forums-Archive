---
title: "Automount Problem"
date: 2010-08-07
forum: Desktop Environments
---

### Post by ttoolin on 2010-08-07
I am using Ubuntu 10.04, and I wish for my second HDD to automount at bootup, and be a shared read drive to anyone on my home network.  I have accomplished this on version 8.04, but I am having trouble now (most likely because I forgot how I did it).

Before I used mountmanager, my second HD (volume label: MediaDrive) came up as a mount option on my 'Places" dropdown menu.  Using mountmanger, and a few attempts, I have achieved an automount state, but now I have two listings of 'MediaDrive' on my 'Places" dropdown, and one doesn't work.  Also, if I unmount the drive, I cannot remount it again, without rebooting the computer.

This is how my /etc/fstab file looks now (after use of mountmanager):

```

/dev/fd0 /media/floppy0 vfat noauto 0 0
UUID=ec741081-f857-4267-a0f5-947ed3adc110 / ext4 defaults 0 1
UUID=12b78db8-c4ef-4cfa-bcc7-5b51bd4cea7f swap swap sw 0 0
UUID=f0d141a5-bf44-4c95-ac6c-2d6332797477 /media/MediaDrive ext3 users 0 0

```

In my tinkering around, I thought it might be wise (and I was quite mistaken) to take out the media/MediaDrive part of the third line.  I was hoping, since the UUID was there, that it would initialize just like my primary HDD.  When I tried to boot the computer after that blunder, it hung during boot up.  I had to get quite creative to figure out how to get enough root access to remove the faulty statement from the /etc/fstab file.

Thanks!

---

