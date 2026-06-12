---
title: "Windows after Ubuntu install?"
date: 2006-02-13
forum: Desktop Environments
---

### Post by majkmil on 2006-02-13
My family computer is a XP Pro machine. I know I know don't shoot. I have been using UBUNTU for about 4 months on another computer. This is my first real try with linux and I love it! My question is, I want to try one of the new builds of windows vista. Can I resize my ubuntu hard drive and install windows on the new partition and dual boot to both? I do not need to share files between the two OS's. This is only for a trial of vista but I don't have another hard drive to install on. I do not want to reinstall breezy because I have everything working great! If this is possible any help will be welcome. Thanks

---

### Post by mthaddon on 2006-02-13
Definitely not an authority on this one (haven't installed Windows on my own machine for a while :) ), but I would be very careful with this one. Unless MS has changed things significantly for Vista (unlikely), Windows won't place nice with other OSes on your computer. Most likely it will just charge ahead and overwrite the boot sector so that you can't see Linux at all. It'll still be there (assuming you work your partitions correctly), but you just won't be able to see it.

Now, there is most likely a way around this which involves creating a rescue disk in Linux, testing that it works correctly (i.e. that you can boot from it), and then going ahead with the Vista install, then using the rescue disk to boot back into Linux and have it reinstall GRUB, but I'm afraid I'm a little hazy on the specifics. Hopefully someone else can illuminate things here....

---

### Post by majkmil on 2006-02-13
Thnaks MTHADDON, I did not think it would be easy. I have read alot about installing ubuntu AFTER a windows install and about reinstalling grub.but I would'nt trust my skills without a lot of help maybe someone else might know something, Thanks again

---

### Post by majkmil on 2006-02-13
Just wanted to bring this back to the forefront.

---

### Post by kaamos on 2006-02-13
Have you seen this?

[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Ramses de Norre on 2006-02-13
You first need to make a boot diskette ```
dd if=/boot/grub/stage1 of=/dev/fd0 bs=512 count=1
``` ```
dd if=/boot/grub/stage2 of=/dev/fd0 bs=512 seek=1
```
Then after installing Windows boot from the diskette
```
grub
``` ```
install (hd0,1) /boot/grub/stage1 (hd0) (hd0,1) /boot/grub/stage2 p (hd0,4) /boot/grub/menu.conf
```
Grub is reinstalled:)

---

### Post by frodon on 2006-02-13
Other way to re-install GRUB : [http://www.ubuntuforums.org/showthread.php?t=76652](http://www.ubuntuforums.org/showthread.php?t=76652)

---

### Post by chettyk on 2006-02-13
I think your biggest problem is going to be that Windows has hitherto insisted on being loaded on the very first partition of the main drive. I assume that the first partition is currently occuppied by Ubuntu. If so, I suspect that you will have to install Vista on the first partition and then reinstall Ubuntu. Have a look at the article "Give Multiple Distros the Boot" that appeared in the Nov. 2005 issue (issue #8 ) of TUX. You can download the issue from:
[http://www.tuxmagazine.com/](http://www.tuxmagazine.com/)

---

