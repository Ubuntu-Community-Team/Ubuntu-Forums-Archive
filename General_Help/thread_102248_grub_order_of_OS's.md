---
title: "grub order of OS's"
date: 2005-12-11
forum: General Help
---

### Post by Hube on 2005-12-11
Hi Folks,

Quick background, the machine I'm using is primarily my wifes, she uses XP, so I dual boot the machine so I can play around with Linux.  I use the wifes machine to test out distros before installing on to a server.

I'm moving over from Fedora Core 4 and would like to maintain a few of the niceities that I have observed in that distro.  I'm used to editing /etc/grub.conf so I created a symbolic link from /etc to /boot/grub using the following:

ln -s /boot/grub/menu.lst /etc/grub.conf

Now looking through menu.lst I see that XP has been added at the bottom of the file, I know I can play with the default to set XP as the default boot OS but what I really want to do is move the windows boot above ### BEGIN AUTOMAGIC KERNELS LIST so that it is always "default=0" and the first choice when the grub menu displays.  I'm also aware that I could put the XP stuff in the AUTOMATIC area but loosing the settinsg every time the kernel gets upgraded doesn't strike me as a good solution...

With Fedora this is completely OK, my question, can I do this with Ubuntu?

So far I'm really liking what I see :-)

Thanks, Hube

---

### Post by aysiu on 2005-12-11
[QUOTE=Hube]
With Fedora this is completely OK, my question, can I do this with Ubuntu?[/QUOTE] Yes. It's fine.

---

### Post by mherring on 2005-12-11
You don't have to move anything around in the menu.lst---just set default equal to the number that you want to be the default.
the behavior of grub should be independent of the distro (as long as the menu.lst file is correct)

---

### Post by Hube on 2005-12-11
OK, Thanks.

Didn't want to make the change and end of breaking the boot loader, been there before!

---

### Post by aysiu on 2005-12-11
[QUOTE=Hube]OK, Thanks.

Didn't want to make the change and end of breaking the boot loader, been there before![/QUOTE] You won't break the bootloader if you mess up. I would do a ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
``` and make sure you have a live CD handy (something like Knoppix). With a live CD, you can easily restore your old configuration.

---

### Post by Hube on 2005-12-11
[QUOTE=mherring]You don't have to move anything around in the menu.lst---just set default equal to the number that you want to be the default.
the behavior of grub should be independent of the distro (as long as the menu.lst file is correct)[/QUOTE]

Yes, but I wanted XP to be at the top so as not to freak the missus out!

Also, If you get a new kernel (via apt-get) and say there are 6 kernel options rather than 4 and XP was originally default=4, would it shift to default=6?

---

### Post by Hube on 2005-12-11
[QUOTE=aysiu]You won't break the bootloader if you mess up. I would do a ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
``` and make sure you have a live CD handy (something like Knoppix). With a live CD, you can easily restore your old configuration.[/QUOTE]

Yeah, got the backup before I did anything...

---

