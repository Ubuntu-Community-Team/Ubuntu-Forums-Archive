---
title: "How to use live disk to partition?"
date: 2005-10-13
forum: Desktop Environments
---

### Post by nrwilk on 2005-10-13
I just built a new rig from parts, and I'm excited to get ubuntu on here.

I need some help with the partitioning, please.

specs on the new box are:
AMD Athlon 64 3500+
Abit An8 mortal1ty nForce4 Ultra mainboard
Samsung 200GB PATA HD
1GB Corsair ram


I've never installed Windows before, but I think that should be easy, right?

Anyway, I want to dual-boot Windows and ubuntu.

What partitions do I need, and how big should they be?  I'd like to have 100GB for each OS.

The other thing I need to know how to do is how to use the ubuntu live disk to partition the drive before installing any OS.  What utility do I use?

Thank you SO much for any help!  I know someone here will know exactly what to do with this!

Thanks again!

---

### Post by nrwilk on 2005-10-13
I found a new problem.  The computer won't boot from the live CD unless I unplug the harddrive's IDE cable. Why?  Can anyone tell me how to do this with the harddrive plugged in so I can use the live disk to partition it?  If I hit the escape key while in the POST screen, I get a small menu that lets me choose a startup device, but whenever I choose CD drive it tells me to insert a startup volume and hit enter.  It doesn't seem to see the drive at all when the HD is plugged in.  Is it ok that I have them daisy-chained on the same IDE cable?  Or, should I use two seperate cables?


Again, thanks for any help!

EDIT:
It worked to stick the CD and HD drives on different cables.  Do I have to keep them on seperate cables?  Or after I finish with the whole booting fiasco, can I put them back on the same one?

I'd still like suggestions for partitions, if there are any

Thanks!

---

### Post by drogoh on 2005-10-13
You only need / and swap space.  100G is way too much unless you're doing data storage.  Set it to something sensible.

You also want to install Windows first, then Linux.

Edit: I think the hardware thing is resolved.

---

### Post by Ampersand on 2005-10-13
I'd recommend having a seperate /home partition. That way, you can safely reinstall everything if something goes wrong without losing anything particularly important.

The swap partition should be around 1.5 times your RAM, the / partition size is up to you, but you shouldn't need any more than 10Gb.

You might also want a FAT partition if you want any files that both Windows and Linux can read and write.

---

### Post by nrwilk on 2005-10-13
Thanks a lot!

What is the utility I can use from the live disk to partition?


I found one called parted, is that any good? or is there a better one?

Also, I'd still like to know if it's ok to put the two drives back on the same cable once I'm done with all this booting from CD stuff.


And, yes I re-thought my space needs and I decided on 150GB for windows and 50GB for Linux.  Instead of 100/100.

---

### Post by the_purulent on 2005-10-13
If it won't boot from the cd when your hdd is attached, make sure you have your bios set to boot from cd first.  could be that whatever was on your disk first is taking priority.

---

### Post by Ampersand on 2005-10-13
If you're moving drives around, you need to make sure that the jumper settings on the drives are correct, and the bios is set up correctly.

The hard drives should have jumper switches on the back to set them to either master or slave. If you have them both on the same cable, make sure one of them is set to each (there should be a key on the drive saying what each jumper position means.

In the IDE section of the bios setup (after pressing whatever key it tells you to enter setup while its booting), go to the IDE setup page and make sure everything there is set up correctly (setting each of the positions which has a drive to auto usually works).

Your hardware's documentation should have more detailed/coherent instructions (:

For the partition editor, I'd recommend Gparted if it's installed on the CD. Parted is also fine if you don't mind using the terminal.

---

### Post by nrwilk on 2005-10-13
can I just create a 150GB partition for Windows, and install ubuntu on the free space?  Wouldn't that be much easier?

Nice! I had completely forgotten about jumpers.

Switched both drives to cable select, and it works great now!

I'm having trouble figuring out these command line partitioning utilities, though.
neither parted or fdisk.

---

### Post by Rounan on 2005-10-13
I would strongly recommend against having your hard drive and your cd-rom on the same IDE cable. Only one device can use the IDE interface at a time. Also, hard disks generally operate in mode UDMA5 or 6, which is very fast. Optical drives can generally only do UDMA2, because the extra bus speed is meaningless for them - their data transfer is already maxed out. A given IDE channel can only do one speed, so your hard drive will only be using UDMA2.

Putting an optical drive on the same IDE ribbon as your hard drive will not only mean that you can't access the hard drive and cd-rom at the same time, but your hard disk will run slower even when the optical is idle. It's a major performance hit.

For a partition scheme, I would recommend ~15-30GB for Windows. 15 if you're just using the OS, Office, and basic apps. More if you plan on installing multiple games. 5-10 gig, max, for your ubuntu / partition. My ubuntu /, with many things installed, is well under 3 gig. Create a seperate /home partition, and give that perhaps 5GB unless you plan on writing a lot of documents or storing years and years of email. Make the rest of the drive a data storage partition. If you want to be able to read and write to it from both OS's, it should be FAT32. If you plan on spending much more time in Windows, make it NTFS, and you'll still be able to read it from Ubuntu. If you're using mostly Ubuntu, make it a linux filesystem (reiserfs or ext3) and know that you won't be able to see it from Windoze. So:

hda1     Swap               ~1.5GB
hda2     Windows           ~10-30GB          NTFS
hda3     /                      ~5-10GB           ext3 or reiserfs
hda4     <extended partition. You're going to have more than 4 partitions.
hda5     /home               ~3-5GB             ext3 or reiserfs
hda6     /data                Remainder          FAT32?

---

### Post by paul6888 on 2007-11-22
I'm trying to partition my laptop's 80GB HD and GParted is confusing me. Any help?

---

