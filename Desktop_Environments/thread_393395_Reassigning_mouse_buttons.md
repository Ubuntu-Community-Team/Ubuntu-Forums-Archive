---
title: "Reassigning mouse buttons"
date: 2007-03-25
forum: Desktop Environments
---

### Post by DeathOnJuice on 2007-03-25
Hey, everyone. I just got a new mouse and keyboard  (Microsoft Optical Desktop 3000), and it seems really nice so far. It's a standard 3-button mouse with a scroll wheel that can also be tilted from side to side However, clicking down the mouse-wheel is a bit sticky. Is there any way to replace the middle click button with tilting the scroll wheel left? I saw the thread here, but I don't know how to apply it:

[http://ubuntuforums.org/showthread.php?t=192264&highlight=intellimouse+explorer](http://ubuntuforums.org/showthread.php?t=192264&highlight=intellimouse+explorer)

Also, is there a way to make the scroll wheel go a few extra lines per click?

Thanks in advance!

---

### Post by DeathOnJuice on 2007-03-25
Anyone?

---

### Post by DeathOnJuice on 2007-03-26
Surely someone must know?

---

### Post by jpkotta on 2007-03-26
You can see what the buttons are called with the xev command:
```
xev
```

When you run it, it will open up a little window and spew tons of info on the terminal whenever you do something (e.g. press a key, click a mouse button, etc.) while the window is focused.  You should see what button it says you're pressing the one you want to be the new middle click.  Then you can use xmodmap to remap the buttons.  For example, if you want button 7 to be the new middle button, then you would do
```
xmodmap -e "pointer = 1 2 7 4 5 6 7 8 9"
```
To reset, in case of a mistake, 
```
xmodmap -e "pointer = default"
```
For the documentation, use google or 
```
man xmodmap
```

---

### Post by AlexKarm on 2007-03-27
Though you should note that Ubuntu doesn't seem to recognise all the mouse buttons by default.

I'm using a G5 Laser mouse, and though I have buttons 1 2 3 (Left, Wheel, Right), 4 5 (Wheel up and down), and 8 (Thumb button), my tilt left and tilt right of the wheel doesn't trigger an event (doesn't register as a button press).

Therefore, if you are in the same boat, a better mouse driver is needed. If anyone knows anything about where to get one, speak up :P

---

