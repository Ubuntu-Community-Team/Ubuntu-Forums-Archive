---
title: "windows 98 wont read disc"
date: 2008-08-30
forum: Desktop Environments
---

### Post by codzilla on 2008-08-30
i put the alternate cd on a blank cd and when i put in my windows 98 computer, it just acts like there is no disc there. It is on the disc though, because my friends xp computer recognized it.

---

### Post by Cato2 on 2008-08-31
> **codzilla said:**
> i put the alternate cd on a blank cd and when i put in my windows 98 computer, it just acts like there is no disc there. It is on the disc though, because my friends xp computer recognized it.

Is this when you are rebooting your PC?  I'll assume it is.  You need to make sure your Win98 PC has the BIOS set up to boot from CD-ROM first, then hard disk.

Some older PCs can't boot from CD which makes installing Ubuntu more challenging - however, Unetbootin makes this much easier, as long as Win98 has working Internet access.  Unetbootin is a nice GUI installer which downloads a 'network install' version of Ubuntu and uses that to install a complete version of Ubuntu into a partition.  See [http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540) (Ubuntu forums HOWTO on Unetbootin) and [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

If you have problems, try an older version of Unetbootin or see [http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora#comment-3971](http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora#comment-3971) which has a specific workaround.

I haven't used Unetbootin myself but it looks really good and MUCH easier than the way I used to install Linux on PCs without usable CD-ROMs - in fact you can simply run this within Win98 and it will download the Ubuntu 8.04 ISO for you, then modify your boot loader in Win98 so you boot into the Ubuntu installer.  It's a bit like Wubi but installs to a real disk partition (faster and lets you drop Win98 completely), works on Win9x through to Vista, and can install many different Ubuntu or Linux variants.

As always, back up any important data from your Win98 system onto a separate USB stick or similar.

---

