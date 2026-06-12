---
title: "Kernel 2.6.27-14 issue *not showing in grub*"
date: 2009-05-13
forum: General Help
---

### Post by iavor on 2009-05-13
Hi guys, my issue is that i cant see the my new kernel in grub, it shows only my current 2.6.27-11-generic and windows not counting memtest and recovery. I've tried installing KGrubEditor because i googled around and i saw a thread here with guy who had the same problem, but he resolved it with the KGrubEditor.. i didn't have the same result, i've also tried update-grub and nothing happened.. so i decided to post a thread. Thanks in advance

---

### Post by WIGGMPk on 2009-05-13
Could you post the output of:

```
sudo update-grub
```

Are you using gfxboot grub? How was the new kernel installed, via update manager or did you compile it yourself?

---

### Post by iavor on 2009-05-13
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-14-generic
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

nope i dont have gfxboot i installed it via the update manager

---

### Post by WIGGMPk on 2009-05-13
Can you open up your menu.lst and paste it in here..

```
gedit /boot/grub/menu.lst
```

You can also try this after your done posting your menu.lst, back it up and have the update-grub script create a new one like so:

```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.backup
```
than do this:
```
sudo update-grub
```

reboot your computer and see if the grub menu was updated properly.

---

### Post by iavor on 2009-05-14
ok i did it.. it show up the new kernel but when i boot it i got this screen
[[IMG]http://img24.imageshack.us/img24/2963/14052009469.th.jpg[/IMG]](http://img24.imageshack.us/my.php?image=14052009469.jpg)

---

### Post by WIGGMPk on 2009-05-14
What video card do you have?
What drivers were you using?


If you were using nvidia drivers from nvidia, you will have to reinstall them for the new kernel. If you were using drivers from restricted-drivers-manager than it should of did this automatically.

For the life of me I cannot remember how to reconfigure the x server to use the open source drivers.. But when you boot up, select the recovery option for that kernel.

I believe you can just open xorg.conf:

```
nano /etc/X11/xorg.conf
```

Navigate to the section that identifies your video card, there will be a line like this:

```
Driver         nvidia
```

Change it to "nv".

Hopefully someone else reads this post because im almost certain there a script that can reconfigure xorg.

---

### Post by iavor on 2009-05-14
ATi Radeon card to be exact 4850
and i manualy installed 9.4 on 2.6.27-11 weeks before..
i reformated today just to be sure.. and again it gave me the same screen on 2.6.27-14 i appreciate your help

---

### Post by iavor on 2009-05-16
nvm i reformated again.... i did update my kernel first.. and then i rushed into installing ati drivers and stuff.. and now its all ok thanks for the help anyway

---

