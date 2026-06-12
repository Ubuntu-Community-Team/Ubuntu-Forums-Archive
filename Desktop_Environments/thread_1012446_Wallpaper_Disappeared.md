---
title: "Wallpaper Disappeared"
date: 2008-12-15
forum: Desktop Environments
---

### Post by EEPS on 2008-12-15
One day booting into GNOME, my wallpaper just disappeared and only shows a solid color (the one selected in background prefrences). Changing the background preferences does not help, nor does adding a new picture and trying to select that. I have rebooted many times and that does not help. The only thing I can think of is that I was using the remote desktop utility and selected the "Disable Wallpaper when Connected" option, but I am logged in locally and I have since disabled that option, so I don't know if that somehow broke something. any ideas?

-Thank You

---

### Post by EEPS on 2008-12-15
Ok, of course I find this thread now [http://ubuntuforums.org/showthread.php?t=974039&highlight=wallpaper]("http://ubuntuforums.org/showthread.php?t=974039&highlight=wallpaper") Go to gconf-editor -> Desktop -> gnome -> background and check draw_background. This is a bug I guess with remote desktop.

---

