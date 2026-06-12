---
title: "Screen Brightness trigger Display Settings"
date: 2014-09-12
forum: Desktop Environments
---

### Post by Manorie on 2014-09-12
Hello everybody,

I have just migrated from Ubuntu to Xubuntu. I have a Radeon HD 7640G Gpu in my Lenovo G505S. First of all, minimalistic desktop feels amazing I strongly recommend Xubuntu over other shells. My problem is, whenever I hit screen brightness key (increase or decrease) it works but it also triggers display settings. If I press it 5 times, 5 new display settings window gets open.
I searched that problem could not find a solution and this was not an issue in gnome or unity, in my previous install.I am using fglrx driver, which is downloaded from AMD website. 

Any recommendations please?
Thank you,

---

### Post by Toz on 2014-09-12
Welcome to the forums.

It would appear that your system is emitting the XF86Display signal when you press the brightness key combination. Try going to Settings Manager >> Keyboard >> Application and delete the "xfce4-display-settings --minimal" - "XF86Display" shortcut and see if that helps.

---

### Post by Manorie on 2014-09-13
Thank you very much, 
This is exactely what was I looking for.

---

