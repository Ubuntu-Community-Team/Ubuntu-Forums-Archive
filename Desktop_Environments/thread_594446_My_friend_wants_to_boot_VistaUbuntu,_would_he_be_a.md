---
title: "My friend wants to boot Vista/Ubuntu, would he be able to access the Vista partition?"
date: 2007-10-28
forum: Desktop Environments
---

### Post by rainwalker on 2007-10-28
He's the only one in his family who wants Ubuntu, so Vista would be the primary OS. I'm guessing he'd need 8-10 gigs for it, nothing big, but he wants to know if he'd still be able to: 
- Access the files on the Vista partition (all of his stuff is on it). 
- Copy those files over to the Ubuntu partition
- Write files to the Vista partition

Is there a way of doing this? Preferably a way that a not-so-tech-savvy 14 year old would understand?

---

### Post by -grubby on 2007-10-28
Ubuntu 7.10 comes with NTFS-write support by default so it wouldn't be a problem

---

### Post by rainwalker on 2007-10-28
Ooh neat!
What should he do before installing Ubuntu? How can he make the space available for it?

---

### Post by CSMatt on 2007-10-28
There's no reason to move all of the files from the Vista partition to the Ubuntu one anymore; just tell him to save files to the Vista partition and he should be set.

As for making the partition, I'd say reserve about 10 GiB for Ubuntu and whatever the amount of memeory you have for the swap partition.

---

### Post by taurus on 2007-10-28
> **rainwalker said:**
> Ooh neat!
What should he do before installing Ubuntu? How can he make the space available for it?

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by rainwalker on 2007-10-28
Alright! Sounds good.

Still, how should he go about making the space for the Ubuntu install? Is there an official, guranteed way to make space?

---

### Post by CSMatt on 2007-10-28
He could also just install with [Wubi](http://wubi-installer.org/) if he doesn't want to bother with partitioning.  I beleive that it now comes on the 7.10 Desktop CD, so if he already has the CD there's no need to download it.

---

### Post by Tyke91 on 2007-10-28
actually, with updates, feisty is able to read/write ntfs as well.

Dual booting with ubuntu is easy, when you get to the setup screen, select "Manual" when it asks you about partitioning. then just use its partition editor (i think it's just Gparted that has been integrated into the installer) to make room for feisty.

i use gutsy for everything (except windows only games) and right now i'm using 50 gigs (videos and music mostly) my windows partition only has the games on it, so right now it's only got 40 gigs total space and i'm using around 15 of that

---

### Post by rainwalker on 2007-10-28
> **taurus said:**
> [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Hm...that would probably confuse him...especially since it confuses *me*

---

### Post by rainwalker on 2007-10-28
> **Tyke91 said:**
> actually, with updates, feisty is able to read/write ntfs as well.

Dual booting with ubuntu is easy, when you get to the setup screen, select "Manual" when it asks you about partitioning. then just use its partition editor (i think it's just Gparted that has been integrated into the installer) to make room for feisty.

i use gutsy for everything (except windows only games) and right now i'm using 50 gigs (videos and music mostly) my windows partition only has the games on it, so right now it's only got 40 gigs total space and i'm using around 15 of that

Ohh, so there's a graphical way to do it that will handle everything? I didn't know that (but that's because I've never done anything with partitions)

---

### Post by CSMatt on 2007-10-28
Then you're better off using Wubi to install.  See my above post.

---

### Post by Gremlinzzz on 2007-10-28
How to dual-boot Vista with Linux (Vista installed first\
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by rainwalker on 2007-10-28
> **CSMatt said:**
> Then you're better off using Wubi to install.  See my above post.

Are you sure? I've heard some good things and some bad things about Wubi.

---

### Post by Tyke91 on 2007-10-28
I've never used wubi before, but I really don't see the difficulty in dual booting using just the gutsy disk. When i first got ubuntu (my very first non-windows OS and my first experience with dual booting) i was able to dual boot it with no problem. I don't know if it's gotten more complicated since then (a year ago) but i've reinstalled using that same feisty install disk on 4 different computers now, and i've upgraded to gutsy.


dunno... maybe it really IS hard and i've just been lucky enough to have a system that 'just works' with ubuntu.

---

### Post by rainwalker on 2007-10-28
No, I'm probably just freaking out like I always do.
Actually, it's probably because if I tell him the wrong thing, he'll screw up his family's (new) computer and **I'll** get in trouble for it...

---

### Post by CSMatt on 2007-10-29
Wubi works just fine for me.  In fact I would recommend using Wubi instead of risking partitioning errors, which could cause data loss.  Presumably the worst that an Ubuntu installation with Wubi could do would still leave the system usable on the Windows side, unless of course FUSE were to screw up, which in my experience it never has, and if it did screw up on a regular basis we probably wouldn't have Wubi to begin with.

I've used Wubi before on my family's computer and while it isn't prefect it pretty much guarantees that you won't get data loss or an un-bootable system.  I would imagine that a worse case scenario would mean uninstalling it through Windows' Add/Remove Programs utility and reinstalling it, which I'll admit I have had to do a few times.

PS: Wubi is just the installer.  When the page says that Wubi is beta, that means that just the installer is beta.  The system itself is for the most part exactly the same, although at the moment upgrading to a new Ubuntu version won't work.

---

### Post by aysiu on 2007-10-29
I'd recommend installing VirtualBox for Windows and then installing a virtual Ubuntu inside of Vista. No need to repartition, no need to reboot.

---

### Post by CSMatt on 2007-10-29
Wouldn't that kind of defeat the purpose if he wants to use Ubuntu instead of Vista?

---

### Post by dukejib on 2007-10-29
Dear,
Ask your friend to Use the last partition of His Win HD for the installation of Ubuntu.
Steps are
Contorl Panel > Administrator Options > Computer Management > Removable Disks > 
"Check the Partitions, and Remove the last partition ( do remember to copy all the data to some other partition )"
System should read that removed partition as "unformatted space" 
then boot with Ubuntu CD, choose the appropriate options.

---

### Post by CSMatt on 2007-10-29
That would work except that most Windows machines have only one giant partition or one main partition and a hidden "recovery" one put in by the OEM.

---

### Post by Steve1961 on 2007-10-29
You can make space for Ubuntu by shrinking the vista partition with vista's own partition management tools.  In fact this is probably the safest and easiest way to do it.

1. Click on the Start Button and right click on Computer and select Manage.
2. Expand the Storage section and select Disk Management.
3. Then just right click on any partition and select either Expand or Shrink to change the size of the partition.

Also, if you don't want to install grub to the mbr you can use the vista boot manager to boot Ubuntu.  When installing Ubuntu tell the installer to install grub to the Ubuntu root partition.  Reboot into vista once installation is finished and install [EasyBCD]("http://neosmart.net/dl.php?id=1")  You can then use this program to easily add Ubuntu to the vista boot menu

---

### Post by Robocoastie on 2007-10-29
Is he set on Ubuntu? Don't get me wrong, I love it but your friend's needs may be better suited to running a distro off a usb key or as others said, a virtual machine. At least until he/she can scrape up the money to put together a cheap Linux only rig. Provided your friend doesn't want to do things like mythtv, gaming, or other heavy multimedia intensive work it wouldn't be expensive at all to slap one together (the monitor being the costliest, never cheap out on the monitor).

---

### Post by Gold3n on 2007-10-29
When I was trying to install Fietsy on my Laptop I tried to change the partition size and it simply stalled out. I tried to reboot but it was unable to find a bootable OS... After lots of scrambling, this was on my work computer mind you, I was able to use the windows recovery tools to repair mbr and windows started and has ran fine since. 

I really want to dual boot my laptop but I can't risk losing my work data. Do you all think I had a hardware issue which caused the stall? And if i tried again might generate the same problem or do you think it was a just a fault in the software which maybe be improved in Gutsy release?

---

### Post by CSMatt on 2007-10-29
What were you using to resize the partition?

---

### Post by Jhongy on 2007-10-30
Long story short -- partitioning is relatively easy. Easy to resize one partition to make room for another. 99.5% of the time no data is lost. But, as the installer warns you, you should back up any important data before you begin. 

Simple as that ---- so since, whatever method you choose, you'll have to back up --- back up first, then just use the install disk. Don't rely on any partition resizing method to get you by without backups.

---

