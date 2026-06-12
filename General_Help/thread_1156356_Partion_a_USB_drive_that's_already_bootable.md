---
title: "Partion a USB drive that's already bootable"
date: 2009-05-11
forum: General Help
---

### Post by sir_nasty on 2009-05-11
sorry if the title is a bit unclear but here's what I have.  I installed Jaunty 9.04 onto a usb drive (8gb drive) and made it bootable so I could check it out.  Well I like it and want to try it.  However, I've done a few things with my existing install so I don't want to make the change 100% yet.  I want to backup my current hdd with partimage to my usb drive.

The issue is that it doen't recognize the free space on there.  Gparted says unrecognized/unknown filesystem.... any ideas?

If no ideas on that, any good pages on how to make an img/iso of my existing drive using usb sticks?

---

### Post by sir_nasty on 2009-05-11
for the sake of documentation here's where I'm at for the moment...

I booted off my Jaunty usb/live drive, did a sudo apt-get install partimage, installed partimage, dropped to command prompt and ran sudo partimage, set the save file as /media/USBDRIVE/backup (USBDRIVE is the name of the SECOND usb drive I plugged in) and I was able to image my hdd to the second usb drive (borrowed one from a friend.  However, I want to do it with one usb drive.  So here's what I'm doing.

Formatted the usb drive, partitioned it with gparted into 2 partions, 1.3gb and 6.7 gb, fat32 partions, trying to installed the jaunty image onto the 1.3gb right now, if that works then I'll boot jaunty and see if I can get partimage to save to my second partion.  If so then I have a nice way to image my drive whenever I need to and be able to restore it with a simple command from usb!  Will updated later for futur referance.

---

### Post by sir_nasty on 2009-05-11
It works!  But one key final step needed....  so here's the process.

1.Download Jaunty

2.Partition the drive (I used fat32 for both partitions), 1gb for Jaunty, then whatever else you want

3.Follow instructions for making a jaunty usb boot drive, however, instead of diskN in the instructions use diskNSX, where it specifies the partion you want to use not the whole disk.

4.Once that's done open the drive in gparted, manage flags on that partition and select boot (if you don't do this step and try to boot off it you get just a blinking cursor)

5. boot off the usb drive

6. in terminal, sudo apt-get install partimage

7. check your computer and determine the partion names for each one on your usb drive, typically /media/disk, or /media/disk-1

8. in terminal, sudo partimage

9. in partimage where it asks for the name of the file type in: /media/NAMEOFYOURDISK/YOURFILENAME, go to next(f5), and select the options you want

10.  Took about 20 minutes to do my mini 9 with 4.37gb's used, 1.77gb was the resulting file size

11.  HOW DO I MARK THIS THREAD SOLVED?

---

