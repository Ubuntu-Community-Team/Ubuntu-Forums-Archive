---
title: "External usb Hard disk not recognized (NTFS partition)"
date: 2009-03-03
forum: General Help
---

### Post by karantina7 on 2009-03-03
Hello, I am new to ubuntu and I have a problem when I plug my external usb WD passport 120GB. I have searched but I couldn't find any info about the problem or I am a copmlete noob. :) I am using Ubuntu intrepid and it's the only OS on this computer. The hard disk is recognized and completely usable on Win XP but it seems it won't mount on ubuntu. Intrepid can't mount NTFS partition drives or I need to install anything else?

Thanks in advance.

---

### Post by taurus on 2009-03-03
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```
That would be a lower case letter L, not number 1.

---

### Post by NetSkay on 2009-03-03
ubuntu uses ext3 or ext2 file system, and cannot mount or read NTFS file systems (which is what you have on the USB HDD); therefore, what u need to do is format and partition ur USB HDD in ext3 file system... 
you cannot convert file systems, so backup all ur data on another computer....

here is how to do the format/partition...

[http://www.cyberciti.biz/faq/howto-linux-formatting-external-usb-hard-disk/](http://www.cyberciti.biz/faq/howto-linux-formatting-external-usb-hard-disk/)

here is another link that will help u with the commands... it is very important to identify and make sure u have to correct name of the USB HDD, either sd* or hd* (where * can be any letter)
[http://www.faqs.org/docs/Linux-mini/Hard-Disk-Upgrade.html#PARTITION](http://www.faqs.org/docs/Linux-mini/Hard-Disk-Upgrade.html#PARTITION)

hope this helps... ill subscribe to instant notify, so if u have questions just post...

---

### Post by taurus on 2009-03-03
> **NetSkay said:**
> ubuntu uses ext3 or ext2 file system, and cannot mount or read NTFS file systems (which is what you have on the USB HDD); therefore, what u need to do is format and partition ur USB HDD in ext3 file system... 
you cannot convert file systems, so backup all ur data on another computer....


Wow!  Who claims Ubuntu cannot mount or read/write to ntfs filesystem?  You can read or write to it with ntfs-3g which should already install on your machine.

Maybe this link is for you, [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G).

---

### Post by blueridgedog on 2009-03-03
> **NetSkay said:**
> ubuntu uses ext3 or ext2 file system, and cannot mount or read NTFS file systems 

Ubuntu has native support for ntfs file systems "out of the box" so to speak.  It is not necessary to reformat the drive.  If it is not detected, it is potentially a USB issue.  As was suggested earlier, can you post the output of 

```
sudo fdisk -l
```

and

```
lsusb
```

---

### Post by karantina7 on 2009-03-03
Thanks for your answers, this is what I get with the command: sudo fdisk -l

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc0b5c0b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60046   482319463+  83  Linux
/dev/sda2           60047       60801     6064537+   5  Extended
/dev/sda5           60047       60801     6064506   82  Linux swap / Solaris

```

From what I see it has only my internal sata2 HDD only

This is what I get from command: lsusb
```
Bus 002 Device 003: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 002 Device 002: ID 045e:00dd Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I did what I see to this link: [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G) but still the HD is not mounted. My OCZ 16GB usb flash stick is mounted and working (NTFS partition) but not the HDD, isn't it weird?

---

### Post by karantina7 on 2009-03-03
Thank you everyone for your help, after restarting the computer my HDD mounted and it's operative :D

---

### Post by Michael84 on 2009-03-03
> **karantina7 said:**
> Hello, I am new to ubuntu and I have a problem when I plug my external usb WD passport 120GB. I have searched but I couldn't find any info about the problem or I am a copmlete noob. :) I am using Ubuntu intrepid and it's the only OS on this computer. The hard disk is recognized and completely usable on Win XP but it seems it won't mount on ubuntu. Intrepid can't mount NTFS partition drives or I need to install anything else?

Thanks in advance.
Maybe you should try additionally using this free prog - [disk usage utility]("http://directorysize.moleskinsoft.com/disk-usage-utility.php"). It helps in many cases. I think here as well...

---

