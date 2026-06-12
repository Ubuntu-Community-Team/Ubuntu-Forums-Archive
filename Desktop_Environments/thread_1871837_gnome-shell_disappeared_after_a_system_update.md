---
title: "gnome-shell disappeared after a system update"
date: 2011-10-29
forum: Desktop Environments
---

### Post by subehsharma on 2011-10-29
I have been running ubuntu 11.10 since its release and loved Gnome 3(gnome-shell). Yesterday after a regular system update, my gnome-shell stopped working all of a sudden and what i'm getting now is a mix of gnome classic and gnome3 (the calendar is still in the middle of the top bar)

I tried to completed remove shell and reinstall it but it didnt work. What can i do now?

---

### Post by crdlb on 2011-10-29
You're in the fallback session. Open a terminal and run:```
gnome-shell --replace || metacity
```

GNOME Shell should print an error when it fails to start.

---

### Post by subehsharma on 2011-10-29
subsharm@subsharm:~$ gnome-shell --replace || metacity


Clutter-CRITICAL **: Unable to initialize Clutter: Unable to select the newly created GLX context
Window manager error: Unable to initialize Clutter.
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

---

### Post by crdlb on 2011-10-29
> **subehsharma said:**
> 
Clutter-CRITICAL **: Unable to initialize Clutter: Unable to select the newly created GLX context


That appears to be a video driver issue. What GPU do you have? Please post your /var/log/Xorg.0.log in code tags.

---

### Post by subehsharma on 2011-10-30
Thanks for the suggestion. I removed nvidia current driver (which i manually installed after downloading the current one from their website) and installed the nvidia-current. After that everything started working.

---

### Post by subehsharma on 2011-10-30
sudo apt-get install nvidia-current

---

