---
title: "Wubi help!"
date: 2009-01-07
forum: General Help
---

### Post by kevinn on 2009-01-07
Hi there,

I have some problems with installing ubuntu beside windows.
So when I start Wubi, it does al the normal things (download ubuntu iso etc.). But then it asks me to reboot. I reboot my system and I go to ubuntu insteed of windows xp. 
Then comes the creepy thing. A totaly black screen with this text:

```
Loading. please wait...

Busybox v 1.10.2 (Ubuntu 1:1.10.2-lubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(imitranfs)_
```

I tried to enter 'help' but the only thing I get is the list of availble commands. So I don't know what to do. somebody does?

Kevinn

---

### Post by namdung on 2009-01-07
1. Edit c:\ubuntu\disks\boot\grub\menu.lst
2. Replace "quiet splash" with "all_generic_ide"
3. Reboot
4. Install Ubuntu!

---

### Post by kevinn on 2009-01-07
The folder grub is empty on my computer.
Maybe i'll have to install the whole thing?

But in the winboot folder is a file called menu.lst. Do I need to edit this file?
EDIT: but in that file there isn't somthing like 'quiet splash'

---

### Post by kevinn on 2009-01-07
In the folder C:\ubuntu\install\boot\grub there is an file called menu.lst. Do you mean this file?

---

### Post by namdung on 2009-01-07
Try copying that file *menu.lst* to 
c:\ubuntu\disks\boot\grub\menu.lst

The following should help
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by kevinn on 2009-01-07
And now there are several lines rolling over the screen. So i think he's loading things and al of a suddens the laptop completly shutsdown. Screen black and he's out. He keeps doing that when I reboot into ubuntu.

Any advise?

---

### Post by Orlsend on 2009-01-08
Normally busybox means that was a bad shutdown or theres some errors on the hardrive.

I am not sure my way fixing this will work now.

---

