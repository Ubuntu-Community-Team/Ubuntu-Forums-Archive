---
title: "Boot CD for BIOS Flash Problems"
date: 2009-05-07
forum: General Help
---

### Post by Silvr2008 on 2009-05-07
I am trying to create a boot cd so that I can flash my BIOS. I followed the directions here: 

[http://ubuntuforums.org/showthread.php?t=190615&highlight=flash+bios](http://ubuntuforums.org/showthread.php?t=190615&highlight=flash+bios) 

but when I try to copy the .exe and the .bin it says that there is no room. Also, the bootdisk that it references did not boot when I burned it without adding anything. 

So I found this: 

[http://wiki.osdev.org/Loopback_Device#Floppy_Disk_Images_With_FAT16](http://wiki.osdev.org/Loopback_Device#Floppy_Disk_Images_With_FAT16)
 
I copied all the stuff to loop0 from the bootdisk I downloaded along with my .bin and .exe but when I try to make the iso with: mkisofs -o BootDisk.iso -b bootdisk.img bootdisk.img it says: I: -input-charset not specified, using utf-8 (detected in locale settings)Size of boot image is 1008000 sectors -> genisoimage: Error - boot image 'BootDisk.img' has not an allowable size. It creates an iso but none of the stuff I copied is there. 

Does anyone know what the easiest way to make a DOS boot CD is?

---

### Post by Silvr2008 on 2009-05-07
I ended up just using a bigger floppy image that I got here:

[http://www.linuxinsight.com/files/FDOEM.144.gz](http://www.linuxinsight.com/files/FDOEM.144.gz)

I would still like to know how to do this though.

---

