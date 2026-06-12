---
title: "Only Fallback mode"
date: 2011-10-25
forum: Desktop Environments
---

### Post by kc153Pirate on 2011-10-25
I have installed gnome shell in 11.10, but when i enter the gnome session the desktop is in falback mode. Not sure how to go about correcting this. I know gnome shell should work since i ran fedora 15 for a while. Any help would be appreciated

---

### Post by merlinus on 2011-10-25
Check your video card against the requirements for gnome shell.  If it does not measure up, then the system reverts to fallback.

---

### Post by crdlb on 2011-10-25
Open a terminal and run ```
gnome-shell --replace || metacity
```

That should give a useful error message.

---

### Post by kc153Pirate on 2011-10-26
> **crdlb said:**
> Open a terminal and run ```
gnome-shell --replace || metacity
```That should give a useful error message.

Xlib:  extension "GLX" missing on display ":0.0".

Clutter-CRITICAL **: Unable to initialize Clutter: The OpenGL version could not be determined
Window manager error: Unable to initialize Clutter.
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

I am running integrated intel graphics but my laptop has the option of running a Nvidia GeForce 9300M GS. Just dont know how to tell linux to use that graphic card instead.

---

### Post by collisionystm on 2011-10-26
> **kc153Pirate said:**
> Xlib:  extension "GLX" missing on display ":0.0".

Clutter-CRITICAL **: Unable to initialize Clutter: The OpenGL version could not be determined
Window manager error: Unable to initialize Clutter.
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

I am running integrated intel graphics but my laptop has the option of running a Nvidia GeForce 9300M GS. Just dont know how to tell linux to use that graphic card instead.

What kind of laptop?

---

### Post by kc153Pirate on 2011-10-27
> **collisionystm said:**
> What kind of laptop?

Its a Sony Vaio VGN-Z520N

---

### Post by kc153Pirate on 2011-10-30
Bump

---

