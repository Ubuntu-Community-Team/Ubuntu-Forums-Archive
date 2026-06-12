---
title: "Disabling or customizing the Send To menu"
date: 2008-08-25
forum: Desktop Environments
---

### Post by lsutiger on 2008-08-25
When you right click on a file in Gnome, you get a Send To option. Is there a way to either disable/remove/edit this option.

I googled a lot and found a ton of answer for windows but nothing for ubuntu or gnome.

Thanx a bunch!

---

### Post by 4leite on 2008-11-17
*bump

Also unable to find anything

---

### Post by lsutiger on 2008-11-18
I ended up just renaming the program tat is responsible for that function. It still shows up as an option, but no action is taken.```
mv /usr/bin/nautilus-sendto /usr/bin/nautilus-sendto.bak
```

---

### Post by shjohnson12 on 2009-04-09
To uninstall the send-to menu you can run this in the terminal:

```
sudo apt-get remove nautilus-sendto
```

Hope this helps! :)

---

### Post by John Mukulu on 2009-09-09
I wonder if there is  a send to pluggin detects removable drives like flash disks,
I think it'll be more fun to have a extends ways of transfering files from place to place within the same hard drive

---

