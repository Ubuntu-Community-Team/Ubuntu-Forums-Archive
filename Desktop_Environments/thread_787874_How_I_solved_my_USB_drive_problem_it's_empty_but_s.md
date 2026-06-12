---
title: "How I solved my USB drive problem: it's empty but says it's not"
date: 2008-05-09
forum: Desktop Environments
---

### Post by davidshere on 2008-05-09
I recently looked at my USB drive, a 4GB Sandisk Cruzer U3, and noticed that it said that the total size of the files was ~800MB but that the total space available was only ~1.6GB.  

I read up and found that the most common cause of this problem is when nautilus/gnome deletes a file on a USB drive, it actually moves it to a trash folder on the drive, thereby not deleting it.  The solution here is to show your hidden files and delete the .Trash-yourUsername folder, or empty the trash on your desktop.

But that didn't work for me.  I chose View>Show Hidden Files, but the .Trash-david folder was empty.  So I deleted everything off the drive.  It still said that 1.6GB was used.

```
david@raptor:/media/disk$ ls -lash
total 16K
 12K drwx------ 2 david root  12K 1969-12-31 19:00 .
4.0K drwxr-xr-x 5 root  root 4.0K 2008-05-09 08:32 ..
david@raptor:/media/disk$ df -h
Filesystem            Size  Used Avail Use% Mounted on
....
/dev/sdb1             3.9G  1.6G  2.3G  42% /media/disk
```

[I]By the way... I recently, and quite unintentionally, placed my USB drive in an area in which it was surrounded by water (clothes washer), and feared that it was lost forever (much cursing)... 
[/I]
Windows was no help -- I tried running a disk check and I got a blue screen of death.  So I decided to do a disk check in Ubuntu from the command line:

```
david@raptor:/media$ sudo umount /media/disk
[sudo] password for david:
david@raptor:/media$ fsck /dev/sdb1
fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
? 1
Reclaimed 416900 unused clusters (1707622400 bytes).
Free cluster summary wrong (584604 vs. really 1001504)
1) Correct
2) Don't correct
? 1
Leaving file system unchanged.
/dev/sdb1: 0 files, 1/1001505 clusters
david@raptor:/media$ fsck /dev/sdb1
fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
? 2
Reclaimed 418050 unused clusters (1712332800 bytes).
Free cluster summary wrong (584604 vs. really 1001504)
1) Correct
2) Don't correct
? 1
Leaving file system unchanged.
/dev/sdb1: 0 files, 1/1001505 clusters
david@raptor:/media$
```

I'm not sure what all this means, but it seemed clear that (a) there was a filesystem problem, and (b) this didn't fix it.  

**SOLUTION:**
I used gparted to run a disk check, and it "recovered" the data, which I didn't really want anyway, so I deleted that, and now my drive is back to it's glorious empty capacity.  I believe that Gparted ("Partition Editor") is included with Gutsy and above.  If you don't see it in your menu, you can install it by typing:

```
 sudo apt-get install gparted
```

0.  Plug in your USB drive.  Watch it appear on your desktop.
1.  Choose System>Administration>Partition Editor (enter your password)
2.  In Partition Editor, choose Gparted>Devices, and then the device that corresponds to your flash drive (which I determined by looking at the total size of the disks)
3.  Unmount the drive: Select it in the list, then choose Partition>Unmount.  
4.  Choose Partition>Check.  A window will pop up on the bottom saying that this one task is pending.  BE SURE THAT NO OTHER TASKS ARE PENDING.
5.  Click "Apply", and "Apply" again in the confirmation dialog window.
6.  When Gparted is done with the check, it will re-mount the drive and open it in a new window.  
7.  Be sure to close Gparted.

If there is an easier way to do this or someone has some additional suggestions, I welcome any feedback.

---

### Post by phr0ze on 2008-05-09
Redoing the partitioning was exactly what I was going to suggest. Hopefully this doesn't happen so often that you need to worry about an easier way. But there is a command like partition editor some people would find faster than gparted.

---

### Post by Richard85 on 2011-02-16
this did not work for me. gparted couldn't finish the operation bc of some error.

---

### Post by archangel2003 on 2012-09-20
0.  Plug in your USB drive.  Watch it appear on your desktop.
Got it.

1.  Choose System>Administration>Partition Editor (enter your password)
And where is system?
Is it system tools? 
Because there is no admin there.

2.  In Partition Editor, choose Gparted>Devices, and then the device  that corresponds to your flash drive (which I determined by looking at  the total size of the disks)
3.  Unmount the drive: Select it in the list, then choose Partition>Unmount.  
4.  Choose Partition>Check.  A window will pop up on the bottom  saying that this one task is pending.  BE SURE THAT NO OTHER TASKS ARE  PENDING.
5.  Click "Apply", and "Apply" again in the confirmation dialog window.
6.  When Gparted is done with the check, it will re-mount the drive and open it in a new window.  
7.  Be sure to close Gparted.

If there is an easier way to do this or someone has some additional suggestions, I welcome any feedback.

---

### Post by coffeecat on 2012-09-20
> **archangel2003 said:**
> 

1.  Choose System>Administration>Partition Editor (enter your password)
And where is system?
Is it system tools? 
Because there is no admin there.

@archangel2003, you are responding to a 4+ year old post which is describing the layout of the old gnome 2 desktop which is no longer current in Ubuntu. Please do not resuscitate dead threads. If you need help with your issue, please start a new thread including details of which version of Ubuntu you are using.

Old thread closed.

---

