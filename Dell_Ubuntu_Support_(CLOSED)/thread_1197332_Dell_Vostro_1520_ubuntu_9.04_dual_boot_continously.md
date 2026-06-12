---
title: "Dell Vostro 1520 ubuntu 9.04 dual boot continously reboots"
date: 2009-06-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nikhil.rao on 2009-06-26
Hi,

I recently installed Ubuntu 64 9.04 on my Dell Vostro 1520 dual booted with Win XP Pro. It was working fine until today, when I rebooted from XP. Now it only loads till Grub loading screen (no OS options displayed) and immediately reboots. This happens continously. 

I've tried the built in system diagnostics, and all components are working fine. Has anyone else seen this problem or can help me in any way ?

Thanks !
Nikhil :confused:

---

### Post by nikhil.rao on 2009-06-26
dmesg has these lines :
...
[   10.640230] cfg80211: Calling CRDA for country: US
[   10.660438] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   10.668516] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   10.709257] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 6, Type 5, Revision 1)
[   10.709297] b43: probe of ssb0:0 failed with error -95
....
[   15.193116] Bridge firewalling registered
[   17.059044] ppdev: user-space parallel port driver

---

### Post by Gramps on 2009-06-26
This might help

[http://ubuntuforums.org/showthread.php?t=476940](http://ubuntuforums.org/showthread.php?t=476940)

---

### Post by nikhil.rao on 2009-06-26
Thanks, from that link, I've decided to run the following commands :

First, output from fdisk
```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa42d04a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        6206    49808735    7  HPFS/NTFS
/dev/sda3            6207       29903   190346152+  83  Linux
/dev/sda4           29904       30401     4000185    5  Extended
/dev/sda5           29904       30401     4000153+  82  Linux swap / Solaris
```Then, I propose to run
```
sudo grub
root(hd0,2)
setup(hd0)
quit
```Just want to check that I have the right commands and won't hose my XP install !

Thanks!

---

### Post by nikhil.rao on 2009-06-26
Update : it worked !

I was too impatient to wait for a reply. Does this also make the changes permanent or will Win XP hose the MBR each time it reboots / hibernates ?

Thanks,
Nikhil

---

### Post by spam12345 on 2009-10-03
does this problem repeat randomly after you restore the MBR (grub)?
I also have Dell vostro 1520 and the mbr randomly get corrupted every two or three days.

---

### Post by jward3010 on 2009-10-04
Not to run to far off topic but what CPU did you get with your Vostro 1520? Last week I bought a 1520, love it - but it came with a 32-bit Intel P8700 and I'm wondering what 64-bit CPU did you get?

---

### Post by spam12345 on 2009-10-05
> **jward3010 said:**
> Not to run to far off topic but what CPU did you get with your Vostro 1520? Last week I bought a 1520, love it - but it came with a 32-bit Intel P8700 and I'm wondering what 64-bit CPU did you get?

I've got P8600.

P8700 is a 64bit CPU. [http://ark.intel.com/Product.aspx?id=37006](http://ark.intel.com/Product.aspx?id=37006)

Good luck with your new laptop. Now I just want to refund my laptop and get back to my desktop. Laptops are so troublesome for me. :(

---

### Post by jward3010 on 2009-10-05
Interestingly I was on a product finder on Intel's site different than that one which said otherwise, anyway now I'll give ubuntu64 a blast. But another quick question, is Ubuntu AMD64 not just for 64-bit AMD architectures?

Here's that page in fact: [http://processorfinder.intel.com/details.aspx?sSpec=SLGFE](http://processorfinder.intel.com/details.aspx?sSpec=SLGFE)

mentions nothing about 64-bit capability, whereas on other it does.

---

### Post by urugTON on 2009-10-05
jward3010,

AMD came up with the 64 bit instruction set for x86 cpus.  Intel later adopted it.  Both Intel & AMD cpus run the software labled AMD.

FWIW, my Vostro 1510 with a 56xx CPU runs 64 bit Ubuntu quite nicely.

---

### Post by jward3010 on 2009-10-05
Why the hell do they call there 64-bit release AMD64 if it's universally compatible. That confused me.

---

### Post by urugTON on 2009-10-05
The history is sorta fun.  I like the idea that AMD gets a little credit for making a move that was not widely popular at the time.  OTOH, the confusion that the Linux/Ubuntu naming convention causes is not any kind of fun.  

Some days it even leads to profanity. :lolflag:

---

### Post by jward3010 on 2009-10-06
I ****** know. 

I remember it now, my days of buying Custom PC magazine and the Athlon64's that we're released (and we're good processors) and then Intel followed suit. Ah the memories.

---

### Post by mikemike_2k4 on 2009-12-05
> **spam12345 said:**
> does this problem repeat randomly after you restore the MBR (grub)?
I also have Dell vostro 1520 and the mbr randomly get corrupted every two or three days.
 
The Vostro 1520 is flawed and I beleive they have a BIOS or HW bug that causes this.  I purchased a Vostro 1520 when they first came out and had it for months and had this problem occur every few days at random.  I was using a multi-boot system for my consulting business and this was not acceptable to me to have to constantly repair the MBR.  I fought with Dell for months, including replacing the hard disks 3 times and the entire system motherboard once.  Here is my post on the Dell forums:
 
[http://en.community.dell.com/forums/p/19279816/19512681.aspx](http://en.community.dell.com/forums/p/19279816/19512681.aspx)
 
Dell was so kind to try to brush this issue under the rug by deleting my posts initially.  No one at Dell would listen to me, support me with this problem etc.
 
Dell's stance/cop out is that they don't support multi-booting.  However I worked around their copout by proving to them the following:
 
1.)  In the bios set the hard disk as the first boot device and the 2nd device as the CD/DVD
2.)  Put a bootable CD in the CD/DVD and leave it in.
 
Under a proper working scenario with a correct MBR, you will always boot off the hard disk.  Once the MBR gets corrupted, it will boot off of the CD/DVD.
 
I proved this to the service person that came out and replicated the problem for him after her replace the mainboard and hard disk.  I even said I'd be there Guinea pig to help debug and test experiment BIOS versions and what not to track it down, but thye had no interest in fixing the issue.
 
Needless to say after many painful months of problems with the keyboard, hard drives and this booting problem, I eventually got a full refund.  I'll never buy Dell products again, ever.
 
Sorry to say I think you may be screwed.  The BIOS revision at the time my unit was reimbursed was A03.  They are at A05 but I wouldn't hold my breath.

---

### Post by jward3010 on 2009-12-27
This problem is a Windows specific bug, not BIOS related. See this bug report here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)

It's a little inconsistent, some thought it was down to Recovery software on their laptops (like HP or Dell restore) which would periodically check the MBR for consistency, find that it was changed (to GRUB2) and wipe part of it. They proved it by uninstalling recovery software and finding the problem was gone. 

Other's such as myself don't have any recovery software (I use OEM Windows 7 Ultimate) but the problem still happens and only rears it's head when I reboot FROM Windows 7, not Ubuntu, so it's Windows related but what it is exactly is a mystery and whether Windows will change their software to suit is a mystery.

The discussion seems to be floating around the fact that GRUB2 is larger than GRUB1 and since GRUB is commonly installed on the first partition of a drive (and often a Windows one), Windows possibly wipes the last few bytes of the larger GRUB2 hence corrupting.

---

