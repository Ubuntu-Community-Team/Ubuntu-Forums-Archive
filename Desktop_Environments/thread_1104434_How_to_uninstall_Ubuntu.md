---
title: "How to uninstall Ubuntu?"
date: 2009-03-23
forum: Desktop Environments
---

### Post by JoeyF on 2009-03-23
I recently dual booted Ubuntu with my WinXP, But i want to go back, I found some tutorials, But the problem is, I don't have an XP disk, It came preinstalled.
How can i uninstall Ubuntu and the ubuntu boot loader?

---

### Post by Froodolt on 2009-03-23
If I understand correctly, you made a dual-boot system (XP Ubuntu) and want to get rid of Ubuntu.
To [remove the Grub boot-loader]("http://ubuntuforums.org/showthread.php?p=1518589") you can (according to this threat) use synaptics to remove the package.
If you have partitioned your disk (XP and Ubuntu on the same disk), I would use [GParted]("http://gparted.sourceforge.net/") to format the Ubuntu part and resize the windows part back to 100% disksize.

Anybody better idea's?

---

### Post by Aflack on 2009-03-23
Nope. I did that and it worked great for me. :popcorn:

---

### Post by JoeyF on 2009-03-23
> **Froodolt said:**
> If I understand correctly, you made a dual-boot system (XP Ubuntu) and want to get rid of Ubuntu.
To [remove the Grub boot-loader]("http://ubuntuforums.org/showthread.php?p=1518589") you can (according to this threat) use synaptics to remove the package.
If you have partitioned your disk (XP and Ubuntu on the same disk), I would use [GParted]("http://gparted.sourceforge.net/") to format the Ubuntu part and resize the windows part back to 100% disksize.

Anybody better idea's?

Thank you, I'll try it later:D

---

### Post by ajgreeny on 2009-03-23
Your main problem is that without a windows CD you will need to restore the original windows MBR somehow, or grub will remain and point to the ubuntu partition for the grub menu.lst file, which will not be there any longer.  You can download a utility to do this from various sources on the net, which I cant find at the moment, or you can try this method below:-

RESTORE WINDOWS MBR FROM UBUNTU LIVE CD

You can install a Windows equivalent MBR to your sda drive by doing the following from your Live CD:
Code:

sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr

Then you should be able to boot directly into Windows again if all goes well. Let me know how it goes or if you run into problems.

---

### Post by JoeyF on 2009-03-23
> **ajgreeny said:**
> Your main problem is that without a windows CD you will need to restore the original windows MBR somehow, or grub will remain and point to the ubuntu partition for the grub menu.lst file, which will not be there any longer.  You can download a utility to do this from various sources on the net, which I cant find at the moment, or you can try this method below:-

RESTORE WINDOWS MBR FROM UBUNTU LIVE CD

You can install a Windows equivalent MBR to your sda drive by doing the following from your Live CD:
Code:

sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr

Then you should be able to boot directly into Windows again if all goes well. Let me know how it goes or if you run into problems.
That just removes grub-Right?, If so. Can i use the above poster's instructions to remove Ubuntu?. If so,
How?
Thanks.
:)

---

### Post by ajgreeny on 2009-03-24
> **JoeyF said:**
> That just removes grub-Right?, If so. Can i use the above poster's instructions to remove Ubuntu?. If so,
How?
Thanks.
:)
Yes it removes grub and replaces it with the original windows MBR.  You can now use gparted on the ubuntu live CD to delete the ubuntu partitions, and either add them to the windows ntfs partition, again with gparted, simply be resizing the windows partition to the full size, or you can just reformat the ubuntu partition(s) as one or more ntfs partitions and use them as data storage, when they will probably show in win explorer as drive D:\, and E:\ if more than one is kept.

---

