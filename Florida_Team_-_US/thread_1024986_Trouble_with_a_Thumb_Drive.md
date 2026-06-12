---
title: "Trouble with a Thumb Drive"
date: 2008-12-29
forum: Florida Team - US
---

### Post by yakove on 2008-12-29
Ok, I am having an issue using the "Create A USB startup disk". here is what I have done
I have a Kingston 2GB DataTraveler.
1. I have successfully installed Ubuntu 8.10 on my system
2. I have Used the "Create a USB startup" utility
3. while using said utility, I used the Install disk to create the image
   and the program says it was successfully done.
4. I also had that program format the drive for me.
5. when rebooting and attempting to go into the USB drive. It leaves me with a command line "Boot:". No matter what I type in this command prompt, It throws back "Can not find Kernel." This happens on both of my computers.
6. I have basically followed this websites instructions to the "T"
[http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/)

It still wont work, what on earth am I doing wrong.

---

### Post by dantrevino on 2008-12-29
> **yakove said:**
> Ok, I am having an issue using the "Create A USB startup disk". here is what I have done
...
It still wont work, what on earth am I doing wrong.

Have you done an md5 hash on the iso you downloaded and compared it to the correct hash?  Did you use the iso or a CD as your "source"?  If you used a CD, does the CD boot up fully?

to find the md5sum:
```
md5sum ubuntu-8.10-desktop-i386.iso
```

of course, substitute the name of the iso you're using..

---

### Post by yakove on 2008-12-29
I used the image on the CD... not the ISO... the Md5sum came back
24ea1163ea6c9f5dae77de8c49ee7c03

I just checked this and it seems to be correct.

The Cd does boot correctly

---

### Post by yakove on 2008-12-29
ok, I also just tried to do it with ISO instead of using the CD... and I got the Same result.

---

### Post by yakove on 2008-12-30
found a possible fix
[http://www.pendrivelinux.com/2008/10/06/error-could-not-find-kernel-image-linux/](http://www.pendrivelinux.com/2008/10/06/error-could-not-find-kernel-image-linux/)

---

### Post by yakove on 2008-12-30
ok my syslinux.cfg looks like this... is this correct? or is something missing?

include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
gfxboot bootlogo

---

### Post by yakove on 2008-12-30
ok, after doing a lot of reading I understand why it is not working...

syslinux.cfg is not pointing to the location of vmlinuz or my initrd.gz on my USB drive at all.

so my next question is... how exactly do I get this file to work properly? maybe someone can show me what their syslinux.cfg on their flash drive looks like.

---

### Post by dantrevino on 2008-12-30
Here's mine.

```
include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
gfxboot bootlogo
```

---

### Post by yakove on 2008-12-31
Does yours works? that looks exactly like whats on mine... hmm I wonder what else could be wrong.

---

### Post by yakove on 2008-12-31
I just used the alternative installation that is shown here

[http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/)

It still is giving me the same error even though the syslinux.cfg seems to be correct. Im starting to think that maybe this particular flash drive might have issues with being used as a bootable device...

---

### Post by dantrevino on 2008-12-31
Mine works like a champ. Maybe, like you suggest, you should try a different stick with the same process.

For me the USB creator that is installed by default has worked out of the box every time.

good luck
dan

---

### Post by yakove on 2009-01-16
I went from using the Kingston datatraveler to a Sandisk USB drive and it worked perfectly. I did a little research about the new kingston datatravelers. The simply are too slow a device for boot... There are many a comment supporting this on the Newegg.com website where you can go to comment on this product.

---

### Post by Marikawn on 2009-04-19
Have you tried using unetbootin?

---

### Post by ezsurfer on 2009-05-16
am using a Kingston, works fine.

What I found after struggling through 2 different USB sticks is some are not "bootable" flagged out of the box.  

There is an HP utility for XP that does it, so I just did it at work.  after that, both my USB sticks work fine.


ezsurfer

---

### Post by itnet7 on 2009-05-17
> **ezsurfer said:**
> am using a Kingston, works fine.

What I found after struggling through 2 different USB sticks is some are not "bootable" flagged out of the box.  

There is an HP utility for XP that does it, so I just did it at work.  after that, both my USB sticks work fine.


ezsurfer

For the benefit of others, mostly here is what you can do to find the device and toggle the bootable flag.

Plug-in the thumb drive, and type: dmesg

```
[205935.776962] sd 15:0:0:0: [sdb] Write Protect is off
[205935.776968] sd 15:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[205935.776973] sd 15:0:0:0: [sdb] Assuming drive cache: write through
[205935.776982]  sdb: sdb1
[205935.780216] sd 15:0:0:0: [sdb] Attached SCSI removable disk
[205935.780360] sd 15:0:0:0: Attached scsi generic sg2 type 0

```

You can tell by the above return that the device is /dev/sdb1.

You can begin fdisk by typing the following:

```
sudo fdisk /dev/sdb
```

It will open fdisk and you will see 

```
Command (m for help):
```

You can hit 'm' to view all of the menu options. 

First lets start off by typing 'p' to print the partition table to the screen.

```
Disk /dev/sdb: 1051 MB, 1051197440 bytes
33 heads, 61 sectors/track, 1019 cylinders
Units = cylinders of 2013 * 512 = 1030656 bytes
Disk identifier: 0x000a5438

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1019     1025593    b  W95 FAT32


```

You will notice that Under the Boot column there is no asterisk present. This means that the bootable flag is not turned on. 

In order to change this: 

The menu reveals that option 'a' is used to toggle the bootable flag.

select 'a', it will ask you for the parition number select the partition number you want to make bootable. In my case I wanted to make the 1st partition bootable so I entered '1'.

Now when you print out the partition table you will see.

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1019     1025593    b  W95 FAT32
```

Then as always in fdisk select 'w' to write the changes. 

Hope this helps someone in the future. 

Chris C.
itnet7

---

### Post by dark_religion on 2009-11-13
Looks correct to me.

---

