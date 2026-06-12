---
title: "USB booting Ubuntu Persistent - worked until first update, now hangs."
date: 2009-02-13
forum: General Help
---

### Post by emarkay on 2009-02-13
I got a bootable USB drive in Ubuntu 8.10 and I had everything working, all persistent changes saved. Then I did the standard Update manager and got all 250 updates. THe Linux xxx.xxx.xxx.7 kernel gave an error message, but as there was already a xxx.xxx.xxx.11 kernel, I used Synaptic to delete the ".7" files.

On next reboot, the mouse is "stuck" in center screen,the sound speaker symbol has a slash through tit, and the "electrons" circle endlessly looking for a network connection.

This will be the THIRD (clean out the files, "Make usb" then update)time I have done this, and I am just hoping I can get a persistent Intrepid bootable on my USB drive. I have 4 gigs alloted in hte option to "Make Bootable USB", and it's a FAT32 unit.

FWIW, had to use "u810p" to actually get the device to boot.

Anyone?

---

### Post by C.S.Cameron on 2009-02-13
If you used usb-creator or Unetbootin to make a persistent flash drive you basically get an image of the Live CD with persistence saved in a file named casper-rw.
Doing an update will not change the image.
Also once casper-rw is filled the drive is no longer persistent and usually does not work.
As the formatting is FAT there is a maximum file size of about 2GB.
If you want to be able to update your bootable flash do a normal install to it as if it was a hard disk.

---

### Post by emarkay on 2009-02-14
Thanks!

I origonally thought of just installing as a HD, but the USB is not seen as an option when I try to install Ubuntu via the CD.

Will continue to experiment.

---

### Post by emarkay on 2009-02-14
Got it - use the install from the boot menu, not the live Ubuntu.

EXCELLENT!

(running it now, here!)

MRK

---

