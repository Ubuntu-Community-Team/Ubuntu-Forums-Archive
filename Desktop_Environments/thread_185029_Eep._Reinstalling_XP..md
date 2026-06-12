---
title: "Eep. Reinstalling XP."
date: 2006-05-31
forum: Desktop Environments
---

### Post by InsanePenguin08 on 2006-05-31
I know, I know, I'm commiting a mortal sin by wanting to reinstall Windows XP.  Sorry guys!

So when I was installing Ubuntu, I had no clue what I was doing (too impatient to check the internet for directions!) and I erased my Windows partiton.  Now all of my harddrive is dedicated to Linux (with the exception of swap mem., of course). My question is, is there any way to make a new partition and reinstall XP without deleting my existing lovely Linux?  

Thanks!
InsanePenguin

---

### Post by jbrader on 2006-05-31
You can use gparted to repartition your disk but I don't think there's an easy way to install windows after linux is already installed and have the dual boot work properly. I'm probably wrong though ;)

---

### Post by jones_jj on 2006-05-31
There really is no easy way to install Windows after Linux has been installed.  MS likes everyone to think that their OS is the only one that people need and should use, that's why it is suggested that you install Windows and then install Linux second.  If you can find a way to partition your disks in such a way that Windows will be the first partition you may be able to install Windows and it will never know Linux is there.

---

### Post by Sef on 2006-05-31
After you install windows, follow these directions:

[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28grub%29%7C%28restore%29]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28grub%29%7C%28restore%29")

---

### Post by InsanePenguin08 on 2006-05-31
Oh geez.  I'm terrified.  I think I'll just wait until the end of senior year when my parents will buy me a new computer.

---

### Post by InsanePenguin08 on 2006-05-31
Hmm, stumbled on this [http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

Would I be able to use a similar technique to make a partition to install XP to?

---

### Post by nocturn on 2006-05-31
[QUOTE=jbrader]You can use gparted to repartition your disk but I don't think there's an easy way to install windows after linux is already installed and have the dual boot work properly. I'm probably wrong though ;)[/QUOTE]

The best recipe would be this:

1. Make room for Windows
2. Install windows on the free space
3. Windows will overwrite the MBR, so GRUB will not show at boot.  Use the LiveCD to recover Grub (see the wiki)
4. Add a grub entry for Windows
5. Done.

---

### Post by InsanePenguin08 on 2006-05-31
And this way will pose little threat to my Linux partition, I believe?

Thanks very much!

---

