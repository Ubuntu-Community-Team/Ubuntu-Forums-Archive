---
title: "Changing grub, not sure if I'm doing it right"
date: 2008-12-03
forum: General Help
---

### Post by munit5000 on 2008-12-03
Here is what the grub menu originally is:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

And I want to make sure the first one doesn't show up, so how would I comment that out using hiddenmenu code (so the option shows up when I press esc):

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

Also is there any way to change the color of an item to orange?

---

### Post by giuspen on 2008-12-03
> **munit5000 said:**
> Here is what the grub menu originally is:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

And I want to make sure the first one doesn't show up, so how would I comment that out using hiddenmenu code (so the option shows up when I press esc):

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

Also is there any way to change the color of an item to orange?

install this:
[http://open.vitaminap.it/en/linux_configuration.htm#stupm]("http://open.vitaminap.it/en/linux_configuration.htm#stupm")
regards.

---

### Post by caljohnsmith on 2008-12-03
To my knowledge you can't comment out a single entry in the Grub menu.lst and have it show up by pressing ESC on start up; you can hide the entire Grub menu on start up by removing the pound sign in front of the "#hiddenmenu" line, and that way you have to press ESC to get the Grub menu. Or another trick you can do is create a "sub-menu" in Grub where if you select it, it will take you to those two Windows options. In other words, you can add something like:
```
title Windows Sub-Menu
configfile (hdX,Y)/boot/grub/menu2.lst
```
Where (hdX,Y) is your Ubuntu partition, and the menu2.lst file contains just your two Windows Grub entries.

---

### Post by Sealbhach on 2008-12-03
You can just delete those lines if you want, if you think you won't need them again.


.

---

