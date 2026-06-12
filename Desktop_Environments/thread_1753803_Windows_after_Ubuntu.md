---
title: "Windows after Ubuntu"
date: 2011-05-09
forum: Desktop Environments
---

### Post by raphaelsaldanha on 2011-05-09
Hi folks,

I have just installed Ubuntu 11.04 on my notebook (Dell Vostro 1310), deleting all partitions and, thanks God, Windows Vista.

But unfortunately, some softwares that I need don't worked well on Wine (Adobe Audition and others).

So, I need to reinstall Windows on my machine, leaving Ubuntu as major OS, and Windows for these applications.

Which is the best way to create a partition and install Windows (probably W7)?

I have read [this guide]("https://help.ubuntu.com/community/WindowsDualBoot#Installing Windows After Ubuntu"), but I'm not sure yet...

Thanks in advance!

---

### Post by manzdagratiano on 2011-05-09
This method in the link is foolproof.

1) Install Windows - it will delete your grub
2) Boot from LiveCD
3) Check which partition is which by running:
```
sudo fdisk -l
```
4) Mount /
5) Mount /boot into /
6) Run:

sudo grub-install --root-directory=<path/to/mounted/root> /dev/sdX

You're all set!

Look here if need be:
[URL="https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD"]
https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD[/URL]

---

### Post by raphaelsaldanha on 2011-05-09
Hi!

Thanks for the explanation. This install of Windows will delete my Ubuntu installation, or Windows will ask for create another partition and etc?

---

### Post by manzdagratiano on 2011-05-15
I am sorry for the late reply, but in case the question is still open for you, the Windows install will **not** delete the Ubuntu install unless you tell it to. You should be able to create another partition from it, but I would suggest creating a separate partition for Windows by using GParted within Ubuntu. Then, install Windows in that partition - it will delete your grub, which may be fixed by following the steps above.

---

### Post by Supergoo on 2011-05-15
Easier was to handle this is use Virtualbox- and run windows in VM. Just a Idea

---

### Post by wildmanne39 on 2011-05-16
> **raphaelsaldanha said:**
> Hi folks,

I have just installed Ubuntu 11.04 on my notebook (Dell Vostro 1310), deleting all partitions and, thanks God, Windows Vista.

But unfortunately, some softwares that I need don't worked well on Wine (Adobe Audition and others).

So, I need to reinstall Windows on my machine, leaving Ubuntu as major OS, and Windows for these applications.

Which is the best way to create a partition and install Windows (probably W7)?

I have read [this guide]("https://help.ubuntu.com/community/WindowsDualBoot#Installing Windows After Ubuntu"), but I'm not sure yet...

Thanks in advance!

Hi, I also am recommending virtualbox,it great except for playing games.:)

---

