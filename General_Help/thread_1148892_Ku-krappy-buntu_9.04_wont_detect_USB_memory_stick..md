---
title: "Ku-krappy-buntu 9.04 wont detect USB memory stick...."
date: 2009-05-04
forum: General Help
---

### Post by garythegoth on 2009-05-04
Any ideas.....

---

### Post by SuperSonic4 on 2009-05-04
What is the output of ```
sudo fdisk -l
```

---

### Post by garythegoth on 2009-05-04
> **SuperSonic4 said:**
> What is the output of ```
sudo fdisk -l
```
///////////////////////////////////////////////////////
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc4c4c4c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321   83  Linux

Disk /dev/sdb: 8019 MB, 8019509248 bytes
247 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 15314 * 512 = 7840768 bytes
Disk identifier: 0x0005b9f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2               6          40      267995   82  Linux swap / Solaris
///////////////////////////////////////////////////////

Ugh so it is detecting it, but just not letting me know its detected it. Or let me have access to it...........

---

### Post by BslBryan on 2009-05-04
How about downloading Nautilus and using that instead of Dolphin?  That just might solve your problem, I think.

Good luck, garythegoth. :)

---

### Post by garythegoth on 2009-05-04
> **BslBryan said:**
> How about downloading Nautilus and using that instead of Dolphin?  That just might solve your problem, I think.

Good luck, garythegoth. :)

How about I just nuke Kubuntu and install Ubuntu......

---

### Post by SuperSonic4 on 2009-05-04
Don't install nautilus, it's a waste of space in kubuntu - dolphin is much better anyway especially in kubuntu.

You could try mounting from the terminal: ```
sudo mkdir /media/disk && sudo mount -t vfat /dev/sdb1 /media/disk
```


It's possible ubuntu might work but I doubt it to be honest. Have you looked into trying another distro? I believe Mandriva has good hardware detection

---

### Post by garythegoth on 2009-05-04
> **SuperSonic4 said:**
> Don't install nautilus, it's a waste of space in kubuntu - dolphin is much better anyway especially in kubuntu.

You could try mounting from the terminal: ```
sudo mkdir /media/disk && sudo mount -t vfat /dev/sdb1 /media/disk
```
It's possible ubuntu might work but I doubt it to be honest. Have you looked into trying another distro? I believe Mandriva has good hardware detection

///////////////////////////////////////////////////////////////////////////////
sudo mkdir /media/disk && sudo mount -t vfat /dev/sdb /media/disk
mkdir: cannot create directory `/media/disk': File exists
///////////////////////////////////////////////////////////////////////////////

Lol......

---

### Post by garythegoth on 2009-05-04
> **SuperSonic4 said:**
> Don't install nautilus, it's a waste of space in kubuntu - dolphin is much better anyway especially in kubuntu.

You could try mounting from the terminal: ```
sudo mkdir /media/disk && sudo mount -t vfat /dev/sdb1 /media/disk
```
It's possible ubuntu might work but I doubt it to be honest. Have you looked into trying another distro? I believe Mandriva has good hardware detection

Normal Ubuntu 8.04/8.10/9.04 work fine with it.

Its just Ku****** that dosent >.>

---

### Post by BslBryan on 2009-05-04
For a lot of people, KDE is flawless, and very useful.

For a lot of other people, though, KDE doesn't work at all.

I'm Switzerland on the issue, but prefer Gnome.  All I will say is that Gnome is a lot more stable for more people than KDE is, while the opposite is true for some.

If you decide to go with Ubuntu, a clean install isn't necessary.  You can just install the GNOME desktop environment and uninstall KDE.  It would be a LOT quicker.

---

### Post by garythegoth on 2009-05-04
> **BslBryan said:**
> For a lot of people, KDE is flawless, and very useful.

For a lot of other people, though, KDE doesn't work at all.

I'm Switzerland on the issue, but prefer Gnome.  All I will say is that Gnome is a lot more stable for more people than KDE is, while the opposite is true for some.

If you decide to go with Ubuntu, a clean install isn't necessary.  You can just install the GNOME desktop environment and uninstall KDE.  It would be a LOT quicker.

Actually with my ISP throttling my connection like a bitch, it would be quicker to do a fresh install....

And Lol@Switzerland, first time Ive seen that phrase used:lolflag:

---

### Post by BslBryan on 2009-05-04
> **garythegoth said:**
> Actually with my ISP throttling my connection like a bitch, it would be quicker to do a fresh install....

Dude, are you serious?  No way.  How fast can you download anything?  

Just try it.  
```
sudo aptitude install ubuntu-desktop
```

```
sudo aptitude remove kubuntu-desktop
```
> **garythegoth said:**
> And Lol@Switzerland, first time Ive seen that phrase used:lolflag:
Haha, yeah.  I haven't heard/used it in a while, actually. :lol:

---

### Post by garythegoth on 2009-05-04
> **BslBryan said:**
> Dude, are you serious?  No way.  How fast can you download anything?  

Just try it.  
```
sudo aptitude install ubuntu-desktop
``````
sudo aptitude remove kubuntu-desktop
```Haha, yeah.  I haven't heard/used it in a while, actually. :lol:

My download speed is like 24kb/s at the minute. On a 8Meg line...... ¬¬
The Ubuntu desktop is 500meg+ last time I checked.
It takes about 15 minutes to install from the DVD. 
That pretty much sums it up....

@Switzerland, Ive never heard that expresion before, but I may well steal it....:lolflag:

---

### Post by BslBryan on 2009-05-04
Fair point. :)

Come back and tell us how it goes.

---

### Post by garythegoth on 2009-05-04
> **BslBryan said:**
> Fair point. :)

Come back and tell us how it goes.

Hah, I cba to reinstall tonight. I may just glue the Kubuntu DVD to the wall and throw knives at the useless ******* thing. It isnt even worthy of being a coaster... >.<

---

### Post by kevil99 on 2009-05-04
have you formatted the stick? if so be sure to keep it fat32

---

