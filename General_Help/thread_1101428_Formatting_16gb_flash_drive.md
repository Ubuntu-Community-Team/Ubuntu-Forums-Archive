---
title: "Formatting 16gb flash drive"
date: 2009-03-20
forum: General Help
---

### Post by Benbow on 2009-03-20
I have a 16gb memory stick on which I have loaded photos to view through my Humax PVR. The PVR tells me that the memory has to be formatted with ext 3 before it will accept it. How do I format this to ext 3?

---

### Post by kpatz on 2009-03-20
1.  Insert the stick into your 'buntu box and then from a terminal type 'mount' to see what device name it has.  For example, you might see:

> 
/dev/sdc on /media/usbdisk type fat32... 

the device would be /dev/sdc in this case.

2.  Back up any data you care about on the stick, since reformatting it as ext3 will erase everything on it.

3.  Unmount the stick:  **sudo umount /dev/sdc** (or whatever /dev name it had)

4.  Format the stick as ext3: **sudo mkfs.ext3 -m 0 /dev/sdc**

5.  Remount the stick (quickest way is to remove/reinsert it and let udev do it)

6.  Copy your photos to it.

7.  Unmount the stick, remove it, and insert it in your PVR.

BTW, once you've formatted it as ext3, you'll only be able to access it from Linux, unless you install an ext3 driver in Windows.

---

### Post by Benbow on 2009-03-20
Thanks for the reply, kpatz. I have formatted as ext3 and re-mounted the usb stick but the pvr still won't accept it nor can I copy any of my photos to it. Sorry for being a bit dense but although I am in my second year with Ubuntu and I fear that I am one of the non-techies. I love the os but the command line still confuses me.

---

### Post by kpatz on 2009-03-20
It seems odd to me that a consumer device would need external flash memory to be formatted to ext3 anyway.  It should be able to read fat/fat32 at least.  Maybe your memory was formatted ntfs and the error message is misleading?  Try formatting it to fat32 and see what happens.  It should read that, unless it's not designed to load photos from a flash drive.

---

