---
title: "How to start a application instead of gnome desktop?"
date: 2009-02-17
forum: General Help
---

### Post by AlwaysMyLady on 2009-02-17
hi there!

   After ubuntu load all the modules needed,it will start gnome desktop with gdm
   
   Bui what if i dont want gnome-desktop to start? i used sysv-rc-conf to forbid gdm in all run levels.But i stucked in the login screen of command-line mode.

   My question is how to auto-start an application like firefox in commandline mode without entering username and password?

   thx very much!

---

### Post by handy on 2009-02-17
> **AlwaysMyLady said:**
> hi there!

   After ubuntu load all the modules needed,it will start gnome desktop with gdm
   
   Bui what if i dont want gnome-desktop to start? i used sysv-rc-conf to forbid gdm in all run levels.But i stucked in the login screen of command-line mode.

   My question is how to auto-start an application like firefox in commandline mode without entering username and password?

   thx very much!

I think you may have a better chance with a distro like Arch when it comes to the type of customising you want to do. ;-)

---

### Post by dawynn on 2009-02-17
Look here:

[http://kiosk.mozdev.org/](http://kiosk.mozdev.org/)

This is a description of a project designed at making a stand-alone kiosk type macine.  They have a default disk you can download, but they also describe all the steps they went through to get there.

The end result is, by popping in a disk, optionally loaded with your own list of accepted / rejected sites, the computer becomes nothing but an internet kiosk.  Every attempt to access anything else is blocked and returns to the home page specified on the disk.

Even if its not exactly what you're looking for, you can probably glean some helpful tips as to how they go straight from bootup to browser.

---

### Post by AlwaysMyLady on 2009-02-17
thx very much for your advice.I will look it up.

but can i customize ubuntu by myself? by just starting system with startx instead of gdm? i have modified ./xinitrc file and after i manully logged into xwindow, i can get the result i want by typing startx.So how can it be
automatically executed?

---

### Post by kerryhall on 2009-02-17
I am curious about this as well.

---

### Post by AlwaysMyLady on 2009-02-17
it looks that kiosk hasn't been changed for a long time,but it's similar to what i want.
Any new idea?

---

