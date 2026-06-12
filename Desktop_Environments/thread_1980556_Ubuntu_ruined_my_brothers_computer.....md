---
title: "Ubuntu ruined my brothers computer...."
date: 2012-05-15
forum: Desktop Environments
---

### Post by Grafeit on 2012-05-15
My brother put Ubuntu on his windows computer and now, by default, it boots to Ubuntu.

Since the grub resolution is so picky, when he turns his computer on, if he boots to the bootloader he see's nothing on screen. His display has a message on it that indicates that there is no input to the display. He has to use the arrow keys and just guess. (luckily he's done it enough to know that pressing down 4 times then pressing enter will boot to windows 7)

He keeps asking me how to remove it from his computer, he doesn't want to deal with Ubuntu at all anymore. From what I can see, it's not possible to boot to use the windows boot loader anymore. I trashed the Ubuntu partition while booted to the windows partition, but I can't seem to find a way to tell the computer to boot to windows by default. I can see his frustration with having to press the down arrow keys (he only gets like 7 seconds to do so, otherwise it boots to something that tells him to install Ubuntu, I had him put Ubuntu back on the computer so that I could try to tinker with it, I still wasn't able to set Windows as the default boot).

Is there anyway to have the computer ignore that bootloader, or just boot to windows by default? (Keep in mind that he cannot see anything when he goes to the boot loader).

Thanks everyone! I look forward to ANY advice you provide.

---

### Post by dniMretsaM on 2012-05-15
You might try reinstalling GRUB. First, unplug all external storage devices. Then run this command and post the output here:
```
sudo fdisk -l
```Then someone will be able to tell you where to reinstall GRUB.

---

### Post by Grafeit on 2012-05-15
That looks like a DOS command, so I'd assume I am running that in the windows command line?

I'll do that and see what comes about. Thanks!

---

### Post by lukeiamyourfather on 2012-05-15
The command above is for reinstalling GRUB which is not what you want to do. If you want to get things back to the way they were before installing Ubuntu you'd want to reinstall the Windows bootloader. Search for it, there are many guides for doing exactly that.

---

### Post by Cythes on 2012-05-15
Its a linux command, sudo = superuser do (Windows don't use super user commands)

Also I am of no use here I just figured I would tell you now that way when you come back to say it don't work you will already have an answer. :) 

-Cheers And Good Luck :D

---

### Post by matt_symes on 2012-05-15
Hi

Do these links help ?

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

[http://www.sevenforums.com/performance-maintenance/51100-repair-cd-system-repair-disk.html](http://www.sevenforums.com/performance-maintenance/51100-repair-cd-system-repair-disk.html)

[http://www.helyar.net/2010/fix-windows-7-mbr-after-grub/](http://www.helyar.net/2010/fix-windows-7-mbr-after-grub/)

[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

Kind regards

---

### Post by dniMretsaM on 2012-05-15
> **Grafeit said:**
> That looks like a DOS command, so I'd assume I am running that in the windows command line?

I'll do that and see what comes about. Thanks!

It's a Linux command, sorry. Also, if you want to just completely remove Ubuntu (which is an over reaction to this small bootloader problem, in my opinion), you can reinstall the Windows bootloader and then remove the Ubuntu partition.

---

### Post by wilee-nilee on 2012-05-15
> **matt_symes said:**
> Hi

Do these links help ?

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

[http://www.sevenforums.com/performance-maintenance/51100-repair-cd-system-repair-disk.html](http://www.sevenforums.com/performance-maintenance/51100-repair-cd-system-repair-disk.html)

[http://www.helyar.net/2010/fix-windows-7-mbr-after-grub/](http://www.helyar.net/2010/fix-windows-7-mbr-after-grub/)

[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

Kind regards

+!

Thread starter the info you need is here, ask questions and we will get the computer booting windows alone, easy peasy. ;)

---

