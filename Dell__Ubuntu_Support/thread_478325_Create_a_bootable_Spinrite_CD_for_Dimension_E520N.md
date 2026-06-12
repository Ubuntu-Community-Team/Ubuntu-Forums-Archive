---
title: "Create a bootable Spinrite CD for Dimension E520N?"
date: 2007-06-19
forum: Dell  Ubuntu Support
---

### Post by Burbank on 2007-06-19
I really need help on:

  Modifying an existing ISO image?
  Making FreeDOS boot properly on my Dimension E520N?
  Booting into DOS and getting it to recognize my second CD drive?
  
I don't know which of these is the real problem.

I just bought my first Linux box as follows:

Dell Dimension E520N
  Intel Core 2 Duo Processor E6320
    (1.86GHz,1066FSB) with 4MB cache
  1GB DDR2 SDRAM at 667MHz
  22 in E228WFPWide Aspect Digital Flat Panel
  256MB nVidia GeForce 7300LE TurboCache
  250GB SATA II Hard Drive (7200RPM)
  2 Optical Drives: 16X DVD-ROM and 16X DVD+/-RW
  Ubuntu Desktop Edition version7.04
  (NO Floppy)
  
I love this machine!

I also bought Spinrite ([http://www.grc.com/sr/spinrite.htm](http://www.grc.com/sr/spinrite.htm)).

All I want to do is make a bootable CD with Spinrite on it. So far, I have spent about 7 hours (and about 30 disks) trying. Emails to spinrite tech support suggest that I may need to wait for spinrite 6.1, but there must be a better answer.

It seems that the FreeDOS that Spinrite uses to create its bootable ISO image won't run on my Dimension E520N. It always locks up part way into the boot process.

If I download the Windows 98 SE ISO boot image from allbootdisks.com that boots just fine on the Dimension E520N. But every time I try to add the Spinrite.exe file to the Windows 98 SE ISO boot disk, that renders it unbootable.



I think another way to ask my question is:

"How can I add a file (spinrite.exe) to an ISO boot image and then burn it to a CD without ruining the image's ability to boot my Dimension E520N?"


(I am an experienced Mac user and know nothing about PC's or Linux. Learning fast.)

Thanks,

Dave Burbank

---

### Post by neptho on 2007-06-19
If FreeDOS won't boot, SpinRite won't work.

Have you tried making a [generic FreeDOS CD](http://www.freedos.org/freedos/files/)?  If it can't boot that, and you are unable to find an old MS-DOS bootable floppy image, you're basically out of luck.

(In my personal opinion, SpinRite hasn't been useful since MFM disks.)

---

