---
title: "[SOLVED] Really Need Help Please.."
date: 2008-12-09
forum: General Help
---

### Post by bobmarley1 on 2008-12-09
Hey,

I hope I can find the help I need here.
I installed linux ubuntu onto my laptop and its been great for ages but I just tried to install vista on it again cuz dont need linux anymore but it said it cant be installed on a FAT32 drive but i dont know how to change my drive back to NTFS in linux to install windows on it again.

Can anyone please help all help would be extremely apreciated.

Thanks.

---

### Post by Therion on 2008-12-09
You'll need to reformat the primary hard drive either as part of the install of Windows Vista or prior to installing.  

I find it hard to believe that formatting and partitioning is not part of the Vista install procedure, but if that's the case you can download and burn a bootable gPartEd CD that you can boot your PC to and use to reformat the drive with NTFS.  Once that is done you'll install Vista as usual.

Download and burn the .iso file you find here for gPartEd: 

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

---

### Post by bobmarley1 on 2008-12-09
Hey.

Thanks for replying I downloaded that and its on my laptop what I do with it now?

I use linux but im not very good with it a mate said it was a cool system and helped me through the basics.

Thank You Again.

---

### Post by cobra741 on 2008-12-09
Hey There. 

Hopefully you downloaded an ISO of gparted. if not jump back to the site and download it from here.

[http://http://gparted.sourceforge.net/livecd.php]("http://http://gparted.sourceforge.net/livecd.php")

Then burn the ISO onto a CD (burning the actual image itself, not just burning the image file onto a disk). if you're using a windows box you can use CDBurnerXP which is a free tool to burn data/audio disks and also burn ISO Images

[http://http://cdburnerxp.se/]("http://http://cdburnerxp.se/")

When you boot from the CD you should have options to reformat your partition (wipe everything) to NTFS. 

If you really need to keep some of the data on the drive you can boot off an ubuntu live CD and whack a USB Stick or hard drive in and copy it across before you try to reformat the drive. 

Hope this helps mate :)

---

### Post by bobmarley1 on 2008-12-09
Hello.

Just wasted a disc trying :P
I downloaded the thing you said un rar'd it and copied it all to disc and put in laptop but nothing happend.
It does come up 'UDF Volume' when I opened 'Computer' when linux loaded.

Did I do it wrong?

Thank You.

---

### Post by mikeize on 2008-12-10
You can't just 'copy the files' to the disc.  You need to select 'burn image to disc'.  In Windows, the aforementioned cdburnerxp works well, and if you still have ubuntu, you should be able to right click on the iso, and write to disc.

---

### Post by bobmarley1 on 2008-12-10
It doesn't come as an iso though when I downloaded it was a RAR file and I extracted and their was a bunch of files (on my windows computer) but no iso file.

---

### Post by spcwingo on 2008-12-10
Ok, let's try again, the direct download link is here:

[http://downloads.sourceforge.net/gparted/gparted-live-0.3.9-13.iso?modtime=1227915767&big_mirror=0]("http://downloads.sourceforge.net/gparted/gparted-live-0.3.9-13.iso?modtime=1227915767&big_mirror=0")

If you have winrar installed on your computer it associates iso files with it.  It's not actually in rar format.  Then use the burner mentioned earlier to burn the image.  Then reboot with the CD in the tray and you should be golden.

---

### Post by bobmarley1 on 2008-12-10
Just wanted to say thanks for everyones help.

Got it sorted now ;]

---

