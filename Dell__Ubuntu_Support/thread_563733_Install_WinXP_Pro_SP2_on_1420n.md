---
title: "Install WinXP Pro SP2 on 1420n"
date: 2007-09-30
forum: Dell  Ubuntu Support
---

### Post by oddabe19 on 2007-09-30
Hey guys,
So i'm receiving a 1420n (probably tomorrow), with Ubuntu pre-installed.  I also have several licenses for WinXP pro (corporate licenses) and would like to use one on this laptop, and dual boot.

I was wondering what experiences people have had doing this on the 1420n.  Are the SATA drivers on the SP2 disc, or will I have to incorporate them onto the disc since I won't have a floppy drive?

What is the availiability of other drivers, and is the 1420n, the same as the 1420?  Will XP already recognize the upgraded display (i got the 1440x900 one)? Wireless, etc?  If not, how available are drivers for that?

Thanks in advance.

---

### Post by notwen on 2007-09-30
I currently dual-boot XP SP2 on my 1420n w/ some small issues.  After shrinking my / partition to make room for the Windows install, Windows likes to install it's MBR into one of the pre-made FAT partitions for Dell's recovery utilities.  This prevent GRUB from launching straight into Windows, so after selecting my Windows option in my GRUB menu list, I go to the Windows boot-loader.  Here is a [thread]("http://ubuntuforums.org/showthread.php?t=540397") w/ links on how to get make a XP disc w/ SATA drivers included.  You may wish to check out all of the links, most are very informative, regarding drivers and such.  Hope this helps. =]

---

