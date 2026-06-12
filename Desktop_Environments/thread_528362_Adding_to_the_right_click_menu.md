---
title: "Adding to the right click menu"
date: 2007-08-17
forum: Desktop Environments
---

### Post by Atsuko on 2007-08-17
I took xandros out and install ubuntu and now I'm upgrading to ubuntu 7.04.
I had seen in the right click menu how if you click on a file or something like that you could open it in a root file manager and just enter the root password and then work from it.
Same with the text file, could open it in the root kate and then edit the file in root mode.
How can I add this to the context menu? :confused:
Thanks for the help.
looks like I have about five hours for the update to finish.

---

### Post by angryfirelord on 2007-08-18
I do it through the terminal:
```
gksudo nautilus
```
That will give you root powers for your file manager. However, it's advisable that you only run it when you absolutely have to (like editing a conf file).

I don't know how to make a menu entry for it though (other than the gnome menu).

---

### Post by Atsuko on 2007-08-18
Thanks.

---

### Post by zero-9376 on 2007-08-18
You may want to install the package nautilus-gksu which adds a right click option "Open as Administrator" which works with both files and folders. I believe what you were originally talking about was nautilus scripts, which I used to install though automatix, but nautilus-gksu and nautilus-open-terminal provide all the functionality i need. there is also an image converter which may be useful, just search for nautilus in synaptic and have a look.

---

### Post by Atsuko on 2007-08-18
Thanks zero-9376, Ill have a look at that when it gets done here with the upgrade.

---

