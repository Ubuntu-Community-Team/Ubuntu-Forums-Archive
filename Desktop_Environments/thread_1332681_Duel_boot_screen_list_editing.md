---
title: "Duel boot screen list editing"
date: 2009-11-20
forum: Desktop Environments
---

### Post by NoonienSoong97 on 2009-11-20
Hi,

I was wondering if there would be complications if I tried to edit out the previous installations on the list at the duel boot screen.

I would be using this line of code gksudo "gnome-open %u" as an application launcher so I can just drag and drop to edit admin files. I have used it before to change the time on the duel boot screen. I just want to be sure if I can just edit out the links to the previous installations of ubuntu without causing any problems to the system?

---

### Post by oldfred on 2009-11-20
Rather than have gnome I open a file with right click, open with other application and use custom command of gksudo gedit. After the first time it then becomes a choice under open with other application and no typing is required.
The danger of having the entire gnome under root is that you may convert, modify other things that then only open with root.
What file are you editing? menu.lst?

---

### Post by NoonienSoong97 on 2009-11-20
Yea menu.lst is what I will be editing. I just want to keep the duel boot menu down to like three options the latest updated ubuntu, safe mode option for ubuntu, and WinXP.

---

### Post by oldfred on 2009-11-20
If you find this entry in menu.lst and change the qty to two as I have you will only see two version of Ubuntu in the updated menu.lst. One # is a parameter used to modify the update, two # are true comments. The kernels do not take a lot of space so you do not have to regularly delete them. 

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=2

run this to rewrite the automagic area with only two entries per parameter. Is automatally run on any new kernel or deletion of kernel.
sudo update-grub

---

### Post by NoonienSoong97 on 2009-11-21
Thanks. I have changed the value, and updated the grub. Will be restarting to check it.

---

