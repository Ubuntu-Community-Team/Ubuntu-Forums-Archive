---
title: "Changing order of boot"
date: 2009-02-02
forum: General Help
---

### Post by CactusBodyslam on 2009-02-02
Hi, I recently installed Ubuntu 8.10 on my computer and I am trying to change the order on the list of installed operating systems. Right now it has a bunch of Ubuntu stuff at the top and Windows Vista at the bottom. I want to move Vista to the top so it loads that one by default.

---

### Post by taurus on 2009-02-02
Just edit /boot/grub/menu.lst

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
and change the **default 0** to whichever number your windows is located.  Remember, each title is counted as one and you start counting from 0.

Save it and reboot.

---

### Post by ChildOfMana on 2009-02-02
Open a Terminal (Applications > Accessories > Terminal) and type;

```
sudo gedit /boot/grub/menu.lst
```

Find the line that says default=0 and change the 0 to the number of the line that corresponds with your Windows entry.

Remeber that the numbering starts from 0, so (for example) if your Windows entry is the 4th one in the list you will need to set it to default=3.

This won't put Windows at the top of the list but it will automatically highlight it, and boot it as the default OS if no button is pressed within the time limit.

Hope this helps.

Edit: taurus beat me to it :)

---

### Post by CactusBodyslam on 2009-02-02
I typed in what you suggested but it opened a blank document, so I went to the file specified, opened it, and tried to edit it but it says I don't have the proper permissions to edit it.
Edit: I see, it was .lst and not .1st, works perfectly thanks a bunch.

---

### Post by ChildOfMana on 2009-02-02
You wont have permission to edit the file if you just navigate to it in nautilus as it's owned by root. That's why you need the *sudo* part of the Terminal command - to give you temporary root permission. You should be able to view it though.

Are you sure you typed the command correctly? Try copying and pasting it.

Edit: Just noticed your edit... man, I'm slow tonight!! Glad you got it sorted :)

---

