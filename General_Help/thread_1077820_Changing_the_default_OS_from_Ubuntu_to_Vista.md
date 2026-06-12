---
title: "Changing the default OS from Ubuntu to Vista"
date: 2009-02-22
forum: General Help
---

### Post by funnyb0nes on 2009-02-22
Hi,

I have recently installed Ubuntu as a secondary operating system on my laptop (it's working fine so far!). My only problem is that Ubuntu comes first on the boot list when I switch the laptop on and I would prefer the computer to boot into Vista automatically. 

I have tried following the advice of others to change the 0 in the line "default=0" within the menu.bat file but when I try to save the file after changing the "0" to a "4", I cannot save the change because I "do not have sufficient access privileges". Why does this happen even if I have the only user account on the computer?

Help would be much appreciated! Thanks!

---

### Post by RedSingularity on 2009-02-22
Change the file by going into it with Root privileges.  Type in terminal "sudo nautilus" without the quotes.  This will bring you to the file system explorer and you can edit and save from there.

---

### Post by ibuclaw on 2009-02-22
Or how about:
```
sudo gedit /boot/grub/menu.lst
```
and **NOT** put the system in jeopardy. :)

Regards
Iain

---

### Post by Lithical on 2009-02-22
Fool-proof way of editing default GRUB OS if you're unsure is:

System > Administration > Synaptic Package Manager

Search "KGRUBEditor"

After installing and booting that up just click the radio box next to your Windows OS entry.

---

### Post by schnauzer93 on 2009-02-22
Or you could just re-arrange your GRUB menu so that Vista is at the top.

---

### Post by RedSingularity on 2009-02-22
> **schnauzer93 said:**
> Or you could just re-arrange your GRUB menu so that Vista is at the top.

I think thats what he is trying to do but without sudo privileges you cannot save the file you edit.

---

### Post by funnyb0nes on 2009-02-23
Good effort guys. Typing that into the terminal did the trick.

Thanks very much.

---

