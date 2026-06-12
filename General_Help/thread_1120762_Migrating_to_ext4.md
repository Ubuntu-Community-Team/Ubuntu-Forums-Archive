---
title: "Migrating to ext4"
date: 2009-04-09
forum: General Help
---

### Post by djbushido on 2009-04-09
I was wondering how to go about migrating my current ext3 partition to ext4. I was thinking of doing a backup, reformatting to ext4, and then placing files back in. I didn't know however:
1. If PING could do the backup and restore, I have used this in the past and like it
2. If not 1, then a good backup manager available from an outside distribution (ex. doing the backup with Fedora 10)
3. If I can avoid the backup and doing something special to turn it into an ext4 partition.

Any help would be greatly appreciated.

---

### Post by N_Nick on 2009-04-09
That is a good question, i'm interested in testing the new ext4 filesystem but i dont want to do a fresh installation. 

Maybe a /home migration would work but i'm not sure about a complete backup.

Maybe some of the beta testers can help us on this

---

### Post by djbushido on 2009-04-09
Found this: [http://ext4.wiki.kernel.org/index.php/Ext4_Howto]("http://ext4.wiki.kernel.org/index.php/Ext4_Howto").
Might work, although there is a note that existing files won't use extents.
So backup might be the best option.
Any ideas on how to backup a partition in Fedora (PING kernel doesn't support ext4)?

---

### Post by Gaweph on 2009-04-09
I was thinking of moving my /home partition to ext3 also, i am first going to install those packagesd in that aritcle which allow ubuntu to read ext4, then try making a new partition first, if it mounts then youcould create a new /home partition and move your stuff over to it.

I think however it is a bit premature at present to install ubuntu on ext4.

Perhaps wait until 9.04 is out, which might allow you to select ext4 when installing.

Gaw

---

### Post by djbushido on 2009-04-09
Definitely DO NOT do it until 9.04 (no kernel support until then). Unless you build your own kernels.
My question is how to do this without destroying the ext3 partition (don't want to do full re-install).
An idea may be to resize ext3 down, install to new ext4, then copy in ext3 data, and finally resize ext4 to fill rest of space previously held by ext3. HOWEVER, I personally do not recommend doing this just yet.

---

### Post by N_Nick on 2009-04-09
> **djbushido said:**
> Definitely DO NOT do it until 9.04 (no kernel support until then). Unless you build your own kernels.
My question is how to do this without destroying the ext3 partition (don't want to do full re-install).
An idea may be to resize ext3 down, install to new ext4, then copy in ext3 data, and finally resize ext4 to fill rest of space previously held by ext3. HOWEVER, I personally do not recommend doing this just yet.

[http://blog.fusi0n.org/linux/converting-ext3-partitions-to-ext4-on-ubuntu-904-jaunty](http://blog.fusi0n.org/linux/converting-ext3-partitions-to-ext4-on-ubuntu-904-jaunty) 

It looks like its possible to just "upgrade" to ext4 if i am right. Of course backing up your data is a must.

---

### Post by sdennie on 2009-04-09
For a long time I was running ext4 on all my partitions (except /boot) in Hardy.  The way I did was to get [sysrescd]("http://www.sysresccd.org/Main_Page"), boot into that, then repartitioning and using tar to move data.  It was a long and scary process but, no data was lost and in the end I was using full ext4.  It's probably also going to be a pain to boot if you make the root partition ext4 unless you are using 9.04.

Edit:
I forgot to mention: "DON'T DO IT!"

---

### Post by djbushido on 2009-04-09
Hehe, like your sig.
Anyway, I think what I will do is upgrade to 9.04 (when it comes out) copy data to my Fedora partition (command anyone? preferably copy over all files into a .tar.bz2 or just .bz2 or even .gz?) then reformat as ext4, copy data back over (this enables extents) then do the same for Fedora.
Think that will work?
NOTE: For this to work, the new Grub has to be installed. Will update-manager take care of that?

---

### Post by sdennie on 2009-04-09
That will work just fine.  The key to converting ext3 to ext4 is having a place to put the data you want converted.  It sounds like you have that covered.

---

### Post by djbushido on 2009-04-09
So then how would one copy over the data? I have a nice 100GB+ Fedora partition (for 30GB of Ubuntu - probably 35 after 9.04) but I have no idea how to get the data over to it.

---

### Post by sdennie on 2009-04-09
That's the easy part:

```

tar cf data.tar data

```

Make your ext4 partition and then while on it:

```

tar xf ../place_you_put_the_tarball/data.tar

```

That's literally it.  

Unless you are using 9.04, you are going to have a ton of problems doing this though.  Most are fixable but, it's going to be a pain.

---

### Post by djbushido on 2009-04-09
Waiting until 9.04, just wanted to get the command for it.
Also, assuming "data" should be replaced with something like "/media/Ubuntu/*"? Not including the filename.
EDIT:Also, will doing this as "su" in Fedora mess up file permissions? is there an option to preserve file permissions?

---

### Post by sdennie on 2009-04-09
No, in reality, when I said, "data", I meant ".".  It's easiest to be in the directory you are trying to tar.  It makes the untar much easier.  ;)

---

### Post by whoop on 2009-04-09
I have upgraded my intrepid (running ext3) to jaunty a while ago (when it was still in alpha6 stage). I have also converted my existing ext3 file system to ext4, leaving all my data on the partition. I just ran into one problem which was quite easy to solve.

Here's what I did:

Booted jaunty live-cd on a system running jaunty and ext3 (on /dev/sda1 in my case), opened a terminal:

```

sudo bash
tune2fs -O extents,uninit_bg,dir_index /dev/sda1
e2fsck -pf /dev/sda1
mount -t ext4 /dev/sda1 /mnt
nano /mnt/etc/fstab

```

In fstab I changed "ext3" to "ext4" for the partition I converted (and saved the changes).

I later got into some trouble because the distribution upgrade does not seem to install the new grub stage. So I did the following to refresh grub (again from a live-cd):

```

sudo bash
mount /dev/sda1 /mnt
grub-install /dev/sda --root-directory=/mnt --recheck

```

You can probably do both things in one session.

It's been running sweet ever since. 
I know that this method will leave all "old" data (data that was present before the file system conversion) practically untouched (still written to disk using ext3 technology) but this is not a problem because ext3 and ext4 are compatible with each other and update-manager practically updated all my packages since the file system conversion, so just about everything is written in ext4 right now. 

I guess when e4defrag becomes available I could be able to update the few ext3 files I have left on my partition, although this isn't really an issue.

---

### Post by whoop on 2009-04-09
> **sdennie said:**
> That's the easy part:

```

tar cf data.tar data

```

Make your ext4 partition and then while on it:

```

tar xf ../place_you_put_the_tarball/data.tar

```

That's literally it.  

Unless you are using 9.04, you are going to have a ton of problems doing this though.  Most are fixable but, it's going to be a pain.

Isn't it useful to use the p flag as well, just to be sure that permissions don't get messed up?

---

### Post by PreviousN on 2009-04-09
From what I understand, ext4 still has some bugs in it, some of which cause serious issues like data loss. Just do a google search for "ext4 data loss." There's even a bug in launchpad. [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781)

So, really now, even though you'll see a SLIGHT performance gain, (like maybe 1 second at boot?) I would argue that its not worth it. I for one won't be a beta tester for a FILESYSTEM, especially one that has problems with data loss at the moment. 

So, like sdennie mentioned: DON'T DO IT. Unless you have absolutly WORTHLESS data and time on your hands for potential recovery, its not worth it. Even if you back up your data, you'll still have the possibility of losing data after the upgrade. 

Wait a few months and I'm sure everything will work flawlessly. 

All this said, it is possible to do, so if you think you'll see a big enough difference and performance gain, by all means give it a shot.

---

### Post by djbushido on 2009-04-09
No, I'm waiting for 9.04 to come out. I think that what i will do is have update-manager upgrade, which fixes grub.
Then, copy off data using the command:
"tar cfp /home/brad/xubuntu.tar ." when in the xubuntu partition.
Then, reformat as ext4 (probably using gparted).
Reset the UUID - "tune2fs -U <some-uuid> /dev/XXX"
Mount as ext4 - "mount -t ext4 /dev/XXX /media/xubuntu"
Copy data back on using "tar xfp ../home/brad/xubuntu.tar" which will untar the file onto the partition, right? 
Update fstab to reflect ext4 with nano. Just change ext3 to ext4, right?
Um... I think that's it, reformatting as ext4 should enable extents, and such right?

---

### Post by whoop on 2009-04-09
> **djbushido said:**
> No, I'm waiting for 9.04 to come out. I think that what i will do is have update-manager upgrade, which fixes grub.
Then, copy off data using the command:
"tar cfp /home/brad/xubuntu.tar ." when in the xubuntu partition.
Then, reformat as ext4 (probably using gparted).
Reset the UUID - "tune2fs -U <some-uuid> /dev/XXX"
Mount as ext4 - "mount -t ext4 /dev/XXX /media/xubuntu"
Copy data back on using "tar xfp ../home/brad/xubuntu.tar" which will untar the file onto the partition, right? 
Update fstab to reflect ext4 with nano. Just change ext3 to ext4, right?
Um... I think that's it, reformatting as ext4 should enable extents, and such right?

There is one small caveat that I see, I could be wrong. If you upgrade from intrepid to jaunty it will update grub but it will not install the new grub stage. I got a fatal error 13 and others have reported getting error 24 while booting jaunty (after upgrading it from intrepid and converting the file system to ext4).
So I think that you could run into problems with your method.
Running this from a livecd would fix it though:
```

sudo bash
mount /dev/sda1 /mnt
grub-install /dev/sda --root-directory=/mnt --recheck

```

This problem is very badly (if at all) documented and not considered as a bug. It is somewhat mentioned in the ubuntu 9.04 technical overview: [http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)

> 
... then you must also use the grub-install command after upgrading to Ubuntu 9.04 ...


---

### Post by djbushido on 2009-04-09
Ok, so if I understand the command, the partition to be modified "mount /dev/sdx /mnt" mounts the drive at mount, then grub installs to /dev/sda while it is mounted at /mnt. Would this cause a problem because the block device is already mounted?

EDIT: But to confirm, my above method plus your grub-install from alt-cd will upgrade to ext4, right?

---

### Post by whoop on 2009-04-09
> **PreviousN said:**
> From what I understand, ext4 still has some bugs in it, some of which cause serious issues like data loss. Just do a google search for "ext4 data loss." There's even a bug in launchpad. [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781)

So, really now, even though you'll see a SLIGHT performance gain, (like maybe 1 second at boot?) I would argue that its not worth it. I for one won't be a beta tester for a FILESYSTEM, especially one that has problems with data loss at the moment. 

So, like sdennie mentioned: DON'T DO IT. Unless you have absolutly WORTHLESS data and time on your hands for potential recovery, its not worth it. Even if you back up your data, you'll still have the possibility of losing data after the upgrade. 

Wait a few months and I'm sure everything will work flawlessly. 

All this said, it is possible to do, so if you think you'll see a big enough difference and performance gain, by all means give it a shot.

Wasn't that bug fixed about a month or so ago. I've had a few (deliberate) system crashes and didn't lose any data (I know this says nothing, but still ;) )

---

### Post by djbushido on 2009-04-09
So ext4 will be "stable" when 9.04 comes out? Meaning usable without fear of losing data?

---

### Post by PreviousN on 2009-04-09
I'm not an expert on ext4, but I have been around the forums a lot lately. I've seen quite a few people still having problems with it. So, "wasn't that bug fixed about a month ago?" no. 

From what I understand is that sometimes programs aren't written in a certain way that ext4 behaves, causing loss of data. Some may say that this is not ext4's fault, but I don't care who's fault it is. If the problem exists and may cause data loss, then I'll just stick to what I have. 

I'm not sure it will be fully stable by 9.04. But, I'd say that it should be "stabler." In that it won't affect most people. 

I won't adopt it until July or so.

---

### Post by whoop on 2009-04-09
> **PreviousN said:**
> I'm not an expert on ext4, but I have been around the forums a lot lately. I've seen quite a few people still having problems with it. So, "wasn't that bug fixed about a month ago?" no. 

From what I understand is that sometimes programs aren't written in a certain way that ext4 behaves, causing loss of data. Some may say that this is not ext4's fault, but I don't care who's fault it is. If the problem exists and may cause data loss, then I'll just stick to what I have. 

I'm not sure it will be fully stable by 9.04. But, I'd say that it should be "stabler." In that it won't affect most people. 

I won't adopt it until July or so.

 on 2009-03-16
Changed in linux:
status: 	Fix Committed &#8594; Fix Released

But I agree, ext4 is relatively new and therefore if you don't have to/need to/want to use it, you shouldn't.

---

### Post by djbushido on 2009-04-09
I'm wanting to migrate to get the benefit of the system tracking corrupt blocks. I'm having problems with unclean shutdowns (i'm on a usb drive, not hdd), so I think that this will drastically shorten fsck times.
To confirm, the commands should be:
> No, I'm waiting for 9.04 to come out. I think that what i will do is have update-manager upgrade, which fixes grub.
Then, copy off data using the command:
"tar cfp /home/brad/xubuntu.tar ." when in the xubuntu partition.
Then, reformat as ext4 (probably using gparted).
Reset the UUID - "tune2fs -U <some-uuid> /dev/XXX"
Mount as ext4 - "mount -t ext4 /dev/XXX /media/xubuntu"
Copy data back on using "tar xfp ../home/brad/xubuntu.tar" which will untar the file onto the partition, right?
Update fstab to reflect ext4 with nano. Just change ext3 to ext4, right?
Um... I think that's it, reformatting as ext4 should enable extents, and such right?
grub-install /dev/sda --root-directory=/media/xubuntu --recheck
So it may be butchered, but will work, right?

---

### Post by Ux64 on 2009-05-08
I did convert whole HD (one partition) to ext4 from ext3 without any problems. Everything went well and I'm happy with it.


I'm just wondering when e4defrag program is released, because without that you can't really "finish" migration, because old files will be still using ext3 addressing.

---

