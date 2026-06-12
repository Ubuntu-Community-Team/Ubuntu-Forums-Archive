---
title: "write to and edit 2nd hard drive"
date: 2009-05-14
forum: General Help
---

### Post by dsimpson on 2009-05-14
I have a Dell dual 933Mhz cpu computer, with a 9Gb SCSI hard drive which has the OS on it (Unbuntu 9.04) and an 30Gb EIDE hard drive that I want to use for storing all my files and downloads. The problem being, on the 2nd HD there is a version of Ubuntu 7.10 which I would like to remove (delete) and clear the HD for storage purposes. How do I go about getting root privileges for the 2nd hard drive to remove the old OS so I can then store my files there. I need the SCSI hard drive, as the BIOS will only boot to that drive. The boot HD is listed 2nd, as /dev/sdb1 and the storage HD is listed 1st as /dev/sda1. Any help would be greatly appreciated.****

---

### Post by dsimpson on 2009-05-15
*BUMP* Anyone?? :)

---

### Post by stretch427 on 2009-05-15
Are you just planing to wipe the IDE drive? and have you already got a system working on y our 9GB drive or are you starting from scratch? 
The way to do this would be using G-parted or something like it to write your drives. 
You would make the 9GB drive the partition for booting and to house the linux OS and then set the 30GB as your home directory. 
Don't do this if you have data already stored. But it seems like 9 GB is not much to back up... 
Don't know if this helped but beset of luck.

---

### Post by tombott on 2009-05-15
> **dsimpson said:**
> I have a Dell dual 933Mhz cpu computer, with a 9Gb SCSI hard drive which has the OS on it (Unbuntu 9.04) and an 30Gb EIDE hard drive that I want to use for storing all my files and downloads. The problem being, on the 2nd HD there is a version of Ubuntu 7.10 which I would like to remove (delete) and clear the HD for storage purposes. How do I go about getting root privileges for the 2nd hard drive to remove the old OS so I can then store my files there. I need the SCSI hard drive, as the BIOS will only boot to that drive. The boot HD is listed 2nd, as /dev/sdb1 and the storage HD is listed 1st as /dev/sda1. Any help would be greatly appreciated.

This guide should help you:

[http://tombott.com/Automatically_Mount_Additional_HD_in_Ubuntu_8.10](http://tombott.com/Automatically_Mount_Additional_HD_in_Ubuntu_8.10)

It was written for 8.10 but applies to 9.04 as well.

You will need to delete the existing partition on the 2nd HD, you can do this using Gparted.

Let me know if you need any further help.

Tom.

---

### Post by dsimpson on 2009-05-15
Hi stretch427 and tombott,
    Thanks for the reply, I will check out the advice you posted and give it a try. To answer your questions and let you know my starting point, I have this right now.
    On the 9Gb HD is the Ubuntu 9.04 OS, this will be my only use for the HD, holding the OS that I am booting to now. On the 2nd drive is an older version of Ubuntu OS that I want to remove so I can have the extra space for storing my files. I store mainly genealogy and language (audio) files, with some photos for editing and then they are stored on a usb disc. This is a personal computer for home use only. It is networked to another computer, (wife's) for printing purposes, other than that my needs are pretty simple.

---

### Post by dsimpson on 2009-05-15
Hi tombott.
    I did the gparted guide up to the point of installing ext3 and it stopped there giving me the message "an error occurred while applying the operations" See the details for more information.

IMPORTANT
If you want support, you need to provide the saved details!
See [http://gparted.sourceforge.net/larry/tips/save_details.htm](http://gparted.sourceforge.net/larry/tips/save_details.htm) for more information.

I tried reformatting and applying again but it did the same thing, I saved the error, but don't know where to go to find it and submit it to gparted.sourceforge.net. 

What might be the next step? What could be the cause of the failure?

---

### Post by KhurramM on 2009-05-15
Can u unmount the drive u want to reconfigure, using cli.

Then open gparted and format it all.

Next do what ever partitioning u want.

Hope this helps.

---

### Post by dsimpson on 2009-05-15
thank you for the suggestion, I tried unmounting but it already was, I had done it in Gparted late last night, tried running again and everything worked today. On with creating a mount point and taking ownership of my disks.

---

### Post by dsimpson on 2009-05-15
**Done**, ***thanks to all, this is a great forum!!!***

---

