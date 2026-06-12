---
title: "Grub/windows boot help"
date: 2009-06-10
forum: General Help
---

### Post by muad on 2009-06-10
SOLVED! [Entropy_Sam]("http://ubuntuforums.org/member.php?u=842197") is the Man!! (or Woman, as Sam can go both ways, LOL) 


I recently upgraded my machine, and in the process I swapped out my main drive that was dual booting ububtu 8.04 and XP , to a fresh 500GB drive with strickly ubuntu 8.10. I hate and Rarely use windows.

The old drive is still in the PC (I swapped the sata cables), and my Grub menu shows that version of XP on there. However, I can't boot it (says error 22 I think). 

So, I pulled up my menu.lst, and tried to edit the values for that option to point to the correct drive/partition. 

I can't get this to work. Am I missing something. Here is a cut n past from my menu.lst, as well as what gparted is telling me. FWIW, gparted says the drive is not mounted, however I can access it fine in nautilus. 

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Windows XP Media Center Edition
root        (hd2,2)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


Now, gparted shows the drive name as /dev/sdc, and the partiton I want is labeled  /dev/sdc2

I was told that in the grub menu, everything starts at 0, where as grpated starts at 1. So, my partion of /dev/sdc2 in gparted, would be /dev/sdc1 in grub? 

Any help here is greatly appreciated. I am trying to get windows up to play teamfortress2 with my old man online, LOL.

---

### Post by Entropy_Sam on 2009-06-10
Can you post the contents of **/boot/grub/device.map** and the output of **fdisk -l**?

First things first, assuming XP **IS **on (hd2,2) Make the following corrections (the text highlighted in bold) to your menu.lst file:


```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Windows XP Media Center Edition
**rootnoverify        (hd2,2)**
savedefault
makeactive
[B]map        (hd0) (hd2)
map        (hd2) (hd0)[/B]
chainloader    +1
```

To boot an ntfs partition, you'll need to start with **rootnoverify(...)**. Also, XP needs tho think it's on hd0 in order to boot - this is why you'd generally use the map (...) (...) to switch the definitions around.

after those map commands, The XP partition will be (hd0,2). Was XP originally installed to the 3rd partition on that HD? If so, I've a good feeling that the above correction will work, but I'd like to know either way. Could you also please post the contents of your XP boot.ini file (in the root of XP's C:\ drive), as I'd like to confirm a theory...

Hope this helps, and thanks in advance for the feedback :-)

---

### Post by muad on 2009-06-10
Here goes:

device.map:
```
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
(hd3)    /dev/sdd
```

boot.ini:
```
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
```

---

### Post by muad on 2009-06-10
> **Entropy_Sam said:**
> Was XP originally installed to the 3rd partition on that HD? If so, I've a good feeling that the above correction will work, but I'd like to know either way. Could you also please post the contents of your XP boot.ini file (in the root of XP's C:\ drive), as I'd like to confirm a theory...

Hope this helps, and thanks in advance for the feedback :-)

I think so , it's a Dell XPS machine, and they have their recovery crap on there, etc.

---

### Post by muad on 2009-06-10
Nevermind, I understand now.

---

### Post by Entropy_Sam on 2009-06-10
The boot.ini contents confirm my suspicions (the partition numbering).

If your XP install is on sdc2, you can first run it past the contents of device.map to find that GRUB sees it as hd2. The GRUB partition numbering, however, starts a 0 (linux's partition numbering starts at 1) thus sdc2 becomes (hd2,1).

**Don't **change boot.ini, but update your menu.lst to this (change is in bold again):

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Windows XP Media Center Edition
rootnoverify        **(hd2,1)**
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1
```

Should work. If it doesn't I'll eat my hat.

---

### Post by muad on 2009-06-10
I hope you are hungry. 

Does it matter that hd2 was at one time the original drive on this machine, that I was dual booting from?? 

Still comes up with Error 22

---

### Post by Legace on 2009-06-10
> **muad said:**
> I hope you are hungry. 

Does it matter that hd2 was at one time the original drive on this machine, that I was dual booting from?? 

Still comes up with Error 22

Post output of **sudo fdisk -l**

---

### Post by muad on 2009-06-10
Here is where the windows install I want to boot is according to gparted:

[IMG]http://i199.photobucket.com/albums/aa46/muad_dib1982/Screenshot--dev-sdc-GParted.png[/IMG]

---

### Post by muad on 2009-06-10
Here you go, sorry I didn't post this up before. 

```
Disk /dev/sda: 80.0 GB, 80000040960 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd13ad13a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9725    78116031    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0279c74

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1033     8297541   82  Linux swap / Solaris
/dev/sdb2   *        1034       60801   480086460   83  Linux

Disk /dev/sdc: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1           7       56196   de  Dell Utility
/dev/sdc2   *           9       15343   123178387+   7  HPFS/NTFS
/dev/sdc3           18847       19452     4867695   db  CP/M / CTOS / ...
/dev/sdc4           15344       18846    28137847+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9bc77dd9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001    7  HPFS/NTFS
/dev/sdd4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdg: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1         992      999904+   6  FAT16

Disk /dev/sdj: 4089 MB, 4089446400 bytes
61 heads, 60 sectors/track, 2182 cylinders
Units = cylinders of 3660 * 512 = 1873920 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               3        2183     3989504    b  W95 FAT32

```

---

### Post by muad on 2009-06-10
BTW, I Greatly appreciate all the help thus far. IF I can get this working so I can play TF2 with my Dad tonight, that would be awesome!

---

### Post by Entropy_Sam on 2009-06-10
Luckily, i don't **OWN** a hat.

Okay, I think I see the issue. GParted shows a region of unallocated space between sdc1 and sdc2. Now this is a guess, but I reckon GRUB is counting that as a partition. So the original rootnoverify(hd2,2) setting might have been correct (sorry).

You can try this to make sure:

1. Boot normally and when you get to the grub menu, edit the Windows entry on the options list (highlight it and press 'e').
2. edit the first line (but don't press enter yet) so it reads ```
rootnoverify(2,
```
3. With the line incomplete like this, press Tab to see a list of the options. Look for the one where the filesystem is listed as "0x7" or similar (might be some trailing zeros). That should be your XP's ntfs partition. Choose that.
4. If that fails to work, you could edit the first line a few times in a row trying numbers 0-4 until it works (it m ust be ONE of them, right?)

Reason I suggested point 4 is that it seems linux isn't numbering your partitions in the order I'd expect it to. I guess that's 'cause you've had reason to play around with your partitioning quite a lot on this drive :-)

Good luck! :-)

---

### Post by muad on 2009-06-10
Thanks Sam, I'm going to try this now.

---

### Post by Entropy_Sam on 2009-06-10
You'll need to remember which partition number it was, so you can go back and change menu.lst (changes you make at this stage won't stay in place) but this is the easiest way to be sure you're choosing the right partitions.

---

### Post by muad on 2009-06-10
> **Entropy_Sam said:**
> Luckily, i don't **OWN** a hat.

Okay, I think I see the issue. GParted shows a region of unallocated space between sdc1 and sdc2. Now this is a guess, but I reckon GRUB is counting that as a partition. So the original rootnoverify(hd2,2) setting might have been correct (sorry).

You can try this to make sure:

1. Boot normally and when you get to the grub menu, edit the Windows entry on the options list (highlight it and press 'e').
2. edit the first line (but don't press enter yet) so it reads ```
rootnoverify(2,
```3. With the line incomplete like this, press Tab to see a list of the options. Look for the one where the filesystem is listed as "0x7" or similar (might be some trailing zeros). That should be your XP's ntfs partition. Choose that.
4. If that fails to work, you could edit the first line a few times in a row trying numbers 0-4 until it works (it m ust be ONE of them, right?)

Reason I suggested point 4 is that it seems linux isn't numbering your partitions in the order I'd expect it to. I guess that's 'cause you've had reason to play around with your partitioning quite a lot on this drive :-)

Good luck! :-)

Ok, while doing some trial and error, I am now able to start the windows boot process, however it failed the first time (the PC just rebooted by itself), and now each time I try, it brings up the continue in safe mode, etc. Nothing I do will get it to actually Boot. 

The other errors I saw looked like this:

Starting......
NTLDR is missing
Press CTRL+ALT+DELETE to reboot

FWIW, I think Grub is seeing the /dev/sdc drive that has windows on it as hd1 not hd2. That is the only drive that brings up more than one partition, and it shows an ext2fs partition on there, which makes sense since I was dual booting with that drive before.  

I can also get the windows safe mode screen no come up idf I try to boot from hd1,0.

I'm kind of lost now.

---

### Post by Entropy_Sam on 2009-06-10
> **muad said:**
> I think Grub is seeing the /dev/sdc drive that has windows on it as hd1 not hd2. That is the only drive that brings up more than one partition, and it shows an ext2fs partition on there, which makes sense since I was dual booting with that drive before. 

That's odd - device.map maps the way Linux names the drives based on how GRUB identifies them.

this is the contents of device.map as you quoted it earlier:
```
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
(hd3)    /dev/sdd
```
Can you check if device.map has changed or not?

> **muad said:**
> NTLDR is missing
Press CTRL+ALT+DELETE to reboot
This means you've found the Windows partition, but it can't find the bootloader because it's not mapped onto hd0.

Pay attention to this  ;-)

Any time you call rootnoverify with a hard drisk other than hd0, you should remap the hard drives afterwards so the root partition you specified is hd0.

For example, if you're calling **rootnoverify(hd1,...)** (which as you say is the only hd to have multiple partitions) it's *_**crucial**_* that you change the **map **commands to swap hd1 with hd0:
```
map (hd1) (hd0)
map (hd0) (hd1)
```If Vista is on **(hd1,1)** you menu.lst should look like this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Windows XP Media Center Edition
rootnoverify        (hd2,1)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```

---

### Post by muad on 2009-06-10
Ok, I was incorrect. hd2 is the correct drive, however GRUB only shows one available partition (0). It too will try and boot windows, but fails.

---

### Post by Entropy_Sam on 2009-06-10
seriously - you're nearly there! I'm actually prepared to discount what device.map says...

Which partition were you calling with **rootnoverify(hdx,y)** when you got the "NTLDR is missing" message?

---

### Post by muad on 2009-06-10
I got it on both hd1,0 and hd2,0.

I believe hd1,0 did this because I have a XP VM via Sun's vbox.

Let me try it again.

---

### Post by Entropy_Sam on 2009-06-10
If it was on hd1, make sure you change the two map command lines after editing the rootnoverify command:

```
map (hd1) (hd0)
map (hd0) (hd1)
```

---

### Post by muad on 2009-06-10
Ok, Here goes. 
 
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Windows XP Media Center Edition
rootnoverify        (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1
```
 
Will pull up this error:
Starting......
NTLDR is missing
Press CTRL+ALT+DELETE to reboot

---

### Post by muad on 2009-06-10
Now, changing the Map to this:
```

Map (hd1) (hd2)
Map (hd2) (hd1)
```
 
Just sits there with Starting Up..........
 
The thing that I'm wondering it, in gprated it shows my main drive (the one with ububtu 8.10 Only) as /dev/sdb, but it looks like GRUB sees it as hd0. That is why I changed the mapping to see what would happen. I let it sit for about 5 minutes and it never got any further.

---

### Post by Entropy_Sam on 2009-06-10
You wont' need to swap hd2 and hd1 around. Only hd0 with another, as windows needs to see it's hd as hd0.

You said hd(1,0) also gave you "NTLDR is missing". Have you tried this...?
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Windows XP Media Center Edition
rootnoverify        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```

Anyway, good luck - I'm going to bed. I'll see how you got on in the a.m. :-)

---

### Post by muad on 2009-06-10
> **Entropy_Sam said:**
> You wont' need to swap hd2 and hd1 around. Only hd0 with another, as windows needs to see it's hd as hd0.

You said hd(1,0) also gave you "NTLDR is missing". Have you tried this...?
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Windows XP Media Center Edition
rootnoverify        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```Anyway, good luck - I'm going to bed. I'll see how you got on in the a.m. :-)

Thanks soo much for your help thus far Sam.

-Will

---

### Post by Entropy_Sam on 2009-06-10
Last message... with the two map commands remapping hd0 and hd1, go ahead and try all the partitions GRUB can see on hd1 :-)

---

### Post by muad on 2009-06-10
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Windows XP Media Center Edition
rootnoverify        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
```This will start to boot, the windows up splash (if that's what it's called) will even come up for a split second, then the computer just reboots. 

I have a third IDE drive in there that I can take out as it's not needed. Maybe that will change something? 

I'm still confused as to why GRUB only sees one partition on both hd1 and hd2. hd0, shows two (earlier I was mistaken, I thought hd1 showed two partitions). 

I'm pretty much spent for today on this, so hopefully you can think of something else. 

A friend said I need to do this:

"You'll want to install GRUB in the MBR on the first hard drive to prevent a lot of hassles when installing Linux.



If it's installed in the MBR of the second drive now, the BIOS isn't
going to load it unless you set boot order to that drive first (which
will usually impact which drive is set to sda versus sdb, etc. using
the newer naming conventions causing compatibility quirks when you
change boot order to the other drive instead).



IOW, if you want an existing windows installation to work properly, I'd
leave it on the first (boot) drive if that's the way it was installed.
Then, when you install Linux on a separate (second drive if you look at
the BIOS boot order), just tell it to install GRUB in the MBR on the
first drive, which will allow it to point to the /boot/menu.list file
on the second drive without needing to boot from it (at least
SimplyMEPIS which I use for the most part works fine installing it that"
way). 
chainloader    +1

If you want to use the GRUB that's already installed in the MBR on the second drive, you'll have to change the drive boot order so that it boots first (which you can probably do by pressing a function key at startup, although you'll have to change the BIOS setup boot order for some boxes). 

But, it's probably better to reinstall GRUB in the MBR of the first drive with windows on it now."

---

### Post by Entropy_Sam on 2009-06-11
The tricks you've performed so far have gotten you around the problems your firend warned of.
 
I was obviously mistaken earlier over the NTLDR error message - Vista must have upgraded since NTLDR.
 
The only thing I can think of is that **makeactive **is ruining things. Not sure what it does, but there's an explanation here I dont' fully understand... [http://www.gnu.org/software/grub/manual/grub.html#makeactive](http://www.gnu.org/software/grub/manual/grub.html#makeactive)
 
I've a feeling we don't want to be doing what it describes if we're using **rootnoverify(...)** as rootnoverify specifies the root partition without actually mounting it.
 
If you remove the **makeactive** command and Vista STILL won't boot, it probably won't be a GRUB error. I don't think I use **makeactive** when I boot XP (cant' check right now as I'm at work)...

---

### Post by Entropy_Sam on 2009-06-11
One more thought:-
 
When you edit the **rootnoverify **line and use tab autocomplete to see which partition types are available on hd0, hd1, hd2 and hd3, could you write down all the details on the available options (on paper I guess) and put them up here?

---

### Post by dandnsmith on 2009-06-11
> **Entropy_Sam said:**
> 
The only thing I can think of is that **makeactive **is ruining things. Not sure what it does, but there's an explanation here I dont' fully understand... [http://www.gnu.org/software/grub/manual/grub.html#makeactive](http://www.gnu.org/software/grub/manual/grub.html#makeactive).

 I don't think I use **makeactive** when I boot XP (cant' check right now as I'm at work)...

I don't use **makeactive** - it only affects the Windows boot processes, and GRUB just doesn't worry.
All I've ever found it to do is put the boot flag on the partition!

---

### Post by Entropy_Sam on 2009-06-11
> **dandnsmith said:**
> I don't use **makeactive** - it only affects the Windows boot processes, and GRUB just doesn't worry.
All I've ever found it to do is put the boot flag on the partition!
 
Well in this case it might be crucial to either add or remove it, as it's the Windows boot process that isn't working...
 
And I've jsut thought of something else...
 
muad, when you first installed Windows (or when it last worked) which partition was it on? 1st, 2nd or 3rd? If you've removed or added another partition before the one it's currently on, it might be an idea to increment/decrement the partition number listed in C:\boot.ini...
 
Either way, would be good to get a detailed rundown of how GRUB sees/numbers your available partitions at boot-time so I can match things up... to what I think you should see...

---

### Post by muad on 2009-06-11
Ok, I took out the extra IDE drive I had sitting in my box to help remove another variable. 

So, now GRUB shows two drives, hd0 and hd1. I took out the makeactive, and now it gets a disc read error when I try to boot windows on hd1,0. So I added that back in. 

Sam, I am trying XP not vista. I wouldn't own/run that OS if you gave it to me for free.:D

Ok, so GRB shows these options for hd0:

0, 0x82, type unknown
1, 0x83, ext2fs

I'm positive this is my main 500GB linux drive that only has two partitions on it, linux-swap, and ext2.

hd1 only shows 0 is available, and GRUB won't put up a list that has any information for that partition. When I hit TAB, it just puts in a 0.

I have not added/removed any partitions. This is what I did step by step a couple months ago.

Before this upgrade (about 2-3 months ago), I was running a dual boot setup on a 160GB drive with ububtu 8.04 (Ultimate Edition 1., and the origianl XP Media Center edition installed by dell.

Here is what I did during the upgrade:

Installed a new 500GB drive, and used the sata cable that was on my old drive for this new one, put the 160GB drive in the secondary slot, and used that sata cable.

Installed an additional 2GB of RAM

Installed a newer video card (GeForce 7900 GS)

Made a 8GB linux swap partition on new drive, created the ext partition on new drive, installed ubuntu 8.10.

So, here is where I am at Now :popcorn:
device.map
```

(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
(hd3)    /dev/sdd
```

fdisk -l
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0279c74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1033     8297541   82  Linux swap / Solaris
/dev/sda2   *        1034       60801   480086460   83  Linux

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           7       56196   de  Dell Utility
/dev/sdb2   *           9       15343   123178387+   7  HPFS/NTFS
/dev/sdb3           18847       19452     4867695   db  CP/M / CTOS / ...
/dev/sdb4           15344       18846    28137847+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9bc77dd9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS
/dev/sdc4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdi: 4089 MB, 4089446400 bytes
61 heads, 60 sectors/track, 2182 cylinders
Units = cylinders of 3660 * 512 = 1873920 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               3        2183     3989504    b  W95 FAT32
```current menu.lst
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows XP Media Center Edition
rootnoverify        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```Here is what gprated shows now:
[IMG]http://i199.photobucket.com/albums/aa46/muad_dib1982/Screenshot--dev-sdb-GParted.png[/IMG]

And when I try to boot hd1,0, I get this error again :(

Starting......
NTLDR is missing
Press CTRL+ALT+DELETE to reboot     

I don't understand why GRUB doesn't see all of the partitions on hd1???

I'm lost yet again, sorry for this HUGE post

---

### Post by Entropy_Sam on 2009-06-11
> **muad said:**
> So, now GRUB shows two drives, hd0 and hd1. I took out the makeactive, and now it gets a disc read error when I try to boot windows on hd1,0. So I added that back in. 
 
Odd... I take it you've tried looking at hd2 and hd3 in GRUB? **sudo fdisk -l** lists 4 drives...
 
Your GRUB disk order seems to depend entirely on BIOS' disk boot order, so if you want specify the order in which GRUB identifies your disks you can edit them there.
 
> **muad said:**
> 0, 0x82, type unknown
1, 0x83, ext2fs
 
In your case at the moment, hd0 is **definitely** sda - look at the correlation between the filesystem ID in the fdisk output and the values listed by GRUB - (0x82 is Linux-Swap format, 0x83 is linux). Your ntfs will show up (0x7) in this display.
 
The other disks fdisk lists are sdc and sdi - both only have one partition (to speak of) - could GRUB be (somehow) seeing one of those as hd1?
 
```

(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
(hd3)    /dev/sdd
```
 
I thought I had device.map down for sure, but I guess I might be wrong if hd1 doesn't match up with sdb...
 
> **muad said:**
> And when I try to boot hd1,0, I get this error again :(
 
Starting......
NTLDR is missing
Press CTRL+ALT+DELETE to reboot 
 
I don't understand why GRUB doesn't see all of the partitions on hd1???
 
I don't understand why GRUB only displays 2 of your hard drives... Could you take a look in BIOS to make sure all of your hard drives are listed in the boot "queue"? You know, where you've probably got CDs or removable drives as 1st priority followed by your standard first bootable hard disk (which should be hd0). If you add the other drives on there, can you see them from GRUB and select the ntfs partition (0x7)?

---

### Post by muad on 2009-06-11
SAM, the other two drives listed are my USB backup drive, and a 4GB SDHC card in my card reader, LOL. 

I will pull those out now :)

---

### Post by muad on 2009-06-11
Here is an update fdisk-l
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0279c74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1033     8297541   82  Linux swap / Solaris
/dev/sda2   *        1034       60801   480086460   83  Linux

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           7       56196   de  Dell Utility
/dev/sdb2   *           9       15343   123178387+   7  HPFS/NTFS
/dev/sdb3           18847       19452     4867695   db  CP/M / CTOS / ...
/dev/sdb4           15344       18846    28137847+  83  Linux

```In the meantime, I found a post on here about installing Steam and Team Fortress 2 via Wine, so I am in the process of downloading that game, so I can't reboot and try again for about another 45 minutes. 

Thanks again for your help. 

Hopefully GRUB will now see all of the partitions on sdb, and allow me to boot windows. 

I had one other thought that I wanted to run by you. 

I was thinking about swaping the sata cables on the drives, then boot up windows like I use to. 

However, will I still be able to boot linux on the new drive (my current version I am using now)???

Maybe this will solve my problem, and I can still boot windows if NEEDED.

---

### Post by Entropy_Sam on 2009-06-11
Hmm, to be honest, I really don't know why GRUB only sees one partition on hd1.

To be honest, I'm stumped, but I have 2 more ideas:

a) Reinstall GRUB to see if it sees hd1's multiple partitions then. If it can only see one partition on hd1, something strange is afoot in hte land of GRUB.

b) **(last-ditch sure-fire workaround)** Make sure you have a working ubuntu live CD/USB, then overwrite GRUB by runnign the XP install CD and having it fix your MBR. I don't really know much about how to do that, but I've seen a few posts on these forums, so it wodl be worth a look. All just to see if XP will still boot from that (if not, it's not a GRUB error and your XP install might be broken). If it does work, you could think about moving your Linux installation to another HD and just change the drive boot order in BIOS when you want to switch OS's (in mine you can hit F8 - that's what I used to do when I kept them on different drives). You should be able to do that from a Live CD/USB installation.

Good luck :-)

---

### Post by Entropy_Sam on 2009-06-11
Hang on, is your Linux install is ON another HD...? Thinking about it, you've got GRUB on the Linux disk, haven't you

If so boot XP, have it fix the MBR on Windows' disk, then see if Grub loads XP.

If it doesn't, you should still be able to just swap BIOS' boot order to boot from the XP disk 'first' if you want to access your XP install.

Like I say, if it won't load then, it's the OS, not the bootloader.

---

### Post by muad on 2009-06-11
I got it to WORK!!

Thanks sooooooo much for your help Sam. I ended up going into the BIOS, and for some reason under Drives, SATA 2 (which is the port that drive (hd1) was on) was Off. I turned it On, loaded GRUB, searched for avaialbe drives, found the two, looked, and poof! it saw all of the partitions. So, I edited it to read (hd1, 1), and it booted perfect. 

I was also able to get TF2 installed and for oline to play. I will say that I have been spoiled by ubuntu though, for some reason my XP install is a pig. Takes a good five minutes for it to actually function, even thought I'm staring at my desktop, LOL. 

Thanks again! If you were close I'd buy you a Monster, Beer, Coffee, Long Island, whatever it is you drink :)

---

### Post by Entropy_Sam on 2009-06-11
> **muad said:**
> I got it to WORK!!

Thanks sooooooo much for your help Sam. I ended up going into the BIOS, and for some reason under Drives, SATA 2 (which is the port that drive (hd1) was on) was Off. I turned it On, loaded GRUB, searched for avaialbe drives, found the two, looked, and poof! it saw all of the partitions. So, I edited it to read (hd1, 1), and it booted perfect. 

I was also able to get TF2 installed and for oline to play. I will say that I have been spoiled by ubuntu though, for some reason my XP install is a pig. Takes a good five minutes for it to actually function, even thought I'm staring at my desktop, LOL. 

Thanks again! If you were close I'd buy you a Monster, Beer, Coffee, Long Island, whatever it is you drink :)

Fantastic! I know what you mean about being spoiled by Ubuntu - every time I go into XP, I find it clunky and outdated.

Apparently Windows 7 is considerably better, but I've *almost* fully migrated to Linux, now... I'm only using XP for Visual Studio 2008 Express (would run it in a VM, but it doesn't support OpenGL well enough atm).

---

### Post by muad on 2009-06-11
Yeah, I do have a few ULEAD programs that I need still use in XP as well. I also have XP running a VM via Sun's vbox. I was going to try and load TF2 in there, but I set the drive to 10GB (recommended size), thinking I've never need more than that. Well, the game was 6GB, and it wouldn't let me load it on anything else but the "C:" drive. 

I was bound and determined, with your help, to get this working though. My father is an IT professional, and he loves Win7. I downloaded the Beta, but never installed it. I'm sold on linux :)

---

