---
title: "USB creator doesn't recognise USB-drive"
date: 2009-03-23
forum: General Help
---

### Post by Screwdriver0815 on 2009-03-23
Hello,

today I wanted to create a bootable USB-stick for a colleague of me. So I took his USB-drive, formated it to FAT32, set the »boot« flag after formatting... and started the USB creator which is integrated in Intrepid Ibex. 

But the USB creator does not recognise the USB-stick. So after some trying, swearing around and so ;) on I tried another USB-stick (not formatted, FAT16 filesystem) which was lying around. This one was recognised.

So I figured out what the differences are, between the two drives. The only difference between the two drives (except from the filesystem) is: the »FAT32« one is mounted in /media/Disk and the old »FAT16« one is mounted in /media/USBDrive.
So I tried to change the mountpoint of the »FAT32«-one with rightclick on the Desktop icon --> properties --> settings and there I filled in the mountpoint /media/USBDrive. The result was that the USB stick can not be mounted again because there is a "/" in the path to the mountpoint... thats what the failuremessage says...

So I would like to ask you experts if you ever had such issues, if the reason for usb-creator not recognising the drive is the wrong mountpoint and how I can get this installation done anyway on the USB-stick of my colleague?

Thank you very much in advance

cheers 
Steffen

---

### Post by Rallg on 2009-03-23
There are various possibilities. If you have access to a Windows sytem (probably Mac OS would work, too), then try this: Insert the problem USB drive, format it there, and change its drive name. This last step is very important. For example, if is was originally JOHNUSB change it to MARYUSB or whatever.

Then see what Ubuntu does.

---

### Post by Screwdriver0815 on 2009-03-23
thanks for your answer. 

it still doesn't work. I have formatted the USB drive and renamed it on a Win XP machine. 

But the usb-creator still doesn't see the drive. 

I have renamed the problem-drive exactly the same way as the other one in Windows ("USBDrive") but Ubuntu sees it as "USBDRIVE" - with capital letters in the whole word.

So maybe because the mountpoint is still different, the usb creator doesn't see the drive?

any other ideas?

Thanks a lot

---

### Post by Rallg on 2009-03-24
OK, here's the next try, more likely to work. In Terminal:

gksudo gedit /etc/fstab

After it gets your password, a text file will open. Look in the file for any line that mentions mounting /dev/sdb to /media/cdrom (your details may differ, but that's the most likely scenario). If you see such a line, comment it out by putting a has # in front. Then save the file, and reboot.

The problem you mentioned is often caused if the system was loaded to hard drive from a USB installer. The installer may think that it is the CDROM. I am informed that the issue is fixed for new build of 8.10, but not retroactively for existing installations (even if updated).

---

### Post by Screwdriver0815 on 2009-03-24
hmm... now something confusing happened

today I told my colleague that his usb-stick doesn't work and he gave me another one. 
Before I follow your advise, I wanted to test if this one works without changing the fstab-file.

It is also mounted in /media/disk on my computer but it is recognised by the usb-creator. :confused: and the creation of the startup disk is done.

So it has nothing to do with the mountpoint, does it? 

anyway, it worked now. But maybe I get the other usb-drive again to figure out if it works after changing the fstab or if the drive has a failure or whatever.

By the way: the system on my computer is installed via Cd from a new .iso (downloaded last weekend). So is the issue you mentioned still in there?

Thank you very much for your help

cheers
Steffen

---

### Post by Rallg on 2009-03-24
I don't know if the issue is in "new" ISO files or not, since it is my understanding that you would normally download a standard distribution (old) ISO, rather than a nightly build.

If the mount problem appears with your original USB but not a new one, it may have something to do with the device being recognized by UUID. There's something that can be done about that, but check /etc/fstab first, for a permanent solution (if applicable).

---

### Post by Screwdriver0815 on 2009-03-25
okay, I got the usb-drive back to test and try to find a way to get it working.

and I have tried the fstab-thing... doesn't work either.

do you have any other ideas?

---

