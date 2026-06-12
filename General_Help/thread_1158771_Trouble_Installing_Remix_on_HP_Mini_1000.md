---
title: "Trouble Installing Remix on HP Mini 1000"
date: 2009-05-14
forum: General Help
---

### Post by Z051392 on 2009-05-14
I am new to trying to install to Ubuntu. I am having trouble installing Netbook Remix on my Mini 1000 (1035NR XP preloaded/reloaded). I followed the instructions to create a bootable USB flash drive using Win32DiskImager and the 9.04 release, and it is recognized in the boot order, but once I choose to boot from it, I am stuck at a flashing cursor and black screen. Can anyone help?

If it matters, i am using a 4GB Sandisk Micro Cruzer.

Any guidance or information would be appreciated.

---

### Post by HuckleSmothered on 2009-05-15
I've had that same problem. Found that it is only with the GUI app's in making a proper flash installation image. They usually mangle the boot record. I dunno why. 

My suggestion would be to reformat the drive using fdisk. New partition table, new partition (fat16), turn on bootable flag. Then copy over the installation file to the flash drive.

The only way I've been able to make a successful one is through this process:

> Command Line Interface

1. Download the desired Netbook Remix .img file (about 1GB)
2. Open a terminal and insert your flash media
3. Look at the output of dmesg | tail -20 to determine the device node assigned to your flash media (e.g. /dev/sdb, not sdb1)
4. Run sudo umount /dev/device/node
5. Run sudo dd if=/path/to/downloaded.img of=/dev/device/node
6. Remove your flash media when the command completes (you may need to wait a few extra seconds for it to finish)

Try the install again.

---

### Post by Fingers &amp; Thumbs on 2009-05-15
I used flashnul to create my image onto usb flash drive, and it worked flawlessly. Flashnul is a windows command prompt utility.

I advise having all flashnul files and UNR in the same directory in windows, cd to that directory before using,

See [URL="https://wiki.ubuntu.com/UNR#From%20Windows%20Command%20Prompt%20using%20flashnul"]https://wiki.ubuntu.com/UNR#From%20Windows%20Command%20Prompt%20using%20flashnul 
[/URL]

---

