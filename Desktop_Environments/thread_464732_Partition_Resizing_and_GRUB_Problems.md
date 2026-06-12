---
title: "Partition Resizing and GRUB Problems"
date: 2007-06-05
forum: Desktop Environments
---

### Post by DeathOnJuice on 2007-06-05
Hey, everyone. I currently run Ubuntu on an ext3 filesystem, but I want to run MythTV. I've decided to create either an additional Ubuntu install with an XFS or JFS filesystem or a KnoppMyth install. (As a side question, can anybody tell me which would be a better choice?)

The only problem is, I need to resize my NTFS Windows XP partition to get this to work. I know I can use GParted, but are there any precautions I should take other than defragging and backing up my data?

The other problem is adding this new install to GRUB. The Ubuntu install always seems to make a perfect GRUB menu. However, I can foresee three issues. One is that I wouldn't be able to tell the two Ubuntu installs apart. I could just edit the names in menu.lst, right? The second is that I don't know where I would store GRUB; I know that some of it goes in the MBR, but I also have a /boot/grub and I don't know what partition to put this on. I really don't get how that works. Finally, the one time I overwrote GRUB with the Windows bootloader, I could NOT set it back up inside Ubuntu or with the LiveCD. Although it seemed to know how to do it during the install, I was getting errors left and right when Ubuntu was already installed and I ended up reinstalling. Besides, I'm not sure KnoppMyth will work as well. In case of problems, could someone give me a good GRUB guide? I have a SATA hard drive.

Thanks so much!

---

### Post by majed on 2007-06-05
Hi,

I have resized my Windowz XP NTFS partition more than once with GParted and it worked just fine. However, you might want to backup your important data before such an activity, just in case! I also have to say that I used the INSERT liveCD to do that. [http://www.inside-security.de/insert_en.html]("http://www.inside-security.de/insert_en.html")

Answering your other questions:

Yes, you can edit the names in menu.lst.

I put GRUB in its own little partition. This way, it is completely indeendent of any OS install. This guide can help for starters: [http://www.troubleshooters.com/linux/grub/grubpartition.htm]("http://www.troubleshooters.com/linux/grub/grubpartition.htm")

You can mostly always restore GRUB. A reinstall of a whole distro is not needed to be yourself back into business. Here is more info but read the whole thread before deciding what you would do: [http://ubuntuforums.org/showthread.php?p=117829#post117829]("http://ubuntuforums.org/showthread.php?p=117829#post117829")

Good luck!

Majed

---

