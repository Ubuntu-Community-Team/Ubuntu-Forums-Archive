---
title: "How could I delete my Windows partition?"
date: 2005-07-14
forum: Desktop Environments
---

### Post by Ferio on 2005-07-14
Finally I've got all the software I need in my Ubuntu, and now I want to delete my Windows partition; the scenario is this:

- Windows: hda1 with a boot flag.
- Ubuntu: hda2.

The thing that is worrying me is this boot flag that GParted shows, and how I could extend the Ubuntu partition to use all the space in this HD, since I can't do anything to hda2 because it can't be umounted. Any ideas?

PS: I've got Partition Magic in the Windows partition, could I use it in boot mode to destroy the partition? I don't know if it would work because I'm not sure about the way in which it does so (I mean that I don't know if boot mode works from the partition or from RAM memory).

---

### Post by twowheeler on 2005-07-14
You don't really have to repartition.  Just make a linux filesystem on the windows partition, and then mount it at a temporary place like /mnt/temp.  Then you could move your /home files to the new partition, and then remount it as /home,   

What type of linux filesystem do you use?  (ext3?  reiserfs?  etc)

---

### Post by Ferio on 2005-07-15
Maybe I didn't explain myself clearly enough (my fault); the (complete) scenario is this:

- hda1 with a boot flag: ntfs (Windows).
- hda2: ext3 (Ubuntu's /).
- hda3: linux-swap.
- hdb2: ext3 (Ubuntu's /home).

What I'd want is this:

- delete hda1.
- resize hda2 to fill all the empty space.
- boot my Ubuntu with no problem.

OR

- convert hda1 to ext3.
- merge hda1 & hda2 (is this possible? Partition Magic used to allow this with Windows partitions).
- boot my Ubuntu with no problem.

Summarizing, in the end I only want 3 partitions:

- hda2: ext3 (Ubuntu's /), and a boot flag if needed.
- hda3: linux-swap (exactly the same as now).
- hdb2: ext3 (Ubuntu's /home) (exactly the same as now).

---

### Post by twowheeler on 2005-07-15
Ok, I understand.  All I am saying is that I don't like to mess with the partition table if I don't have to.  All of the partition tools I have seen come with big warnings to the effect that there is a risk of losing all your data so make a complete backup.  The risk is admittedly small but finite so I tend to take those warnings seriously.  The time involved in making (and worse yet, reinstalling and restoring from) backup is considerable.  Since just mounting the partition on the linux filesystem (after a mkfs -t ext3 /dev/hd?? ) is risk-free and is transparent to the user for all practical purposes, it seems like an unnecessary risk to me.  

But of course its your disk, and you can do what you want.  I hope you don't take offense as it is meant to be helpful, not overbearing.  As far as how you do it, sorry I can't help with that.  

Cheers!

---

### Post by Ferio on 2005-09-01
I had some problems with my e-mail account and I didn't know I had another answer. Since I'm not a native English speaker, I didn't notice I was being rude, I didn't meant it, I'm very sorry!

I'm still trying to remove my Windows partition in the way I liked to do it, but it seems not to be possible, I'd probably have problems with the MBR, and moving the Linux partitions because they're active, etc. What a pity :???:

---

### Post by Lord Illidan on 2005-09-01
Instead of removing it, can you resize it to say... 8 mb or so? That will allow the MBR to work, and it will not affect your over all space..

---

### Post by Ferio on 2005-09-01
Well, in fact it's almost 9 Gb size, but it's not just a space problem. Two days ago, I logged in my Windows to try to install an application that I wanted to try, and as soon as I launched IE, I got 6 new icons in my desktop offering me free holydays and so, and I couldn't uninstall the application that was installed without my permission. Neither using ClamWin Antivirus nor using Ad-Aware, the app is still installed, doing only God knows what. Besides, I found a program that runs in Linux with the same functionality I wanted, so I definitely don't want Windows anymore, it has become a moral thing.

I has just thought that maybe reinstalling my Ubuntu and formatting my Windows partition, I will get ridden of it, but I'm feeling lazy right now as to do this...

---

