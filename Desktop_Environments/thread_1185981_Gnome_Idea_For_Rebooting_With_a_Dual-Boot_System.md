---
title: "Gnome Idea For Rebooting With a Dual-Boot System"
date: 2009-06-12
forum: Desktop Environments
---

### Post by kaoskorruption on 2009-06-12
Hey, here's an idea:

What if when you went to the restart option in Gnome, it looked at grub's menu.lst and asked you which OS you wanted to boot back into? Perhaps it could put a flag or something on grub or the bios (I don't really know how grub/boot menus work). This would make it so you don't have to stare attentively at the screen if you want to reboot into another OS waiting for the menu to show up so that you can quickly press the down arrow to select it before it automatically boots into the default OS. Maybe instead you could grab a coffee.

---

### Post by bolweval on 2009-06-12
That would be very cool.

---

### Post by lidex on 2009-06-13
Already done. It's called "grub-choose-default". Available in Ubuntu universe repository. Web page:
[http://digamma.cs.unm.edu/trac.dmohr/wiki/GrubChooseDefault]("http://digamma.cs.unm.edu/trac.dmohr/wiki/GrubChooseDefault")

---

### Post by lidex on 2009-06-13
Don't forget if you are having issues with not enough time to select option in grub menu you can change the timeout value in "boot/grub/menu.lst"```
sudo gedit boot/grub/menu.lst
```

Scroll down to the section labeled "## timeout sec" and change the integer value to desired timeout in seconds. Save and reboot.

---

### Post by kaoskorruption on 2009-06-16
Perhaps grub-choose-default could be implemented into the shutdown menu in Gnome/Ubuntu.

---

