---
title: "Dual boot with RAID 0?"
date: 2007-07-09
forum: Dell  Ubuntu Support
---

### Post by rboone on 2007-07-09
Hi,

Complete Ubuntu newbie here -- but before I make a serious mistake ...

I've got a new Dell Dimension 9200 running XP, but the 2-250GB harddrives
are in a RAID 0 configuration (Intel 82801 SATA Raid Cotroller) giving me the
appearance of a single 500GB drive (I had to install the Intel drivers during
the XP install, so I think this is a software RAID perhaps).

I want to add a SATA 500GB drive (ie, a 3rd physical drive) and
install Ubuntu in a dual-boot configuration (the 3rd drive would not
be in the RAID as I understand it).   The RAID stuff has me confused.

Will a simple install work?  Will Ubuntu/GRUB recognize the RAID array
and install GRUB on the MBR of that array (where XP is installed)?  I 
think the BIOS gives the option of setting the boot order to this 3rd
drive first if I want.  Would it be easier to install Ubuntu and GRUB on this
3rd drive, make it the "boot drive" and then add the WinXP Raid drives to
GRUB manually?

Sorry for all the questions, but thanks in advance for any help.
Rog

---

### Post by ZephyrXero on 2007-07-09
I'm no expert, so I may be very much wrong on this.... but from what I understand, GRUB does not like being installed on a RAID array itself. You'll probably have to setup a seperate, non-raid partition for /boot/.

---

### Post by fjgaude on 2007-07-09
FWIK, it's like this: Linux will not recognize the RAID drive because it doesn't have the driver. There are ways, but to that later.

Install Ubuntu on the third drive, boot loader there too, have the BIOS point to it as the boot disk. After it is installed Linux will not even know the Windows RAID is there, yet. If you wish to use Windows, have the BIOS point to the original drive, and reboot.

Now, booting from Ubuntu, install dmraid using Synaptic. Read the man page for dmraid. It shows that you have Intel raid working on other disks.

Then ask more questions here.

frank

---

### Post by rboone on 2007-07-09
Thanks for the replies thus far.  I'm a little unclear on the last message.
Are you saying:

a) I'll never be able to truly dual boot XP and Ubuntu because there are no drivers
available to recognize the array until after Linux loads?  Thus, I would have to do a BIOS change
every time I want to switch between the two OSs, or

b) I should be able to dual-boot (without BIOS changes) after I install the dmraid software.

I know I could try it myself and answer my questions, but before I spend $150+ on
a 3rd drive, I'd like to better my understanding :-)

Thanks again!
Rog

---

### Post by fjgaude on 2007-07-09
After you successfully install dmraid you will be able to access your Windows files from Ubuntu.

I have never seen a situation where a Windows boot would see the Linux partition.

The Windows RAID is not an easy thing to work with, I'm sure you know this.

The normal situation is to install Windows, then install Linux, and from the GRUB file of Linux you can boot into either Linux or Windows. The issue here is that Windows is already on a RAID pair and you can't install Linux on that pair, at least not in a way I can tell you.

If you do a Google of Linux RAID, etc., you'll undestand or see:

  [http://ubuntuforums.org/showthread.php?t=464758](http://ubuntuforums.org/showthread.php?t=464758)

You get an idea of what the issues are and how to overcome them. Just getting Linux to boot from a software RAID is no easy feat, but can be don't. Then adding the overhead of having Windows already loaded onto a RAID partition makes life difficult, but not impossible.

Here's another post you might find interesting:

  [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Good luck!

frank

---

### Post by fjgaude on 2007-07-09
To perhaps better understand the problem, Linux sees the Windows RAID at boot up as two separate drives. There is no RAID until Windows boots. So what would we put into the GRUB files to boot into Windows, what drive letters?

Maybe there is someone here with more knowledge than I that can point to a solution, maybe a Dell engineer?

frank

---

