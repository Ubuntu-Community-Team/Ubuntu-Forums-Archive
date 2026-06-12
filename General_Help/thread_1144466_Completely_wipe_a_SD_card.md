---
title: "Completely wipe a SD card"
date: 2009-04-30
forum: General Help
---

### Post by theozzlives on 2009-04-30
I've got a phone that for some reason don't like the way Linux writes files. I wrote some files to my micro SD card and my phone kept rebootin, then I used gparted to delete the partition so I could put it in the phone and format it.

I used windows to copy the files, but the damage was done. I need to wipe everything and start over. Please help.

---

### Post by GreenBowlPacker_3 on 2009-04-30
What types of files are you trying to put on the card, and what type of phone is it?

---

### Post by theozzlives on 2009-04-30
MP3 and Samsung Delve

---

### Post by BGFG on 2009-04-30
use gparted to format the card to fat16. Most portable devices seem to default to fat16/32. ubuntu writes to these filesystems fine.

---

### Post by theozzlives on 2009-05-01
> **BGFG said:**
> use gparted to format the card to fat16. Most portable devices seem to default to fat16/32. ubuntu writes to these filesystems fine.

I got it FAT32 (FAT16 won't work on 8 GB). It's a Kingston micro SD card if that helps.

---

### Post by WatchingThePain on 2009-05-01
Hi,

I had to format my phone memory card once when it was getting unlocked and FAT32 works fine for me.

---

### Post by theozzlives on 2009-05-01
I just want to do what is the equivalent of a low level format on it.

---

### Post by ajaysutton on 2009-05-01
If you just want to wipe the card, gparted is the best way to do that.

---

### Post by theozzlives on 2009-05-01
I've used gparted, it didn't start acting up until I wrote to it with Linux. Maybe partition Magic for Windows? Don't get me wrong, I LOVE Ubuntu... I just don't think my phone does.

---

### Post by blackgr on 2009-05-01
```
dd if=/dev/zero of=/dev/sdX1 
```
where sdX1 is your sd device. It will zero out you sd card so you can start over

---

### Post by WatchingThePain on 2009-05-01
Yes use the dd command. To fill with zero's is the best thing to a low level format you will get.

---

### Post by theozzlives on 2009-05-01
> **WatchingThePain said:**
> Yes use the dd command. To fill with zero's is the best thing to a low level format you will get.

well that didn't work, I guess I gotta find a Samsung Forum.

---

### Post by GreenBowlPacker_3 on 2009-05-01
I use a PSP wth HomeBrew and I've had similar problems with my Memory Stick Pro Duo in Ubuntu.  Now I just stick to windows when writing files to a portable device.  If you use Windows XP, insert your card in the reader, go to Start > Run > diskmgmt, from there you should at least see the memory card even if it isn't partioned.  You can re-enable it and format it from there.

---

### Post by anjilslaire on 2009-05-01
> **GreenBowlPacker_3 said:**
> I use a PSP wth HomeBrew and I've had similar problems with my Memory Stick Pro Duo in Ubuntu.  Now I just stick to windows when writing files to a portable device.  If you use Windows XP, insert your card in the reader, go to Start > Run > diskmgmt, from there you should at least see the memory card even if it isn't partioned.  You can re-enable it and format it from there.

The trick with the PSP on Ubuntu is to properly unmount/eject it after writing and disconnecting it from the PSP. I write to mine all the time. Do it as follows:
1. Plug in the PSP, set to USB mode, get the connection set.
2. write data to the Pro Duo via Ubuntu.
3. Right-click the PSP drive and select "Eject" (this is done on my Xubuntu 8.10 desktop right now. Gnome may have a slightly different menu system, but you get the point)
4. A pop-up usually occurs that this may take some time, still writing to th drive. Wait for it to complete, and the PSP drive to disappear from your desktop.
5. On your PSP, press O to stop USB Mode.

Your files should be written correctly. I do this very frequently, and always had problems until I started unmounting in Ubuntu before disconnecting.

---

### Post by GreenBowlPacker_3 on 2009-05-02
I'll try that, thanks.

---

### Post by theozzlives on 2009-05-02
Why did my Thread become a PsP Thread? Don't people know how to start their own?

---

### Post by sgosnell on 2009-05-02
It doesn't matter if it's a PSP or a phone, the principle is the same - dismount/eject the drive before removing it from the computer.

---

### Post by anjilslaire on 2009-05-03
Yes, apologies for the apparent sidebar.

You mention dd didn't work. Can you elaborate? Did the zeroing not complete, or did the card still not read in your phone after writing files in Ubuntu?

What is the current status of the card/phone?

---

### Post by theozzlives on 2009-05-03
> **anjilslaire said:**
> Yes, apologies for the apparent sidebar.

You mention dd didn't work. Can you elaborate? Did the zeroing not complete, or did the card still not read in your phone after writing files in Ubuntu?

What is the current status of the card/phone?

I used DD, used the phone to format it, and copied the files using Windows. How do I verify that my files aren't corrupt? They work in other phones.

---

### Post by theozzlives on 2009-05-03
I take off PsycoMan.mp3 and put on Angel.mp3 and the phone acts up, switch it back and it's fine. That leads me to believe there's an integrity issue with some of my files, I need a Linux program to test my mp3s and move the bad ones to a temp directory. Anyone know of such a critter? Maybe ffmpeg?

---

### Post by alex_sv on 2009-05-03
Btw, I've got a similar problem with my SD card from my old Cannon digital camera. I put it to my upgraded Ubuntu as I did 1000 times earlier on Ubuntu 8.04, but after copying data and inserting it back to the camera, SD card became locked and camera refuses to either read or write data on it.
When I inserted it to my Ubuntu laptop again, SD becomes completely unusable, I mean even hand-written mount/fdisk/dd commands are not helping at all, they gave just I/O error.

Ubuntu does recognise the block device, but it can't neither mount vfat filesystem nor write zeroes at the lowest level possible (I mean dd command). That is why gparted don't even see the SD device.

I found that linux maps my broken SD card to /dev/mmcblk0 - (i.e. inserted SD qualified as a plain block I/O device?).
The results of mount command are too frustrating to be listed here.

dd gives I/O error, corresponding kernel log records are as follows:

```

[ 2771.978949] mmc0: new SD card at address b368
[ 2771.980030] mmcblk0: mmc0:b368 SMI-S 512 KiB 

-- dd started here
[ 2771.980179]  mmcblk0:<3>mmcblk0: error -110 transferring data
[ 2772.239254] end_request: I/O error, dev mmcblk0, sector 0
[ 2772.239254] __ratelimit: 15 callbacks suppressed
[ 2772.239254] Buffer I/O error on device mmcblk0, logical block 0
[ 2772.503248] mmcblk0: error -110 transferring data
[ 2772.503263] end_request: I/O error, dev mmcblk0, sector 0
[ 2772.503277] Buffer I/O error on device mmcblk0, logical block 0
[ 2772.762632] mmcblk0: error -110 transferring data
[ 2772.762647] end_request: I/O error, dev mmcblk0, sector 0
[ 2772.762660] Buffer I/O error on device mmcblk0, logical block 0
[ 2773.021315] mmcblk0: error -110 transferring data
[ 2773.021330] end_request: I/O error, dev mmcblk0, sector 0
[ 2773.021344] Buffer I/O error on device mmcblk0, logical block 0
[ 2773.280513] mmcblk0: error -110 transferring data
[ 2773.280527] end_request: I/O error, dev mmcblk0, sector 0
[ 2773.280541] Buffer I/O error on device mmcblk0, logical block 0
[ 2773.280580] ldm_validate_partition_table(): Disk read failed.
[ 2773.539713] mmcblk0: error -110 transferring data
[ 2773.539724] end_request: I/O error, dev mmcblk0, sector 0
[ 2773.539736] Buffer I/O error on device mmcblk0, logical block 0
[ 2773.798869] mmcblk0: error -110 transferring data
[ 2773.798881] end_request: I/O error, dev mmcblk0, sector 0
[ 2773.798894] Buffer I/O error on device mmcblk0, logical block 0
[ 2774.058162] mmcblk0: error -110 transferring data
[ 2774.058175] end_request: I/O error, dev mmcblk0, sector 0
[ 2774.058189] Buffer I/O error on device mmcblk0, logical block 0
[ 2774.317327] mmcblk0: error -110 transferring data
[ 2774.317340] end_request: I/O error, dev mmcblk0, sector 0
[ 2774.317354] Buffer I/O error on device mmcblk0, logical block 0
[ 2774.317399] Dev mmcblk0: unable to read RDB block 0
[ 2774.576523] mmcblk0: error -110 transferring data
[ 2774.576537] end_request: I/O error, dev mmcblk0, sector 0
[ 2774.576550] Buffer I/O error on device mmcblk0, logical block 0
[ 2774.835701] mmcblk0: error -110 transferring data
[ 2774.835714] end_request: I/O error, dev mmcblk0, sector 0
[ 2775.094878] mmcblk0: error -110 transferring data
[ 2775.094892] end_request: I/O error, dev mmcblk0, sector 24
[ 2775.354046] mmcblk0: error -110 transferring data
[ 2775.354058] end_request: I/O error, dev mmcblk0, sector 24
[ 2775.620075] mmcblk0: error -110 transferring data
[ 2775.620089] end_request: I/O error, dev mmcblk0, sector 0
[ 2775.881369] mmcblk0: error -110 transferring data
[ 2775.881383] end_request: I/O error, dev mmcblk0, sector 0
[ 2775.881800]  unable to read partition table
[ 2776.159664] mmcblk0: error -110 transferring data
[ 2776.159679] end_request: I/O error, dev mmcblk0, sector 0
[ 2776.159710] end_request: I/O error, dev mmcblk0, sector 8
[ 2776.159718] end_request: I/O error, dev mmcblk0, sector 16
[ 2776.159727] end_request: I/O error, dev mmcblk0, sector 24
[ 2776.420935] mmcblk0: error -110 transferring data
[ 2776.420950] end_request: I/O error, dev mmcblk0, sector 0
[ 2776.694258] mmcblk0: error -110 transferring data
[ 2776.694272] end_request: I/O error, dev mmcblk0, sector 0
[ 2776.694306] end_request: I/O error, dev mmcblk0, sector 8
[ 2776.694314] end_request: I/O error, dev mmcblk0, sector 16
[ 2776.694322] end_request: I/O error, dev mmcblk0, sector 24
[ 2776.953576] mmcblk0: error -110 transferring data
[ 2776.953588] end_request: I/O error, dev mmcblk0, sector 0
[ 2834.546457] mmcblk0: error -110 transferring data
[ 2834.546468] end_request: I/O error, dev mmcblk0, sector 0
[ 2834.830647] mmcblk0: error -110 transferring data
[ 2834.830662] end_request: I/O error, dev mmcblk0, sector 0
[ 2834.830675] __ratelimit: 15 callbacks suppressed
[ 2834.830683] Buffer I/O error on device mmcblk0, logical block 0
[ 2834.830706] end_request: I/O error, dev mmcblk0, sector 8
[ 2834.830712] Buffer I/O error on device mmcblk0, logical block 1
[ 2834.830719] end_request: I/O error, dev mmcblk0, sector 16
[ 2834.830724] Buffer I/O error on device mmcblk0, logical block 2
[ 2834.830731] end_request: I/O error, dev mmcblk0, sector 24
[ 2834.830737] Buffer I/O error on device mmcblk0, logical block 3
[ 2835.089857] mmcblk0: error -110 transferring data
[ 2835.089869] end_request: I/O error, dev mmcblk0, sector 0
[ 2835.089881] Buffer I/O error on device mmcblk0, logical block 0

```

Looks like I have to buy another SD :)

---

### Post by theozzlives on 2009-05-03
> **alex_sv said:**
> Btw, I've got a similar problem with my SD card from my old Cannon digital camera. I put it to my upgraded Ubuntu as I did 1000 times earlier on Ubuntu 8.04, but after copying data and inserting it back to the camera, SD card became locked and camera refuses to either read or write data on it.
When I inserted it to my Ubuntu laptop again, SD becomes completely unusable, I mean even hand-written mount/fdisk/dd commands are not helping at all, they gave just I/O error.

Ubuntu does recognise the block device, but it can't neither mount vfat filesystem nor write zeroes at the lowest level possible (I mean dd command). That is why gparted don't even see the SD device.

I found that linux maps my broken SD card to /dev/mmcblk0 - (i.e. inserted SD qualified as a plain block I/O device?).
The results of mount command are too frustrating to be listed here.



That's not my problem, I've replaced the card and I have a 1 GB... same problem. I can store as many pics as I want, it's the integrety of the mp3s. I don't want to test over 18 hours of music file by file. That's why I asked for a program.

---

### Post by sgosnell on 2009-05-04
Alex, are you using a Nokia N8*0?  I've only seen /dev/mmcblk0 used under Maemo OS2008.  I've never seen that on any other computer, but of course I've never used every computer ever made.

I don't know of an app that will test mp3 files.  One may be available, but I've never heard of one.  Perhaps Google with carefully considered search terms...

---

### Post by speculatrix on 2012-12-27
don't zero out an SSD or SD card, because that marks blocks as in use.

fill with all ones, e.g. like this:

tr '\000' '\377' < /dev/zero > /dev/sdc


filling with ones is same as being erased to the controller so it knows the blocks are unused.

---

