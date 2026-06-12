---
title: "Mouse right click too sensitive."
date: 2009-02-16
forum: General Help
---

### Post by Bruv on 2009-02-16
When I right click the mouse it automatically creates a new folder on the desktop. Then when I try to delete it, it automatically opens it. I close it and try again to delete and am caught in a cycle of either creating new folders or opening new folders I don't want.

Where and how do I change this behaviour ?

---

### Post by Partyboi2 on 2009-02-16
Make the adjustment in System>Pref>mouse

---

### Post by Bruv on 2009-02-16
> **Partyboi2 said:**
> Make the adjustment in System>Pref>mouse

I have been there and tweaked, but to be honest don't know which setting will alter this behaviour.

---

### Post by geirha on 2009-02-16
Open a terminal (Alt+F2 -> gnome-terminal) and run ```
xev
```
Move the mouse pointer inside the white window that appeared. You'll see alot of MotionNotify events scroll by in the terminal. Hold it steady and click the right mouse button, then move it out of the window and click the X to close the window. What events were created by the mouse-click (in between those MotionNotify events)?

I got these registered
```

ConfigureNotify event, serial 28, synthetic NO, window 0x5a00001,
    event 0x5a00001, window 0x5a00001, (500,55), width 178, height 178,
    border_width 2, above 0x207c513, override NO

ButtonPress event, serial 28, synthetic NO, window 0x5a00001,
    root 0x63, subw 0x0, time 220262440, (104,76), root:(606,133),
    state 0x10, button 3, same_screen YES

ConfigureNotify event, serial 28, synthetic YES, window 0x5a00001,
    event 0x5a00001, window 0x5a00001, (500,55), width 178, height 178,
    border_width 2, above 0x34055bf, override NO

ButtonRelease event, serial 28, synthetic NO, window 0x5a00001,
    root 0x63, subw 0x0, time 220262545, (104,76), root:(606,133),
    state 0x410, button 3, same_screen YES

```

---

### Post by Bruv on 2009-02-16
Now thats a worry, nothing happened.

While moving the pointer into the square the pointer changed as it does on boxes, to re-size, but once inside, nothing, nothing at all.

For information its an Optical mouse from Saltek

---

### Post by geirha on 2009-02-16
Do you have another computer and/or OS you can try that mouse on? It may be a driver issue and it may be a hardware issue...

---

### Post by Bruv on 2009-02-16
I am dual booting XP and Ubuntu, but no other PC available.
Should I try to replicate the problem in XP ?

---

### Post by Bruv on 2009-02-16
The mouse works perfectly in XP

---

### Post by geirha on 2009-02-16
If it works normally in Windows, then it must be a driver issue. In that case you should report the bug on launchpad. [https://bugs.launchpad.net/ubuntu/+source/xorg-server](https://bugs.launchpad.net/ubuntu/+source/xorg-server)

---

### Post by Bruv on 2009-02-16
> **geirha said:**
> If it works normally in Windows, then it must be a driver issue. In that case you should report the bug on launchpad. [https://bugs.launchpad.net/ubuntu/+source/xorg-server](https://bugs.launchpad.net/ubuntu/+source/xorg-server)


I have just done so, my first bug report.....sigh.

---

