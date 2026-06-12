---
title: "[SOLVED] Kernel update messes up with grub menu.lst"
date: 2008-07-16
forum: Desktop Environments
---

### Post by pentolino on 2008-07-16
Hello everyone,
I start by saying that I already know what to do when this situation arises, but I would be happy to have it solved once for all.
I use Ubuntu 7.10, all updated; I recently had two kernel updates (say in the last month). The update goes well but it changes menu.lst in a wrong way, resulting in an unbootable linux system after reboot.
The fact is simple, before kernel update menu.lst is configured to look for kernel images in 
(hd0,2)
after the update I found that it is modified to
(hd0,3) 
which of course results in an unbootable system.
I can avoid this by correcting menu.lst by hand after update, but is there a way to make update work correctly like it used to do before?
Thanks for any help,
Riccardo

---

### Post by Wolki on 2008-07-16
> **pentolino said:**
> 
The fact is simple, before kernel update menu.lst is configured to look for kernel images in 
(hd0,2)
after the update I found that it is modified to
(hd0,3) 
which of course results in an unbootable system.


Read the menu.lst: 

```

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

[some stuff left out]

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

```

Yes, the comments determine how the update-script edits the auto-configuration. Doesn't really make a lot of sense, but apparently it's neccesary so that everything can be in the same file.

So edit the singly commented line to the right device and it should work.

---

### Post by pentolino on 2008-07-16
thanks very much, I think you are right; the option you pointed out was directed to:
(hd0,3) (which is wrong)
I changed it to the right value; I just can't tell you for sure if it works, have to wait next kernel update :-)
Thanks for your help.
Bye

---

