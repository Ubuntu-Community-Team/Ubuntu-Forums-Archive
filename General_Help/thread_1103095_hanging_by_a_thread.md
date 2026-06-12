---
title: "hanging by a thread"
date: 2009-03-22
forum: General Help
---

### Post by seabrighter on 2009-03-22
I had originally posted in another section of the forum, but now I realize this may be a more general problem.

Background:  First time user, Windows has crashed beyond repair, fixed drive still has critical data, running Ubuntu 7.04 from the LiveCD

Objective:  Must migrate critical data from fixed drive onto an external hard drive in order to safely install new OS (Ubuntu)

Problem:  Ubuntu not able to write data to external hard drive

Description:  The fixed hard drive is fully intact and accessible.  All critical data can be read and verified.  The external hard drive (via USB) is fully functional.  GParted can recognize the external and format it.  The external has been formatted a number of times, in a number of formats (NTFS, EXT3, FAT32).  However, when attempting to move files to the external, the drive is always "locked," and not writeable.  Gparted will then show a little "lock" icon when it lists the drive.

At one point some files were "test copied" onto the external drive when it was formatted to FAT32.  However, I am not in favor of moving all my data from an NTFS hard drive to a FAT32 external drive, thereby losing some of the data.  

Other issues:  After formatting the external hard drive, "mounting" it, and failing to write data, when attempting to "unmount" the drive I get the following message:  "there is data that needs to be written to the device Hitachi HTS543225L9A300 before it can be removed.  Please do not remove the media or disconnect the drive."  It has said this every single time I try to unmount.

Obviously I could go buy a $50 hard disk enclosure that would allow me to plug my fixed hard drive into another windows computer and transfer to the external, but the idea is not to spend a bunch of money.  I'm trying to work with what I have, and I would eventually like to fully install Ubuntu once I know my data is safe and secure.  I'm desperately stuck in this limbo world of running my computer from my CD drive.  I'm hoping someone can shed some light on this dilemma and show me that Ubuntu offers real solutions, not just more problems.

Thanks in advance.

---

### Post by howefield on 2009-03-22
Try running nautilus from terminal with superuser rights.

```
gksu nautilus
```

Then try copying your data.

---

### Post by seabrighter on 2009-03-22
> **howefield said:**
> Try running nautilus from terminal with superuser rights.

```
gksu nautilus
```

Then try copying your data.

Just gave this a shot...nautilus looked just like the regular file browser except it did not show the fixed hard drive nor the external.  Is there something I'm not understanding about this program?

---

### Post by 3Miro on 2009-03-22
I had a similar problem once, Ubuntu was reading the NTFS files permissions and since I was in as a regular user, I could not copy the files.

gksu nautilus

Fixed the problem. You will be transferring files as almighty root.

---

### Post by seabrighter on 2009-03-22
> **3Miro said:**
> I had a similar problem once, Ubuntu was reading the NTFS files permissions and since I was in as a regular user, I could not copy the files.

gksu nautilus

Fixed the problem. You will be transferring files as almighty root.

OK, now I understand how this is supposed to work.  Nautilus shows the File System, and I can find the drives under /media/disk (fixed drive) and /media/disk-1 (external drive).  Still, both drives have a little lock listed on them.  Tried to go into the properties of disk-1 and it would not let me change them to read and write.  It still says the drive is read only.  Root not so allmighty?

---

### Post by howefield on 2009-03-22
> **seabrighter said:**
> Root not so allmighty?

Is root sitting in the swivel chair ?

---

### Post by seabrighter on 2009-03-22
> **howefield said:**
> Is root sitting in the swivel chair ?

Not sure what that means?

---

### Post by emarkay on 2009-03-22
Get teh latest (Intrepid) version - there is better NTFS "finding" abilities, as I see - just even try the live CD to confirm!

---

### Post by seabrighter on 2009-03-22
> **emarkay said:**
> Get teh latest (Intrepid) version - there is better NTFS "finding" abilities, as I see - just even try the live CD to confirm!

It's a great idea, in theory.  The Live CD that I'm currently running on was given to me.  Since I do not have an OS without this CD being in the drive, I do not have the ability to burn a new OS CD.  Of course, if Feisty is my problem and Intrepid is the only solution, I would go out of my way to make a field trip to someone's house to burn the new OS.

---

### Post by emarkay on 2009-03-22
Yea, I can't guarantee that's going to solve it, but if you were local (south Indiana) I'd fling one your direction today; bored and nothing planned)

Prob worth getting latest release anyway.

Going to leave this to the experts now.

---

### Post by seabrighter on 2009-03-22
After reading [the following]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G"), I'm guessing that maybe my problem is indeed Feisty?  It seems like there is no way for Feisty to support writing to NTFS drives.  I'm tempted to try making this work with EXT3 formatting, but I am still nervous about moving my data from NTFS to EXT3.

Here are my two next possible paths of action:

A.  Find another computer, download and burn Intrepid, boot my system with Intrepid LiveCD, attempt to make the data migration while preserving the NTFS format.

B.  Reformat the external drive in EXT3 format, attempt to mount it with full write permission (assuming [these instructions]("https://help.ubuntu.com/community/Mount/USB") will work, and copy my data onto the external in EXT3 format.

My instinct tells me to go with option A.  Can anyone give me a push in one direction or another?

---

### Post by issih on 2009-03-22
[http://www.howtoforge.com/ntfs_3g_ubuntu_feisty](http://www.howtoforge.com/ntfs_3g_ubuntu_feisty)

You could do that to instll ntfs write support, but as the system is entirely in ram (and on the cd) you'll need to install it every time you boot the pc.

Hope that helps

---

### Post by seabrighter on 2009-03-22
> **issih said:**
> [http://www.howtoforge.com/ntfs_3g_ubuntu_feisty](http://www.howtoforge.com/ntfs_3g_ubuntu_feisty)

You could do that to instll ntfs write support, but as the system is entirely in ram (and on the cd) you'll need to install it every time you boot the pc.

Hope that helps

I liked that idea, but unfortunately when I search the Synaptic Package Manager for ntfs-3g, it does not even come up.  Back to option A...

---

### Post by ZarathustraDK on 2009-03-22
Here's a linky that may help in regards to ntfs-3g: [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

The reason you may not be able to find it with synaptic is because you haven't enabled the universe-repository (I don't think universe-repos are enabled by default on livecd's, but they can be enabled manually).

---

### Post by JohnLM_the_Ghost on 2009-03-22
As I understand you only have trouble copying to NTFS, which as it turns out Feisty doesn't support.

And don't sweat too much moving data to a different partition type. You won't lose any data, except some permission metadata you'd lose anyway (and what you probably won't need).

I'd go for ext3 if you don't need windows to read it later... else fat32.
Only thing about fat32 is it doesn't support 4GB+ files.

---

### Post by seabrighter on 2009-03-22
Good news!!

Option A worked like a charm.  Apparently Feisty was the only thing stopping me from copying my data to the external drive.  Once I booted up with Intrepid, the drives mounted up with no problems and files freely flowed in between.  All my essential data is backed up and I'm ready to do a full install of Intrepid tonight.  Wish me luck!

---

