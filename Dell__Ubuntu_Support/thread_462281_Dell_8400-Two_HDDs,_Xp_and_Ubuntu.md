---
title: "Dell 8400-Two HDDs, Xp and Ubuntu"
date: 2007-06-02
forum: Dell  Ubuntu Support
---

### Post by corjello on 2007-06-02
I've been running Xp for the longest time and recently downloaded and burned the live cd to try it out. Im interested in buying another internal hard drive to run ubuntu on. I would keep my current internal hardrive just the way it is for the transition into using ubuntu the majority of the time. The problem is, what type of internal drive do i need? IDE? SATA? DO-HICKY? haha, but really. Also, if i had one drive with windows and the other with ubuntu, could i easily boot from one drive or the other?

)corjello(

---

### Post by TransitMan on 2007-06-03
If you inded have an 8400, as I do, you need an SATA drive.
Once it is installed, you will need to go the BIOS and activate the drive from there, in order for it to be seen by both WinXP and the Ubuntu Live CD for install.

Once you install Ubuntu onto the second drive, a "Grub" boot loader will install on the first drive, whereby you will be given the option of booting into Ubuntu or Windows, your choice.

I have 3 drives on my machine, all SATA and I am dual-booting XP and (K)Ubuntu with it. Have been using a version of Ubuntu since December 2005.

Best of luck.

---

### Post by corjello on 2007-06-03
awsome, thanks for the tips.

)corjello(

---

### Post by plo on 2007-06-07
I big warning to you.

If you have a raid configuration on your discs it is not as simple as that.
I failed big on that install.

See thread here: [http://ubuntuforums.org/showthread.php?t=462304](http://ubuntuforums.org/showthread.php?t=462304)

If your not in raid - fine.  Also note that removing raid0 means loosing all data if you look in Dell documentation.

/ Palle

---

