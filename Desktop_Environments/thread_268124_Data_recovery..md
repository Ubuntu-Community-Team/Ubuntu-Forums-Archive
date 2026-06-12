---
title: "Data recovery."
date: 2006-09-29
forum: Desktop Environments
---

### Post by Levdir on 2006-09-29
I, uh, accidentally killed my iPod with gParted. I have two hard drives, and for some reason Kubuntu didn't recognize the second one when I was installing it (even though it's formatted to ext2). Anyway, I was playing around with gParted to see if I could find the second drive and get it running, and it did in fact register a second volume. Unbeknownst to me, this second volume was my iPod. I applied a new drive label to it, <i>then</i> thought to look and see what it actually was. Anyway, I seem to have borked the OS, and I had the entire contents of my personal files from my previous Windows install backed up on the thing. Yeah.

Once you're done laughing at me, does anyone know of a data recovery application I could use to try and get my files back? I had/have all of my music, movies, and my various bits of digital art on that little black box.

Any help would be appreciated.

---

### Post by aysiu on 2006-09-29
You may not be able to get your files back if you installed over them.

I've heard good things about (but don't know how to use) a program called GPart (not to be confused with GParted) that may help.

---

### Post by nthdegree on 2006-09-29
If you formatted with ext2/3 over a FAT/FAT32 filesystem (iPod) there may be little that can be done, since the FAT32 (File Allocation Tables, 32 bit) file system will have lost all the names/locations of all the files meaning to find where all the pieces of files X, Y and Z were would be really difficult for any recovery app.

If it was a FAT32 format on a FAT32 file system there's a very high chance of recovery, i'd try all the freeware Windows recovery tools 1st though.

---

### Post by Levdir on 2006-09-30
Alright, those sound like good places to start. Thanks.

---

