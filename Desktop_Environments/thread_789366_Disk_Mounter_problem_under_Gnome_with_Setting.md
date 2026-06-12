---
title: "Disk Mounter problem under Gnome with Setting"
date: 2008-05-10
forum: Desktop Environments
---

### Post by calif99x on 2008-05-10
Hi:

This is likely a problem of experimenting in an area with not enough knowledge.  

I am having a problem with large file access after upgrading to Hardy 8.04.  In browsing around, I saw references to lfs option for mounting files and it seemed it might be applicable.

In looking at properties brought up by Gnome Disk Mounter, it had a setting area and what looked like a place where options could be added.  OK, so I put "lfs" there, rebooted the system just to be sure; and got an "Invalid option" error message when attempting to mount the drive.

I can see the drive on the top gnome panel, but left click to mount repeats the error message, and I can't seem to locate the conf file where the settings are stored to manually edit them.

The docs on Gnome Disk Mounter are pretty thin, and the utility seems to have a major flaw in that it won't tell me the specific bad option (I can guess though), nor give me a chance to fix it.  Also, without mounting the drive I can't access the setting area where I added the option.

Any pointers or help would be great.

---

### Post by njparton on 2008-05-12
Is this problem with a local disk or over a network?
 
What's the filesystem of the partition?
 
Can you post your /etc/fstab file?

---

### Post by calif99x on 2008-05-13
I was able to fix this problem by using gconf-editor to edit the settings.  I was looking at /etc/fstab, and other areas, but since gnome stores it's settings in a XML schema, that was not helpful.  

Ultimately I got a couple of tips to poke around using this utility which is somewhat similar to MS Windows regedit.  I found the storage section, and removed the options I had added.  The disk was immediately mountable.

I have still not solved the original problem of why network of large files seems to freeze after about 100MB of data transfer, so that is still work in progress.

Cheers

---

