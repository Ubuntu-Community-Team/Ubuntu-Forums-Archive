---
title: "Simple GRUB question"
date: 2006-09-25
forum: Desktop Environments
---

### Post by zuccs on 2006-09-25
hey all,

I had grub setup perfectly running Ubuntu/XP and I have updated my Ubuntu (via: sudo apt-get install linux-686-smp) and this has erased my previous GRUB list and I can no longer select windows.

Can someone provide me with the template to add windows back into the menu.lst file?

Also, I was told that by installing 686-smp that it is a lot faster and won't lag when scrolling down websites, but this is also not available in the GRUB menu.lst file. How can I add this linux kernal to the grub list? I think I am just currently using the same version as I was previously.

Thanks for all your help!

---

### Post by gilgongo on 2006-09-25
I've got the following in my menu.lst, right at the bottom of the file, after all the Linux kernel stuff:

> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


I suppose the "root" line will depend on where your Windows partition actually is.

---

### Post by zuccs on 2006-09-25
Ok, thanks champ, that's what I needed for the first part.

Now does anyone know how to add in a line to boot linux-686-smp? It currently only has the same version I was already using.

---

### Post by dyrer on 2006-09-25
How can make Windows starts first?

---

### Post by ponzio on 2006-09-25
> title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

add the "microsoft windows whatever you want there" above the automagic kernel list, as seen above.

---

