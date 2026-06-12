---
title: "Harddrive Corrupted"
date: 2009-05-16
forum: General Help
---

### Post by kngcalvn on 2009-05-16
Hey Everyone!! ):P
(sorry if I'm posting this in the incorrect location, but it didn't seem to fit anywhere else, and seemed like a "general" error.)

I have a Dual installation of Ubuntu and Windows Vista on my Dell Inspiron 1525 labtop.

One fine morning, I turned on my computer and tried to get into Ubuntu, and got the following error:
```

Try (hd0,0): FAT16: No WUBILDR 
          Try (hd0,1): NTFS5: No wubildr 
          Try (hd0,2): NTFS5: No wubildr 
          Error: Cannot find GRLDR in all devices. 
          Press Ctrl+Alt+Del to restart 

```The exact same problem described by this user, except that I didn't change any videocard drivers or anything:
[http://ubuntuforums.org/archive/index.php/t-1014208.html](http://ubuntuforums.org/archive/index.php/t-1014208.html)

I restarted the computer, and tried to get into windows, and got the Blue Screen of Death. I went into command prompt through the Recovery option in windows.

When I try accessing C:\ I get "The file or directory is corrupted and unreadable." I tried chkdsk, it scanned and scanned.... but didn't solve any problems. (But was able to get access to C:\)

WHen I tried the "startup repair" option through the "system recovery options" I got the following output:
```

Root cause found:
---------------------------
System volume on disk is corrupt.

Repair action: File system repair (chkdsk)
Result: Completed successfully. Error code = 0x0
Time taken = 286402 ms
--------------

```but it did not repair the problem.

It looks like neither windows nor ubuntu is able to access the C: "raw"... due to "corruption." (I was later able to confirm that c: does have wubildr, but ubuntu cannot access it.)

Dell computers have an extra "recovery" partition. so what I did was put a copy of "wubildr" onto that partition. When I restarted the computer, and went to ubuntu the wubildr was located on recovery partition and ubuntu started!!! WOOOOO.... I am also able to access all my windows files through "host" so that was a relief *whew*

but windows still does not.


Sooooooooo... I was hunting around this forum looking for an answer and I think I found it:
[http://ubuntuforums.org/showthread.php?p=7007024](http://ubuntuforums.org/showthread.php?p=7007024)
> I've got the same problem (Ubuntu 9.04) and I believe the ntfs-driver is corrupting the partition/ntfs data structure in some very subtle way if you move, create and delete large chunks of data. Perhaps moving gigs from the disk-image to /host might cause this all alone.

That was exactly what I did, I moved 2gb worth of files to my "host" folder in the filesystem, so that I could access it from windows. I tried deleting the files that I have moved, but it was too late, the damage was done.

Is there anyway I can repair this problem without reinstalling everything? PLEASEE HEELPPP!!!!!

Thank you for your time.

---

### Post by kngcalvn on 2009-05-17
Is there a program besides chkdsk that could repair the ntfs partition?

---

### Post by kngcalvn on 2009-05-18
I tried the gparted check didn't help...

anyone have any ideas? I don't want to reformat my harddrive... 

 if there is no solution. Wubi... ubuntu distributions should come with a large warning "DO NOT TOUCH THE FILES IN HOST" they should've made it "read only" or hidden it all together.

---

### Post by cariboo on 2009-05-18
I would suggest you go to your hard drivess manufacturers web site and dwonload and use their diagnostic tools to make your your hard drive doesn't have any more problems.

> if there is no solution. Wubi... ubuntu distributions should come with a large warning "DO NOT TOUCH THE FILES IN HOST" they should've made it "read only" or hidden it all together.

Linux expects you to take some responisbility for what you do, this sounds more like a hardware problem, unless you changed the boot files when you were running Ubuntu.

---

### Post by kngcalvn on 2009-05-18
Thanks, yeaahhh... I just had Dell Diagnostic do a mass Harddrive test, (5 hours... Read, Seek, SMART.. etc.) and it found no errors

Once Ubuntu starts the harddrive it is fully accessible ( the ubuntu installation is running on a virtual partition on the harddrive in question.)

Had I known that transferring large files from ubuntu partition to the ntfs host partition would corrupt the ntfs partition, I wouldn't have done so... was why I suggested a "WARNING" label when users try installing ubuntu using wubi. Wubi does warn against force shutdown, and that causing ntfs corruption, which could be fixed by running chkdsk, but it looks like corruption due to cases such as these cannot be repaired with simple chkdsk.

(this might be completely false, as I don't know anything about how partitions work) What I suspect happened was, the large files were fragmented and thrown all over the ntfs partition, and there was somekind of indexing issue... like the files were indexed in non ntfs standard.

---

### Post by cariboo on 2009-05-18
I have no problem copying 10Gb+ files to an ntfs partition over the network, but I would suggest it is a MS problem, more than an Ubuntu problem, If you have an other computer try copying large files via the network to see if you run into the same problem.

---

### Post by kngcalvn on 2009-05-18
I think Thats different...
Perhaps someone with a wubi installation of ubuntu can try copy some large files into their host folder?
(which I suspected was the cause...since it was the last thing I did before shuting down the computer and I found someone else here reporting the same problem when they moved large files: [http://ubuntuforums.org/showthread.php?p=7007024](http://ubuntuforums.org/showthread.php?p=7007024) )

This is the only computer that I have... I suspect my brother would not be very happy if I mess up his computer lol .

---

