---
title: "nvidia raid recovery"
date: 2009-04-07
forum: General Help
---

### Post by reegmas on 2009-04-07
how can i access a sata drive as raw bytes?

[http://forums.nvidia.com/index.php?showtopic=25535](http://forums.nvidia.com/index.php?showtopic=25535)

---

### Post by fjgaude on 2009-04-07
Not sure what you mean by "raw bytes"? Not as a file with characters?

The Linux program **dmraid** handles BIOS created raid from Ubuntu. You might give it a try.

---

### Post by reegmas on 2009-04-08
i mean the file system is such that i need to search for patterns in order to determine how it is spread out, in other words the file system is ntfs just not readable, I need to mount an unknown file system and search for patterns in hex or binary whatever it takes, I want to write(eventually, im still poking around manually for now) a program to search for the right combination to read what used to be my array.

---

### Post by fjgaude on 2009-04-08
Under Ubuntu you can use **hexer** or **okteta** and even **tweak**, all in the repository.

Here's other hex editors that could be useful:

[http://linuxpoison.blogspot.com/2008/09/hex-editor.html](http://linuxpoison.blogspot.com/2008/09/hex-editor.html)

[http://linux.softpedia.com/get/Utilities/wxHexEditor-43862.shtml](http://linux.softpedia.com/get/Utilities/wxHexEditor-43862.shtml)

Good luck!

---

### Post by reegmas on 2009-04-09
I have already tried bless, I like it but I cant figure out how to open an unmounted drive? also if there were a read only option that would make me feel alot better until I figure out what is where.

eventually I would like to be able to write some sort of program to guess and check how the pieces fit together.....

I dont suppose anyone knows what exactly the nvidia mediashield's migrate operation actually does and how it is supposed to work(in my experience it doesnt)

I also know very little about the ntfs filesystem (wait isnt that redundant), and at one time i created a dynamic disk on a drive or two that may be part of my corrupted array, mo idea what to expect to be left over from that.

Its my understanding that the first 512 bytes on a drive contain the partition information?

And the MFT is a file about what where and attributes of the files supposed to be in the partition? and it has an identical mirror? so I could find it by searching for identical blocks and perhaps figure out from them a pattern to my data?

With a large file system I would assume that the MFT is larger than the default nvidia raid 5 block size of 64k? if so what can i do then? 


Thanks do much, Im feeling more optimistic already

---

### Post by reegmas on 2009-04-09
is using dd to copy small chunks of the block device to a *.image file then using either a hex editor or cat to decipher it manually really my best option?

I tried this with a usb flash drive this afternoon and saw what the first bytes should look like of that but what should i look for to determine raid configuration?

---

### Post by reegmas on 2009-04-10
I tried to copy a little of the each drive using:
 
   sudo dd if=/dev/sdb of=/home/myuser/raid_recovery_project/a/test.image bs=65536 count=100

(i attached labels to them a-f to keep track of what drive is which)
now two of the six drives spin up then click rather softly then spin down, so now i have hardware failure as well as data corruption.

of the 4 that did work the hex on two of them looked to be identical and then a third one was different but the fourth one began with 64k of all zeros(followed by data), does that mean anything and if so what could it mean?

---

### Post by reegmas on 2009-04-11
how can i compare files to find patterns?
say i took a ms dll file i knew would most likely have been on my array when it was still readable and i split it into the default block size for nvidia raid 5 (64k) and wanted to search for those pieces on the drives, how could i do that?

currently i am limited to my laptop (1.1ghz PIII with usb 1.1) and a single usb sata enclosure to read my raid disks with and an ide external drive with about 50 gigs free so with my laptop hdd and that i have around 60 gigs i can use.

I have a 1TB drive but i dropped it(it was off and in an enclosure) and its been sick ever since so im keeping it off till i can buy another one to copy what i can onto it.

i want to take a dll file and split it into 64k chunks and put them all in a folder then search a block device for any matches how can i do that? and how long could that take?

does anyone know anything about nvidia raid?

---

### Post by reegmas on 2009-04-14
bump?

---

### Post by vivichrist on 2009-04-28
my stripped nvidia raid has 128k stripes. I have a similar problem. ckdsk.exe let loose on my raid set with ntfs partition.

---

### Post by vivichrist on 2009-04-28
have you used Scalpel before? is data recovery and computer forensics tool.

---

