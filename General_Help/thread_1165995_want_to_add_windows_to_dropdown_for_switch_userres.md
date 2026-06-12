---
title: "want to add windows to dropdown for switch user/restart/shutdown"
date: 2009-05-21
forum: General Help
---

### Post by zero7404 on 2009-05-21
how do i go about adding an entry in the dropdown that can temporarily change GRUB and boot into windows upon restart ?

currently have GRUB default as Ubuntu, but occassionally boot into windows too. would be more convenient to have that item on the pulldown so that i can just click it and walk away (as opposed to wait for grub to load and choose the OS).

---

### Post by Vaphell on 2009-05-21
googling indicates that grub-reboot <id> command does that (id - identifier of desired OS in grub menu.lst)
no idea how to add that to gui

---

### Post by pricetech on 2009-05-21
Add as a Custom Application Launcher ???  I'll set up a dual boot box as soon as I get time and test that.

---

### Post by zero7404 on 2009-05-21
within ubuntu i use kgrub editor and it works fine for changing the boot sequence, but i have to do it the long way, as opposed to just clicking an icon, having it modify grub for the next boot...

---

### Post by pricetech on 2009-05-21
Check out this article.  The guy uses KDE, but if you're using Gnome it should be pretty much the same I'd think.

I'm in the process of testing it here.

[http://robotics.caltech.edu/~klk/linux.html](http://robotics.caltech.edu/~klk/linux.html)

---

### Post by pricetech on 2009-05-21
The link in my last post:  The shell script doesn't work.  Has something to do with the entries not being numbered as best I can tell.

That's why I can't get the other solution to work.  No "id" on the entries in "menu.lst".

I'll be glad to test any other ideas, but I'm out.

---

### Post by zero7404 on 2009-05-23
considering Linux' extreme versatility, someone out there has probably done it before, or there could be an app in synaptic....i'll keep looking, but if anyone knows of how to get a feature like this into the user switcher i'd like to hear....

---

### Post by Locutus_of_Borg on 2009-05-23
[http://wiki.debian.org/GrubReboot](http://wiki.debian.org/GrubReboot)

---

### Post by zero7404 on 2009-05-24
thanks for the link Locutus, that looks interesting...

in the meantime, i found a tool that's closer to what i want, it's called grub-choose-default....
i installed it thru synaptic, then placed a launcher on the desktop using gksu to start it (need to be root in order to run it)....

so if i have something to do in windows and need to walk away during reboot, i'll set it in grub-choose-default, restart, then come back to my other OS.

---

