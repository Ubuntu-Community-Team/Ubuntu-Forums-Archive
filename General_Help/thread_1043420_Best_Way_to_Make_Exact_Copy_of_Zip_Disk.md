---
title: "Best Way to Make Exact Copy of Zip Disk"
date: 2009-01-18
forum: General Help
---

### Post by DrewT on 2009-01-18
Ubuntu/Linux is a terrific OS but there are so many ways to do everything that we newbies sometimes want to tear our hair out. So here's a real basic newbie question to address a very specific situation -- and hopefully I'll learn a little more from the answers.

I have a bunch of Zip disks that were created on a Mac G3 -- most or all of them on System 9 or earlier, I think. Some of the disks seem to have data that is hidden from Nautilus -- at least the amount of total data reported is greater than the sum of the files I can see.

Before I do anything else, I would like to make bit-for-bit clones of these disks and burn the resulting images onto CD (or DVD) so we can try looking at them on a Mac, with System 9 if necessary. But when I search for help on disk images, I quickly find myself buried in possible alternatives with no idea how to start choosing one.

What's the simplest, most straightforward way to do this in Intrepid? I'd prefer to use the GUI, but I'm happy using the command line as long as I understand exactly what I'm doing (which is rare!).

---

### Post by yoyoned on 2009-01-18
Use the dd command, but use it very carefully.  It can quickly make a good day turn bad.

```
dd if=/dev/sdb of=zipcopy.img
```

---

### Post by DrewT on 2009-01-18
Excellent. Where do I find the right **if** path? The drive is showing up in Nautilus as **/media/[Zip 100]**, where **Zip 100** is the name given to the disk when it was made. Will that path work for my purposes or will it only give me so much of the data as Nautilus "sees"? If I should be using the dev/sd*n* path, where do I make sure I've got the right *n*?

(I know this makes me sound painfully ignorant -- but then, that's just what I am!)

---

### Post by DrewT on 2009-01-18
Okay, I answered my question -- I ran the **mount** command and found my zip drive at /dev/sde4. I then ran the above command (with sudo), and it seemed to work, at least there's now an .img file of 96+ mB. 

So thanks, yoyoned!

A couple of followup questions.

First, I got the following error:

```
:~$ sudo dd if=/dev/sde4 of=Zip_100.img
dd: reading `/dev/sde4': Input/output error
196104+0 records in
196104+0 records out
100405248 bytes (100 MB) copied, 190.69 s, 527 kB/s
```

Is this anything I can or should do anything about?

Second, what can I do with the resulting image file? I'd like to burn it to a CD and look at it on a Mac, but what's the right way to do that?

---

### Post by mssever on 2009-01-18
> **DrewT said:**
> ```
:~$ sudo dd if=/dev/sde4 of=Zip_100.img
dd: reading `/dev/sde4': Input/output error
196104+0 records in
196104+0 records out
100405248 bytes (100 MB) copied, 190.69 s, 527 kB/s
```Is this anything I can or should do anything about?Given that error, I wouldn't trust your copies to be bit-for-bit accurate. However, I don't know how to solve this problem. Trying again might help, though.

> Second, what can I do with the resulting image file? I'd like to burn it to a CD and look at it on a Mac, but what's the right way to do that?
You can't really burn it to CD. I'm quite certain the filesystem is something other than iso9006 (quite likely, it's FAT, but you need to find out for sure). Your best bet is to transfer the file somehow to OSX and loop mount it. I don't know how to loop mount on OSX, but in Linux it's ```
mount -t vfat -o loop image_file /mount/point  # be sure to change vfat as appropriate
``` This probably won't work in system 9.

---

### Post by DrewT on 2009-01-19
The filesystem is hfs. The image file I made as above will open and mount natively in OS X just by double-clicking, but I can't open it at all in System 9, which I reinstalled to test it. When I open it in OS X I don't see anything I can't see in Nautilus. 

I'm starting to feel like I'm on a snipe hunt here. I am going to have to rethink my objectives.

---

