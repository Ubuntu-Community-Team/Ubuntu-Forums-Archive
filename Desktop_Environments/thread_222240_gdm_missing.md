---
title: "gdm missing"
date: 2006-07-24
forum: Desktop Environments
---

### Post by Horndog on 2006-07-24
The last kernel upgrade trashed my sound and one other picture viewing app. I followed a how to for recompiling my sound driver and broke my desktop, as in login only from the terminal. I installed the desktop (gnome) and now the gdm is missing. So now I have not access to root privileges in desktop (sudo) and have to start the desktop by "~$startx". Any help would be appreciated.

---

### Post by Jagot on 2006-07-24
```
sudo aptitude update && sudo aptitude install gdm
```

---

### Post by Horndog on 2006-07-24
Thank you for the reply. I will try that if what I did fails. I was able to access synaptic using the terminal and install gdm. I now has root privileges again and have the graphical login screen. I still have a glitch with firestarter (starting at boot) giving me a "do not have root privileges error) but it starts. At least the GUI does. Thanks again

---

