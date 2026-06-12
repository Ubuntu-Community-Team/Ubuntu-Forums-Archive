---
title: "very slow copy if the file/folder size is large"
date: 2009-01-14
forum: General Help
---

### Post by antipergel on 2009-01-14
Hi all,

I have been experiencing a weird problem after I updated my Ubuntu to 8.10:

Copying larger files/folder between partitions or hard drives takes longer than I would expect.

For example,

600 MB folder ~ 25 MB/sec
7.2 GB folder ~ 5.6 MB/sec

Also in same cases, when I do the copy with drag and drop and press cancel button, although the copy GUI disappears, the copying continues.

Thoughts?

---

### Post by pavel989 on 2009-01-14
the system probably tries to finish copying, and then delete, maybe a user problem?

and about the copying, same FS? and whats your ram lookin like?

---

### Post by antipergel on 2009-01-14
> **pavel989 said:**
> the system probably tries to finish copying, and then delete, maybe a user problem?

and about the copying, same FS? and whats your ram lookin like?

Well, I still expect the OS to stop copying when I press the cancel button.

I am copying from ext3 to NTFS.

I have a Lenovo T400, Intel Centrino2 laptop with 4 GB Ram. Have the 64 bit Ubuntu.

Again, the smaller the file, the faster the copy...

---

### Post by pavel989 on 2009-01-14
i expect it to stop too, but who knows. I think this has a lot to do with ext3 to ntfs, but it shouldn matter with 4 GB ram.

Other than that, i can't really help. not a guru. I would look into the FS change tho.

Also, is this on just separate partitions, drives, both?

---

### Post by mwillams73 on 2009-05-29
Im having almost the same problem except it invovles copying files within ubuntu or using the save image as command in the right clik context menu in web pages, what happens is if the destination folder reaches somewhere around 150 mb's it takes almost a whole minute for the "browse to"( i think thats what that window is called) folder window to open and allow me to type whatever the name is of the file, less than 150 mb's its instantaneous! the same thing happens when i want to make a new file to put my images in so that i can copy to the old file . 

What i mean is i create a new folder call blah vol 2 and rename the original blah vol 1 that way i can "save image as" to the vol 2 folder and its fast like its supposed to be but then when i want to copy the files within that folder to the vol 1 folder it takes forever, it doesnt make any sense at all. I guess what im asking is, does ubuntu have some sort of folder size limit that causes this? or what? Im getting tired of having to have 2 folders for any particular images i am working on. 

By the way im on hardy, i have a gig of ram, and a 1.2 gig amd on demand upscaling to 1.7 stable cpu, i never had this problem in windows at all, so i dont understand why ubuntu is doing this. To be clear it doesnt take a long time to download the file, only to manually copy from a small folder to a larger folder( small folder = to 50 mb's /larger folder = to 150+) and also when i try to "browse to" the larger folder(using the save image as command in the right clik context menu) the "browse to" window opens instantly but i have to wait as much as a minute before i can type anything or click save or hit enter. I hope that clarifies things. Any help would be appreciated!!

---

### Post by gradinaruvasile on 2009-08-23
Same problem here... 
Optiplex 755 / Core2Duo E6550 /2.3 GHz / 2 GB 800 MHz RAM 
hdparm -Tt /dev/sda 
gives 3600+ MB/s on the cached reads / 62 MB/s device reads

But when copying files larger than 600MB - 1GB from JFS to JFS or EXT3 to JFS (I tried only with these, maybe a general problem) the throughput slowes down to 6-7 MB/s.

 I remember on a laptop (DELL D630) i copied with 11-19 MB/s from EXT3 to NTFS...

Are there some settings that can be tweaked in order to make it work faster?

---

