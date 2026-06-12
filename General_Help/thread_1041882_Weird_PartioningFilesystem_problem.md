---
title: "Weird Partioning/Filesystem problem"
date: 2009-01-17
forum: General Help
---

### Post by JebusWankel on 2009-01-17
I recently repartioned my hard drive to install windows 7 as a dual boot with my existing Ubuntu 8.10. I used the livecd to do the partioning. I wasn't sure how much to give to windows, so I initially set it to give all the free space from my home partition to the new partition, then I set it to leave about 5gb of free space on the home partition. Then I hit apply. All it needed to do was shrink the home partition once and create the new partition. I forgot that is not how gparted works, so it took 4 steps instead of two. 
1. It shrank the home partition, ridding it of all free space.
2. It grew the home partition by ~2gb
3. It created the new partition formatted in ntfs.
4. It grew the home partition another ~2gb.

I didn't know it was bad to do step 1. I fixed GRUB and both OS's boot. Windows runs fine, Ubuntu runs well enough except for some weird stuff. There is no free space on /home, even if I delete stuff. df-h gives out

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             192G  184G     0 100% /home


When I tried stuff like sudo grub, and gksudo gedit from the terminal to fix GRUB, the commands didn't work. They would accept my password and then complete without doing anything.

Firefox doesn't display the Bookmarks toolbar folder. I had a bug where this happened, I just had to disable the ubuntu firefox add-on, take the bookmark toolbar folder off and put it back on. Now when I do the latter, I can't put it back, because now the Customize option gets disabled, along with all the menubar menus. My history is gone when I shift-ctrl-h, but not the most recent history under the history menubar option. The search field doesn't work. 

My Nautilus bookmarks are gone. Luckily there were only two. I've had this happen before as well.
I wanted to open firefox in safe mode, so to find out what to put type in the terminal, I did "man firefox" but there's no entry. I don't know if this is normal.

When I partitioned the hard drive, GParted ran fsck (IIRC, it was e2fsck -p -v -y, which is weird, because I tried to run it on my own and it said esfsck is only for ext2, and I of course only have ext3 besides the new ntfs one I made) between just about everything it did and didn't bring up any errors. When I run it now it doesn't give out errors. I don't normally run fsck so I'm not sure how it's supposed to behave, but I did fsck.ext3 /dev/sda3 and seconds later it printed the free space, total space and said there were no errors. The partitioning took about two hours, most of the time being taken up by fsck. Come to think of it, GParted may have run e2fsck with -f not -p, which would explain why it took longer.

I'm really confused, I hope someone can help. Thanks.

---

### Post by JebusWankel on 2009-01-17
bumpkins

---

### Post by jerome1232 on 2009-01-17
Sounds like classic symptoms of having a full disk to me, you emptied your trash and everything?

You can use du to find which folders have alot of data in them. I think you just need to delete some more stuff and empty your tash.

```
du -hx --max-depth=1 ~/
```

---

### Post by caljohnsmith on 2009-01-17
Since you are having problems with sudo, how about using your Live CD instead, and please post the output of:
```
sudo fdisk -lu
df -h
```
And we can go from there if you want.

---

### Post by JebusWankel on 2009-01-17
fdisk -lu reads:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004cdda

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20016989    10008463+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2        20016990    23888654     1935832+  82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sda3        23888655   429674489   202892917+  83  Linux
/dev/sda4   *   429674490   488392064    29358787+   7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
```
df -h reads:
```
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 493M  2.0M  491M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 493M  2.0M  491M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 493M     0  493M   0% /lib/init/rw
varrun                493M  104K  493M   1% /var/run
varlock               493M     0  493M   0% /var/lock
udev                  493M  2.8M  490M   1% /dev
tmpfs                 493M  104K  493M   1% /dev/shm
rootfs                493M   99M  394M  20% /
/dev/scd0             699M  699M     0 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 493M   12K  493M   1% /tmp
/dev/sda4              28G   16G   13G  57% /media/Windows
/dev/sda3             192G  183G     0 100% /media/disk
```
Right now I'm using the LiveCD to ferry files to the windows partition. I'll post any updates on the sitch. Thanks.

---

### Post by caljohnsmith on 2009-01-17
If you have all your files from your sda3 home partition safely backed up, how about trying the following:
```
sudo umount /dev/sda3 && sudo e2fsck -f /dev/sda3 && sudo resize2fs /dev/sda3
```
Then please post the output of:
```
sudo mount /dev/sda3 /mnt
df -h
```
And we can go from there if you want.

---

### Post by JebusWankel on 2009-01-17
Everything seems to be fixed except my Nautilus bookmarks have been replaced with those of a default Ubuntu installation, which is an incredibly trivial problem. I even got back my last Firefox session, tabs and all. I'm gonna call this problem solved. Thanks again.

---

### Post by caljohnsmith on 2009-01-17
Glad that worked OK; cheers and have fun with your Ubuntu install.

---

### Post by jerome1232 on 2009-01-17
@caljohnsmith So I take it the file system didn't actually get resized correctly by gparted, is this common?

I'm just curious as to how you caught what the problem was.

I mean from what I can tell from all that output shows the partition was ~193 GB and the file system is 192 GB, seemed right to me.

---

### Post by caljohnsmith on 2009-01-18
> **jerome1232 said:**
> @caljohnsmith So I take it the file system didn't actually get resized correctly by gparted, is this common?

I'm just curious as to how you caught what the problem was.

I mean from what I can tell from all that output shows the partition was ~193 GB and the file system is 192 GB, seemed right to me.
I guess for one thing, I noticed from "df -h" that the sda3 home partition was using 183 GB out of 192 GB, and yet it was marked as 100% full; losing 9 GB to file system overhead seemed a little high to me, but I could be wrong about that since it is such a large partition. The main thing that tipped me off is that JebusWankel said his home partition was still showing at 100% full even after he deleted some files, so that's how I figured it had to be a problem with the resizing. So the bottom line is yes, I think that somehow in JebusWankel's multiple resizing efforts, somehow the sda3 home partition was not resized correctly. I really don't know if it is a common problem with gparted, because I haven't resized enough ext3 partitions to have a feel for it. I just know that using that e2fsck followed by resize2fs trick often cures that type of problem. :)

---

