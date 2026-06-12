---
title: "partitioning problems"
date: 2009-05-30
forum: General Help
---

### Post by punkbohemian on 2009-05-30
Recently, I decided to get rid of Vista entirely and run only Ubuntu. I had it (Vista) running on another partition, which I've deleted. Now, I'm trying to resize my Ubuntu/ext3 partition using the live CD, and it won't let me increase the size of the partition, despite having over 75gb of free/unallocated space. Am I missing something? Thanks.

---

### Post by Volt9000 on 2009-05-30
What's the exact error you're getting? A screenshot of the main GParted window and the error would be useful.

First make sure all partitions are unmounted. You can't perform any operations on mounted partitions.

---

### Post by punkbohemian on 2009-05-30
I'm not getting any error. When the resize window pops up, the maximum size I can enter is the size the partition already is. As for unmounting the drives, I booted from the live CD so nothing should me mounted. However, I did see the "key" icon next to my linux swap partition and the the "extended" partition (the latter I assume is due to the swap partition being mounted. The Gparted window basically looked like this:

[http://s51.photobucket.com/albums/f364/badhabitbrota/Screenshot--dev-sda-GParted.png](http://s51.photobucket.com/albums/f364/badhabitbrota/Screenshot--dev-sda-GParted.png)

with the only difference being that /dev/sda5 partition wasn't mounted (I'm not currently running off the live CD). As you can see, I have 76.53gb unallocated and I want to tack that on to the ext3 partition. What should I do now? Thanks.

---

### Post by punkbohemian on 2009-05-30
*bump*

---

### Post by freebeer on 2009-05-31
Probably the easiest and safest way is to reformat the old NTFS partition to ext3, then mount that partition as part of the file system rather than trying to enlarge the existing partition to incorporate the extra space.  (Which is what I think you are thinking of doing.)

---

### Post by punkbohemian on 2009-05-31
You're right, I am trying to enlarge the space.

Creating another ext3 partition is plan B. It would be a lot more convenient for me if I could just have one larger partition. For starters, I would have to mount the second partition every time I boot up...

I don't know if this matters, but when I rebooted, I noticed that vista was still listed in my boot menu, even though I completly wiped the partition it was on. Is it possible that remnants of vista still linger and have "reserved" that chunk of my hard drive making it impossible to resize my ext3 partition?

Anyway, the remaining space is free. I don't see why I can't just tack it on to an already existing partition.

---

### Post by tommah04 on 2009-05-31
sorry for my lack of information... but I believe there's actually a program for re-designating partition sizes.....but for the life of me I can't remember the name :-/

so unless I'm completely wrong, you might wanna start there

---

### Post by freebeer on 2009-05-31
Personally, I'd be a little leary of trying to extend or tack on the additional space to the same partition.  First of all, the new space needs to be formatted, and I'm not aware of any handy tools that would allow you to do that, nor would I consider it a safe practice.  If you do attempt it, make sure you back up everything first!

Having to mount the drive every time you boot up can be made an automatic process... it's a quick and easy edit of the fstab file.

---

### Post by punkbohemian on 2009-05-31
> If you do attempt it, make sure you back up everything first!

I'd consider attempting it, but I don't know how. And I do have everything and anything important backed up. I'm half tempted to wipe out everything (except the recovery partition, of course) and start from scratch.

> Having to mount the drive every time you boot up can be made an automatic process... it's a quick and easy edit of the fstab file.

How do I do that? It's sounding like Plan B is going to have to be my Plan A. :(

And I still don't understand why I can't just resize the partition using gparted. I even formatted the old partition to ext3, just like my main partition...

---

### Post by merlinus on 2009-05-31
PMJI, but it might be useful to post a screenshot of what you are looking at in gparted.

Also, the output of:

```

sudo fdisk -l

```

l is a lowercase L.

---

### Post by punkbohemian on 2009-05-31
the gparted screenshot is a few posts back in the thread, and the sudo fdisk -l command gives me this:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd09d5d20

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9991    80252676   83  Linux
/dev/sda2           17883       19457    12651187+   7  HPFS/NTFS
/dev/sda3            9992       17882    63384457+   5  Extended
/dev/sda5            9992       17554    60749766   83  Linux
/dev/sda6           17555       17882     2634628+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

---

### Post by dandnsmith on 2009-05-31
> **punkbohemian said:**
> the gparted screenshot is a few posts back in the thread, and the sudo fdisk -l command gives me this:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd09d5d20

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9991    80252676   83  Linux
/dev/sda2           17883       19457    12651187+   7  HPFS/NTFS
/dev/sda3            9992       17882    63384457+   5  Extended
/dev/sda5            9992       17554    60749766   83  Linux
/dev/sda6           17555       17882     2634628+  82  Linux swap / Solaris

Partition table entries are not in disk order

Because of the fact that the NTFS partition is physically positioned after the extended partition (which contains a linux partition followed by swap), you'd have to do an awful lot of manoeuvring to do any extension to incorporate it as part of another - easiest route is to reformat it and have it as a separate filesystem, and choose the mount point you want.

---

### Post by punkbohemian on 2009-05-31
> Because of the fact that the NTFS partition is physically positioned after the extended partition...

I kinda suspected that the recovery partition being physically in the middle might be the problem...

So, can anyone tell me how to edit the fstab file to auto mount the new partition every time I boot? Also, is there a way to edit the Places menu (or something else) so that when I click on the Videos folder it will instead go to a folder of videos on this other partition?

---

### Post by kruegger on 2009-05-31
You still have an 12gb ntfs primary partition which prevents you from enlarging the ext3 area and that shows at GrUB menu at booting.

If you delete that ntfs partition and the swap partition, you can enlarge with Gparted graphically by clicking and dragging on the partition bar. The formatting is done after you choose the partition dimensions. A swap partition can be set at any time/place.

This applies if you want to forwardly enlargement (in your case).

If you want to go for the unllocated space directly, it is a backwardly enlargement. This should be done graphically as above.

---

### Post by DeMus on 2009-05-31
> **punkbohemian said:**
> Recently, I decided to get rid of Vista entirely and run only Ubuntu. I had it (Vista) running on another partition, which I've deleted. Now, I'm trying to resize my Ubuntu/ext3 partition using the live CD, and it won't let me increase the size of the partition, despite having over 75gb of free/unallocated space. Am I missing something? Thanks.

You should enlarge the extended partition first, before trying to enlarge the ext3 partition. Your Ubuntu ext3 partition is part of an extended one, so this one has to be enlarged first.
Before all that, unmount all drives otherwise it still won't work.

---

### Post by punkbohemian on 2009-05-31
> You still have an 12gb ntfs primary partition which prevents you from enlarging the ext3 area and that shows at GrUB menu at booting.

That's just a recovery partition hp installs. While booting, I can hit f11 to restore my comp to the factory settings (i.e. one partition, all vista). It has a vista installer, but not vista itself. I haven't tried it, but I think if I were to select it from the boot menu, I'd get some kind of fatal error since the entire vista partition has been wiped.

> You should enlarge the extended partition first, before trying to enlarge the ext3 partition. Your Ubuntu ext3 partition is part of an extended one, so this one has to be enlarged first.
Before all that, unmount all drives otherwise it still won't work. 

When I ran the live CD, the ext3 partition was unmounted, but I wasn't able to unmount the extended partition. I don't even think I had the option to do so. (I'll double check).

I'm still interested in learning how to edit fstab to automatically mount the other partition, and also change the references in the places menu (e.g. so when I choose "Videos", it will go to a folder on the second partition.

---

### Post by freebeer on 2009-05-31
Here's a link to a page describing how to edit the fstab file: [Linky]("http://www.tuxfiles.org/linuxhelp/fstab.html").  It's just the first one I ran across.  You might want to check out a few others (google "fstab editing" or similar) to see which one is clearer for you.

Recently I added a hard drive to one of my systems, so the principles of what you're trying to do is similar, but the details are going to be different.

My new hard drive was formatted to ext4 and the device is /sda1.  I then created a folder in /media/ called "backup".  In your case you'd want to make it "videos" I guess.

I then added the following line to my fstab file using a text editor:
```

/dev/sda /media/backup ext4 defaults 0 0

```

Now I can access my hard drive's contents by going to /media/backup.  If I created other folders there, the path would be /media/backup/newfolder.

---

### Post by punkbohemian on 2009-05-31
Thanks, I'll take a look at the guide.

In the meantime, I cannot write to the new ext3 partition. I mounted it, and when I tried to copy and paste some files over, pretty much all the commands from the right-click menu were greyed out. Do I have to set some kind of read/write permissions on the drive?

---

### Post by merlinus on 2009-05-31
```

gksudo nautilus

```

This will load nautilus with root privileges.  Navigate to the partition and you can change the permissions.

---

