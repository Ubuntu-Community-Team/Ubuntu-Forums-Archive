---
title: "Where is the hardware configuration tool"
date: 2006-09-07
forum: Desktop Environments
---

### Post by Rusty Shackleford on 2006-09-07
I downloaded Nvidia grapihcs driver through easyubuntu, but it doesn't seem to be running, or ubuntu is just naturally slow. 

Where is the tool to see what drivers are installed?

---

### Post by croak77 on 2006-09-08
Check your /etc/X11/xorg.conf. And look for;
```
Driver      "nvidia"
```

If it says "nv" then change it to nvidia. Restart X, Ctrl-Alt-Backspace and you should see the nvidia splash logo.

---

