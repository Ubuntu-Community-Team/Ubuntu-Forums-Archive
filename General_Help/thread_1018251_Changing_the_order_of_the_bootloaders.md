---
title: "Changing the order of the bootloaders"
date: 2008-12-21
forum: General Help
---

### Post by 123456789mike on 2008-12-21
Well, Wehn I turn on my computer, the GRUB bootloader comes up first, I was hoping I could return it to Windows Boot Manager first, and so the Ubuntu option leeds to the GRUB bootloader

Well, just any way so that if I turn on my computer it will load XP instead of ubuntu, instead of my having to select Longhorn>Older version>Older version...

Well, thanks, I am pretty much just asking how to swap the order of GRUB and Windows Boot Manager

---

### Post by 73ckn797 on 2008-12-21
> **123456789mike said:**
> Well, Wehn I turn on my computer, the GRUB bootloader comes up first, I was hoping I could return it to Windows Boot Manager first, and so the Ubuntu option leeds to the GRUB bootloader

Well, just any way so that if I turn on my computer it will load XP instead of ubuntu, instead of my having to select Longhorn>Older version>Older version...

Well, thanks, I am pretty much just asking how to swap the order of GRUB and Windows Boot Manager

I have never done what you are wanting but I have edited grub to boot one drive by default. All I did was swap relevant grub info. Example: 64 bit was second in order with 32 bit version first. By copying one to a position ahead of the other and moving the other to a secondary position I was able to accomplish that. I do not know whether moving the Windows selection to the top of the list would work but I would try that first. I would back up the menu.lst just in case it messed things up.

I am sure there is another way to do what you want so, hopefully, someone will add their comments. I am just the kind that would try what seems like it would work. It might mess things up but it could be reversed.

---

### Post by caljohnsmith on 2008-12-22
Are you using Ubuntu installed inside Windows via Wubi? Or did you do a normal install and give Ubuntu its own partition? In order to get a clearer picture of your setup, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

---

### Post by 123456789mike on 2008-12-22
I will try 73ckn797's idea later, hopefully all goes well, if not I will reverse and try your idea,caljohnsmith.

---

### Post by 73ckn797 on 2008-12-22
> **123456789mike said:**
> I will try 73ckn797's idea later, hopefully all goes well, if not I will reverse and try your idea,caljohnsmith.


I assume all went well?

---

### Post by 123456789mike on 2008-12-23
Well, I am quite confused on changing the orders of different things. Here is what my computer looks like on start-up(I am sure your's does as well):
[IMG]http://i44.tinypic.com/2w49t6s.jpg[/IMG]
I just want to make it so that the bottom choice is at the top... When I click 'e' on the bottom choice, (Longhorn/loader), these are my options:

root(hd0, 0)
savedefault
makeactive
chainloader

---

### Post by TeXtonyx on 2008-12-23
[http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/)

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system. 
default 0 <--- That is the number you change to the Windows number (menu.lst)

---

### Post by 73ckn797 on 2008-12-23
> **TeXtonyx said:**
> [http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/)

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system. 
default 0 <--- That is the number you change to the Windows number (menu.lst)


I was not aware of this, Thanks!

---

### Post by 123456789mike on 2008-12-23
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0<------------------
You are certain that I change the 0^ to 4, without any errors? I really don't want a non-booting computer ;)

---

### Post by 123456789mike on 2008-12-24
Any help...?

---

### Post by caljohnsmith on 2008-12-24
From the screen shot you gave in post #6, it shows Vista being the 7th entry in the Grub menu, so if you change your default line to "default 6", then you should by default boot Windows. Or if you want, you can move Vista to the top of of the Grub menu (before the Ubuntu entries), and then leave the default line as "default 0". Either way, you can edit your menu.lst by first opening a terminal (Applications > Accessories > Terminal) and doing:
```
gksudo gedit /boot/grub/menu.lst
```
And then if you want to move Vista to the top of the Grub menu, just move Vista entry to be directly above the "AUTOMAGIC" lines in the menu.lst, so that particular section of your menu.lst looks like:
```

title Windows Vista 
root (hd0,0)
savedefault
makeactive
chainloader +1

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
```
If you move Vista above Ubuntu, you won't need the "Other Operating Systems" divider, so you can delete the two lines at the bottom of your menu.lst that say:
```
title Other Operating Systems
root
```
And then you should be all set. Let us know how it goes.

---

### Post by 123456789mike on 2008-12-24
All went well, thanks a ton!

---

