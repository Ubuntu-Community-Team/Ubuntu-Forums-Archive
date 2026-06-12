---
title: "Anoying Windows Boot Manager"
date: 2009-02-21
forum: General Help
---

### Post by compnut41 on 2009-02-21
I just installed windows 7 beta version. It is nice but it installed this windows boot manager that only allows me to boot vista or Win 7, and frankly I like grubs a lot better. Does anybody know how I can get grubs back, then configure grubs so vista is out of the other partition slot and windows 7 is there because right now the list does not include it.

 --thanks in advance

---

### Post by Leaf on 2009-02-21
I too installed win7beta, after I had installed 2 XP partitions, and an Ubuntu partition.

Win7beta, in all of its wisdom, *carved* a chunk out of my first windows install, ruining it and my GRUB booter, just so it could have the first partition on the drive.

My advice, install win7 first, then XP, then Ubuntu.  

To answer your question this thread might help, it explains how to install grub from a LiveCD.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by caljohnsmith on 2009-02-21
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and what it might take to reinstall Grub and boot both your Windows OSes from Grub.

---

