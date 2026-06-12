---
title: "Downgrading from ext4 to ext3"
date: 2009-01-15
forum: General Help
---

### Post by homemadejam on 2009-01-15
Hey,
Is there any way of downgrading from ext4 back to ext3?

Thanks in advice,
Jam

---

### Post by ajcham on 2009-01-15
I believe that would involve a reformat of your disk, so you would have to back up anything you want to keep.

---

### Post by stefangr1 on 2009-01-15
> **homemadejam said:**
> Hey,
Is there any way of downgrading from ext4 back to ext3?

Thanks in advice,
Jam

If I may ask, why do you want to downgrade?

---

### Post by homemadejam on 2009-01-15
Well, I've upgraded to ext4.. but I cannot boot it up.

I have a 2nd partition which I have a 2nd copy of Ubuntu installed onto there...

So I have instaled Grub2, and added my ext4 partiton on there.

I still had no luck in booting it up...
And I read somewhere that I had to add a fwe thigns into the initramfs moudles... ext4, jbd2 & crc16 (I think).

But still no luck.
Someone said that my placing a custom script telling it what to mount and where into scripts/local-bottom would work.. still no luck.

I have also added things like rootfstype=ext4 into the Grub... but nope.

So I have had enough of trying to get it to work.. I just want to be able to use it again.

Thanks,
Jam

---

### Post by homemadejam on 2009-01-15
I can mount my ext4 partition from my other spare partition... is there any way in which I can copy all my files over to my 2nd partition.. format my 1st (back to ext3) and then move all my files back?

Thanks,
Jam

---

### Post by cariboo on 2009-01-15
The answer to your question is yes. I may be an good idea to do this soon, as I am seeing reports of data loss in the Jaunty Testing and Discussion Forum.

Jim

---

### Post by PeterLohmann on 2009-02-22
So can I just tar my / into one big tarfile, delete the ext4 partition, recreate it as ext3 and untar everything back? Will this be ok for all the special and device files on the root partition?

My reason for going back to ext3 is the lack of backup tools for ext4 as I would like to use something like dump or at least partimage.

---

### Post by lvleph on 2009-03-08
This is what I read.
> 
There is also a downgrade path from ext4 to ext3, with a method to con-
vert the extent files back to indirect mapping files. In the case that users
prefer to go back to ext3, they can mount the ext4 file system with the
&#8220;noextents&#8221; mount option, copy the extent-based ext4 files to new files,
rename these over the old extents, use tunefs to clear the
INCOMPAT_EXTENTS flag, and then remount as an ext3 file system.

I don't understand what this means, but I would like to figure it out.

---

### Post by frankstrudel on 2009-07-14
Have you figured it out yet? Or if anyone else there, can they help?

(Sorry to bump an ageing thread)

---

### Post by PeterLohmann on 2009-07-14
What (finally) worked for me is the following:
1. Downsize the ext4 partition.
2. Create a new ext3 partition.
3. Just "cp -a" everything from the old to the new one.

The tricky part was point "1." which was suddenly working after I tried again a few weeks after my first try.

---

### Post by yakshbuntu on 2010-01-30
Hi, 

I posted a blog about how to downgrade from ext4 to ext3 here

[http://duopetalflower.blogspot.com/2010/01/how-to-migrate-ext4-partitions-to-ext3.html](http://duopetalflower.blogspot.com/2010/01/how-to-migrate-ext4-partitions-to-ext3.html)

---

### Post by sergiomb on 2011-07-22
> **yakshbuntu said:**
> Hi, 

I posted a blog about how to downgrade from ext4 to ext3 here

[http://duopetalflower.blogspot.com/2010/01/how-to-migrate-ext4-partitions-to-ext3.html](http://duopetalflower.blogspot.com/2010/01/how-to-migrate-ext4-partitions-to-ext3.html)

man your site is unreadable:(

---

### Post by sergiomb on 2011-07-22
>  Though not as straightforward as ext3 to ext4, there is a path for any user who may want to downgrade from ext4 back to ext3. In this case the user would remount the &#64257;lesystem with thenoextents mount option, copy all &#64257;les to temporary &#64257;les and rename those &#64257;les over the original &#64257;le. After all &#64257;les have been converted back to indirect block mapping format, the INCOMPAT_EXTENTS &#64258;ag must be cleared using tune2fs, and the &#64257;lesystem can be re-mounted as ext3. is more clear?
Seems no solution unless, copy, format and copy back.

---

