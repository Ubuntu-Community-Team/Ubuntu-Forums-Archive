---
title: "Menus for Evince/Document Viewer"
date: 2016-06-08
forum: Desktop Environments
---

### Post by rwigle on 2016-06-08
On one of my Ubuntu 14.04 systems, Evince has a "File Edit View" type of menu at the top. On the other I see various icons (the one on the far right has a dropdown menu).

I prefer the latter setup. What do I need to change to get that behaviour? Thanks in advance.

---

### Post by vasa1 on 2016-06-08
Run ```
apt-cache policy evince
``` and
```
lsb_release -a
```
on both computers.

It's possible that you have a more recent version of evince on the one showing "various icons (the one on the far right has a dropdown menu)."

---

### Post by rwigle on 2016-07-03
I ran the suggested commands and the results on the two machines are the same.

It would be nice to use the later version on both machines, but it isn't essential.

P.S. Thanks for your help and sorry for delay in responding. Other troubles .......

---

### Post by rwigle on 2016-08-01
At some point I installed a package (on the machine that now has the newer evince) which loaded some KDE packages. Is it possible that one of those packages could somehow have triggered the newer version of evince to be installed?

---

### Post by Frogs Hair on 2016-08-01
In Appearance > Behavior check if the menu setting for In menu bar or in window title bar are the same.

---

