---
title: "Can't mount external ntfs drive as read/write"
date: 2007-06-28
forum: Desktop Environments
---

### Post by cri on 2007-06-28
I have a 200GB external USB Seagate hard drive. It was originally formatted as fat32. As fat32, however, it was never recognized by my Feisty desktop. I would plug it in and I'd never get a desktop icon or automount. I could mount manually but that was a pain. Search around these forums and you'll find plenty of other posts about this problem. I mention it here so others in a similar situation may find this post. 

A half-way fix was to convert the drive's filesystem to ntfs. As ntfs the drive now automounts but it does so as read-only. I have ntfs-3g installed and have checked the "Enable write support for external device" option in ntfs-config. But no luck getting read/write at automount. 

As a Linux old schooler I want to put an entry for the drive in /etc/fstab to explicitly set the mount privileges and FS type. However, it seems that the device node the drive attaches to varies with every automount. I tried putting an entry in /etc/fstab using the device node registered on an automount but the next time I plugged in the drive it registered at another spot in /dev. 

How can I get my external ntfs drive to reliably automount read/write? How should USB devices be handled in /etc/fstab? 

Many thanks.

---

### Post by warcriminal on 2007-06-28
The problem is that it is formatted as NTFS.  UBUNTU cannot recognize the format.  You need to use a utility such as NTFS-3G to see the drive.

There is a step by step guide at;

[http://www.goitexpert.com/entry.cfm?entry=Make-Your-Windows-Share-ReadWriteable-From-Linux](http://www.goitexpert.com/entry.cfm?entry=Make-Your-Windows-Share-ReadWriteable-From-Linux)

Replace the share directory //server/share with the external hard drive mount point; /dev/sda1

And you're off to the races.

---

### Post by pingpongboss on 2007-06-28
> **warcriminal said:**
> The problem is that it is formatted as NTFS.  UBUNTU cannot recognize the format.  You need to use a utility such as NTFS-3G to see the drive.

There is a step by step guide at;

[http://www.goitexpert.com/entry.cfm?entry=Make-Your-Windows-Share-ReadWriteable-From-Linux](http://www.goitexpert.com/entry.cfm?entry=Make-Your-Windows-Share-ReadWriteable-From-Linux)

Replace the share directory //server/share with the external hard drive mount point; /dev/sda1

And you're off to the races.

that doesn't take care of the automount issue tho

i have the same problem where ubuntu refuses to automount my seagate external harddrive :T

---

### Post by hamster_billy on 2007-07-06
I'm also having problems, though they aren't confined to external NTFS drives, but FAT flash drives too.

Since I upgraded to Feisty my (as far as I remember everything worked fine in Edgy) my two Sandisk Cruzer flash drives (FAT) have failed to automount. Peculiarly one has consistently failed ever since the upgrade, and one failed only after a couple of weeks. I can manually mount them, but it's a pain. Other flash drives I've tried seem to work fine, as do SD cards and MemorySticks, in my laptop's built-in reader, and CF cards in a PC card adaptor. I wonder if the Cruzers don't automount because at some point I failed to manually eject them before unplugging - it's the only thing I can think of. Is there a way to reset this?

Today I plugged in my Freecom external NTFS hard drive, which has automounted successfully in the past on Feisty, but this time it automounts as root read only. It took me a long time to figure out that I have to manually mount this without using the 'mount' command: sudo ntfs-3g /dev/sdb1 /media/usbdisk.

If anyone can tell me how to fix it so that all usb drives automount read/write for current user that would be fantastic. I've found it pretty frustrating that since ntfs-3g came out, a lot of instructions for manually mounting and other fixes seem to have been taken down from ubuntuguide.com. It seems to be generally assumed now that everything works just fine, which isn't the case.

---

### Post by jimbo99 on 2007-07-07
Install the "ntfs-config" utility from the feisty repository.  Then run it.  Indicate you want to read/write also.  You should be able to find it using synaptic package manager.

That will make the appropriate changes in your /etc/fstab file to provide an auto-mount.

---

### Post by pingpongboss on 2007-07-08
> **jimbo99 said:**
> Install the "ntfs-config" utility from the feisty repository.  Then run it.  Indicate you want to read/write also.  You should be able to find it using synaptic package manager.

That will make the appropriate changes in your /etc/fstab file to provide an auto-mount.

I've had ntfs-config installed and set to "read+write" already, and it has not helped with the auto-mount problem.

---

