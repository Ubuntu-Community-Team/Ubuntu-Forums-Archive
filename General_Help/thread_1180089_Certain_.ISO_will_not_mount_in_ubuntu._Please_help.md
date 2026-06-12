---
title: "Certain .ISO will not mount in ubuntu. Please help"
date: 2009-06-06
forum: General Help
---

### Post by Poyntz on 2009-06-06
Hi,

I've had excruciating difficulty trying to mount a .ISO file which will not be mounted.

**So far I have:**
1. Ascertained its type. It's a data image (ie, taken from **file <name>.ISO**
2. Established that it will not be mounted to several basic file systems including loop, ext3, ext2, vfat, iso9660, cramfs and ufs. 
- I've also tried the above, mounting to /media/cdrom (reason explained below)
3. Used the command **dd if=/path/blah.iso of=/dev/<my usb harddrive>** to attempt to extract the image onto the usb harddrive
[B]
Results:[/B]
1. > WCIII.iso: data
2. 
- *sudo mount -o loop -t <file system> returns:*
> mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
- *if I exclude the -t <file system>*
> mount: you must specify the filesystem type
3. 
- Under xterm, **ls** returns lines of messed up rubbish language, possibly machine code?
--Under gnome the USB harddrive content shows a few folders and lots of files with names that are unreadable


**My hypotheses:**
- The .ISO was written under Windows, so requires Windows to be opened
- The .ISO was opened on windows via daemon tools, thus in order to open it ubuntu or mount has to some how simulate an active cdrom 

Also,
```
dmesg | tail
``` and 
```
dmesg | tail -n 100
```
didn't give me any valuable information

Please help me if you can.

---

