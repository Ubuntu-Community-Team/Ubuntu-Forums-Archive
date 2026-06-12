---
title: "Unable to mount Camera! FIX!"
date: 2006-09-03
forum: Desktop Environments
---

### Post by gustolove on 2006-09-03
Ok, I've seen LOTS of posts of people who say they are unable to mount their camera when it is plugged in through a USB cable.

Today I found out what the issue is, or at least what I believe it to be.

Ok, so personally I have a Canon camera (powershot a520.)

The newer Canons (as well as other brands) do not have support to be listed as a Mass Storage Device (where you can access the files through nautilus or similar file browser.) 

They list as a camera device where you cannot write to them but only "Import" the photos onto your computer.

when you do the 'mount' command for example with one of these cameras you will not be shown the device as mounted, even if its plugged in and on.

also the 'dmesg' command will show the device but not list its file format

---------------------------

This is an issue with the camera and how it is made to connect to a computer. 

The easiest way to resolve this is to purchase a $10 card reader for your type of card and use that. The reader will list the card as a Mass storage device and give you a nice little icon on your desktop!!!


NOTE: if you want to RECOVER data off of the camera that you accidentally lost(deleted), you will need to get the card listed as a mass storage device. and then use the app "photorec"([http://www.cgsecurity.org/)](http://www.cgsecurity.org/)).

Type this to install photorec and its parent app testdisk:
```
sudo apt-get install testdisk
```

---

