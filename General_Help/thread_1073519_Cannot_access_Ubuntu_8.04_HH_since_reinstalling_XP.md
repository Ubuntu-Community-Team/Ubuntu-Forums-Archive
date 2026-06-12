---
title: "Cannot access Ubuntu 8.04 HH since reinstalling XP"
date: 2009-02-18
forum: General Help
---

### Post by Nailhac on 2009-02-18
Hi
I have a duel boot system. 1 hard drive dedicated to UBUNTU 8.04 and the other to XP. All worked well since initial installation 9 months ago. I was always presented with a boot menu asking which build of ubuntu to run or windows xp.
I had a severe problem with XP and reformatted and reinstalled XP home edition (previously had media centre editoin which was problematic). After having reinstalled Home edition XP I find I cannot find the boot menu to access UBUNTU. I would appreciate any help in how to go about either accessing Ubuntu or accessing the normal boot up menu that previously existed.
Thanks in advance.:(

---

### Post by Iowan on 2009-02-18
XP loader seems to be a bit agressive - it'll even overwrite Vista's loader.  I'll look for more specifics, but procedure I remember involves using Ubuntu install CD to repair MBR.

[Here]("http://ubuntuforums.org/showthread.php?t=990830") is a how-to for 8.04.
[Another]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1") Dual boot article.

---

### Post by Slim Odds on 2009-02-18
> **Iowan said:**
> XP loader seems to be a bit agressive - it'll even overwrite Vista's loader. 

LOL    --- MS still likes to think that it's the only game in town.....

---

### Post by wildman4god on 2009-02-18
I have had this problem every time I install xp after ubuntu, check this out: 

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

This will help you get grub back up, also if that doesn't work you might have to modify the boot list I will look for the tutorial on that.

---

### Post by wildman4god on 2009-02-18
Found it:

[http://ubuntuforums.org/archive/index.php/t-393809.html](http://ubuntuforums.org/archive/index.php/t-393809.html)

If you have any questions don't hesitate to ask. best of luck. :D

---

### Post by Nailhac on 2009-02-19
Thanks wildman4god and iowan. Managed to get things up and running again.:)

---

