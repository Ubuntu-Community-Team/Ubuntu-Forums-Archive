---
title: "Bad superblock"
date: 2006-08-25
forum: Desktop Environments
---

### Post by Flavian on 2006-08-25
I got a serious problem
A few days ago I had to back up some data from a windows hard drive from my relatvies, so I unplugged one of my ext3 harddrives in my Pc and plugged the NTFS Harddrive in, started up the computer and the system said that the partition was not an EXT3... I continued thinking it was nothing...
Now everything is back in order, the hard drive that was in the PC before is back on again and it works, BUT the drive I backed the data up to has problems:
It says that it is NOT an ext2 filesystem OR that the superblock might be corrupt and so the system can't mount the drive.
Linux suggests to use another superblock...

Now I am a little bit of a noob, so what is the superblock? Is it the bootrecord?
The HDD is found in Linux, so it works, it also shows up in BIOS, but it does not WORK under ubuntu anymore and I can NOT enable it too...
Can someone help me rescue the drive.
I don't want to reformat and I have no idea how that could have happened too...

thanks for any help!
Flo

---

### Post by peabody on 2006-08-25
[http://www.angelfire.com/myband/binusoman/Unix.html](http://www.angelfire.com/myband/binusoman/Unix.html)

A good intro to Unix filesystems.

How exactly did you perform the backup?

---

### Post by Flavian on 2006-08-26
I don't actually know if the back up has something to do with the error.
I just want my hard drive to work again!

I simply plugged in the other hard drive and booted up, it recognized the hard drive and I copied the data from one drive to the other, that was it.

---

### Post by peabody on 2006-08-26
> **Flavian said:**
> I don't actually know if the back up has something to do with the error.
I just want my hard drive to work again!

I simply plugged in the other hard drive and booted up, it recognized the hard drive and I copied the data from one drive to the other, that was it.

I'm confused in your first message just what hard drive was running ext3, what hard drive was running ntfs, and what operating system you were in when you performed the backup.

Could you clarify a little more?

---

### Post by Flavian on 2006-08-26
Thanks Pea for your help!
I finally got it to work again. I have no idea what caused the error, but I just love Linux more and more... it's way easier to fix a harddrive than it is in Windows. I had some serious data loss with NTFS hard drives on my windows server, but now with linux, everything just works fabulous!

Here's the way I got it to work again
```

mke2fs -n /dev/hdc1

```
That command put out the super block backups, knowing that I ran this command...
```

e2fsck -b 32768 /dev/hdc1

```
Whereas the number was the "coordinate" of the super block
It detected some errors, I said "yes" three times and that's it...
The HDD is finally back on, and everything seems to be there.
I don't know if anything is missing but it seems to be ok :)

Thanks for your help anyways.
Flo

---

### Post by peabody on 2006-08-26
Glad you got it working.

Sounds like I didn't really help :) but thanks for the thanks.

---

### Post by Hollowman on 2006-09-27
:) :) :) :) Thank you for your post.  My wife borked my /home partition some how, and now its back in a few easy steps. You saved my skin.  All our pics were there and now there back.  

Thanks for the easy solution, gotta love linux


Hollowman

---

### Post by Tylo on 2006-11-14
Is there a command that will work with NTFS file systems?

I see that this only works with ext2 or ext3 file systems.

Thanks,
Tylo

---

### Post by a6jarvi on 2006-11-23
> **Flavian said:**
> 
Here's the way I got it to work again
```

mke2fs -n /dev/hdc1

```
That command put out the super block backups, knowing that I ran this command...
```

e2fsck -b 32768 /dev/hdc1

```


Thank you a million times, you saved my day (and my data)! :-D 

My computer was open on the floor and I accidentally managed to connect the molex to one of the capasitors on the motherboard. Computer shut down, I rebooted and on the boot one of the partitons didn't pass the fsck (fsck.ext3: unable to set superblock flags on /dev/hdb5). I googled some information on backup superblocks but no one seemed to know how to use them.

This did the trick! Thanks! :D

---

### Post by deleonjavier on 2008-05-28
hey flavian, 

I had a question about mke2fs. did that erase or format your drive. I see you got the e2fsck -b 32768 /dev/hdc1 as an output. I'm getting a hard drive error which sounds like something you got.

---

