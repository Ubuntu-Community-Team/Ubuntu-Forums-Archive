---
title: "No screensaver/dark screen...no matter how long I am away"
date: 2009-11-28
forum: Desktop Environments
---

### Post by divinityofnumber on 2009-11-28
Hello all,

After the upgrade to 9.10 this started happening. I have not had any other problems though.

I can walk away from the computer, and come back 5 hours later, and my desktop is still just as up and bright as it was when I left. I have it set to activate a blank screen screensaver when the computer has been idle for 5 minutes. But, it never does. 

Any ideas?

---

### Post by hirnwurscht on 2009-11-28
To check your DPMS / Screensaver settings type
```
xset -q
```
in a Terminal.

with
```
xset dpms 0 0 360
```
and DPMS enabled you will have your monitor suspend after 5mins (360secs).

To make this permanent put the command in the autostart of your desktop.

Maybe someone else has a solution using gnome-screensaver or such.

---

### Post by divinityofnumber on 2009-12-11
Thanks for the advice. For some reason it seems to have been fixed by itself. There have been updates almost daily it seems, and I did notice a couple of them had to do with gnome screensaver, etc. So, it seems to have been taken care of by the updates.

---

