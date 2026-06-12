---
title: "Creating recovery media for Latitude E7440"
date: 2014-01-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by scotthosking on 2014-01-07
Hi, I've just got myself a Latitude E7440 pre-installed with windows 7.  I would  like to create a recovery image before I partition the SSD drive to  install Ubuntu along side Win7.


 So far, I have been able to use the Dell Backup and Recovery software  to create a factory recovery image on a USB pen drive.  To create the  recovery image I needed ~10Gb of disk space, and so I put it on a clean  64Gb usb drive. 


 I have a couple of questions regarding this:


 1. Can I compress (contain, zip) this ~10Gb recovery image somehow  (.iso?) so that I can get full use of this 64GB USB drive again?  I  guess simply copy and pasting the files over into a folder will not work  as there will be a boot sector on the USB drive that is needed in order  for the laptop to recognise it upon recovery.


 2. Secondly, although I have Windows 7 pre-installed, the laptop came  with a Windows 8 recovery disc (at least this is what I think it is).   Does this mean I could install Windows 8 instead if I wanted to one  day?  Furthermore, as there is no DVD drive in the laptop, how would I  go about installing Windows 8 from this recovery disc?  If I can install  Windows 8 from this disc then I wouldn't be as nervous about losing the  ~10Gb Windows 7 recovery image that I've placed on my USB drive.   Although, I'd rather be safe than sorry.

---

### Post by varunendra on 2014-01-10
Welcome to the forums scotthosking !

I don't know what exactly the Dell Backup tool does or how it does whatever it does, so can't say what you can or can't do with it. But if it placed the backup on the USB to be used manually later (booting from it and performing the restore automatically or manually after booting), you can do the same thing with Clonezilla.

Clonezilla by default compresses the backup image with Gzip which has a pretty good compression ratio. But if you are too serious about size of the backup, it also gives you the option to compress it using Bzip which probably comes next only to 7zip in compression ratio.

Please read this post for a very quick 'How To' on using Clonezilla to create an auto-restore image : [http://ubuntuforums.org/showthread.php?t=2197659&p=12892466#post12892466](http://ubuntuforums.org/showthread.php?t=2197659&p=12892466#post12892466)
Tutorial on using Clonezilla (first run only, second run to create automated recovery image has not been included in this guide) : [http://www.dedoimedo.com/computers/clonezilla.html](http://www.dedoimedo.com/computers/clonezilla.html)

Feel free to ask questions you may have regarding this.

Answers to your original questions, but in context of clonezilla -

[indent]1. The .zip image clonezilla creates is a simple file. You just have to extract its contents on any USB disk, and run a script (on linux) or a batch file (on windows) to make it bootable. This script is part of the extracted contents. As such, you can keep the .zip file anywhere you like, until it is required to do the restoration.

2. Not sure about the Recovery disc. The only way to make sure, unless someone experienced with it can confirm, would be to take a full disk image of your hard disk, then try the Restore DVD and see what it does. To get back to the original state, restore the image you took before the experiment. Assuming you have no user data on the disk yet, clonezilla or any backup tool should take less than 20 minutes to image the whole drive. And about 10 to 15 minutes to restore it back.
[/indent]

**EDIT:**
Forgot about the "there is no DVD drive in the laptop" part. You can use CD/DVD to USB tools like [YUMI]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/") or [WinToFlash]("http://wintoflash.com/overview/en/") to put the contents of the DVD on a USB and install from it. Although I'm not sure if they can deal with the Recovery disk properly or not if it is too different from the standard Windows installation disc.

---

