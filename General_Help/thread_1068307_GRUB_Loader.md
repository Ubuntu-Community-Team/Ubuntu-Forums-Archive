---
title: "GRUB Loader"
date: 2009-02-12
forum: General Help
---

### Post by CraigBray on 2009-02-12
Can i make the grub automatically load my Windows Vista partition on default?

---

### Post by lordrick112 on 2009-02-12
Install StartUp-Manager.

Under Boot Options you can change your default OS.

sudo apt-get install startupmanager

---

### Post by CraigBray on 2009-02-12
Thank you! :)

---

### Post by e1mer on 2009-02-12
It seems a little heavy handed to use a program to do what you can do with
vi.

```
sudo vi /boot/grub/menu.1st
```
and change the line that says default 0
to read default 1
(or whatever number corresponds to your windows installation after that.)
(count the title sections.)

---

### Post by CraigBray on 2009-02-18
Oh, thanks, an even easier solution! Thank you. :D

---

### Post by CraigBray on 2009-03-11
Worked, added question to this, can i change the order of how they display? for example, have Vista Longhorn at the top, Ubuntu regular in second, then maybe adunno (for educatonal purposes) SUSE at number 3, then put the the ubuntu memtest under that, then the two recovery modes. (I don't know if suse has a recovery and memtest function in the grub.)

---

### Post by lindsay7 on 2009-03-11
Just edit the menu1st file (gedit) You will see the os's and memtest listed in the order the appear on the screen at startup. Change the list order to the way you want it to show up.

Here is the info from another post.

Rallg 
Way Too Much Ubuntu

 
Join Date: Mar 2008
Posts: 270 
Hardy Heron (Ubuntu Development) 	Re: dual boot startup default 
From within Ubuntu, open a Terminal. then:

sudo gedit /boot/grub/menu.lst

This is the file containing the boot order. Any line begiining with a hash (#) is a comment.

Towards the bottom, you will see the Windows boot instructions. Cut and past so that those instructions precede the boot instructions for your ubuntu. I don't mean put them at the top of the file, I mean relative to the other boot instructions.

Just keep in mind that there are several "sample" boot instructions, commented out.

Save the file, then you can reboot.

What if you made a terrible mistake, and bungled the editing? All is not lost. You can edit that file using something such as a live Linux distribution on a USB stick. Just keep in mind that you need to edit the menu.lst file on your hard drive, not the one within the live Linux distro.

---

### Post by CraigBray on 2009-03-11
Thank you :)

---

### Post by manojks on 2009-03-14
This was really useful. Thanks.

---

