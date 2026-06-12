---
title: "Matlab - text not working (Gutsy)"
date: 2007-11-28
forum: Education &amp; Science
---

### Post by ackey on 2007-11-28
I installed Matlab shortly before the gutsy upgrade, so while I feel like this problem didn't exist from the beginning, I am unsure if its beginning corresponded to Gutsy or some other system update.  This problem occurs whether or not I have the compiz effects turned on.

After Matlab opens a figure window (specifically in the workspace the main window is in), it prevents me from typing in the command window.  Specifically, I can position the cursor, right click, paste, or highlight text, but cannot executed pasted text or type.  If I pop-in or pop-out, then I am able to type.  If I double click on a previous command in the command history window it is able to execute it.  Closing the figure windows does not fix the text problem.

I have had other problems with Matlab - such as the mouse going quite wacky and then not being "aligned" properly.  I am not positive this was caused by Matlab.  The output of dmesg:
```
[ 4312.352000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 4312.352000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 4312.352000] psmouse.c: issuing reconnect request
[ 4312.988000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[ 4313.020000] input: SynPS/2 Synaptics TouchPad as /class/input/input7

```

Any advice on what could be causing the problem or where to look for help would be great.  Thanks!

---

### Post by ackey on 2007-12-05
Well, I've worked around my problem somewhat by having the figures popped-in to the desktop, which mostly helps.

However, my surface plots are always black.  I've tried changing the color map, but they are always a giant black blob.  Is this related?  Can anyone help me?

---

### Post by amateur-scientist on 2007-12-12
I had the same problem, and fixed it by (1) disabling all (compiz) visual effects under System-Preferences-Appearance-Visual Effects, and (2) in System-Preferences-Windows I unchecked 'Select Windows when mouse moves over them', and disabled the double click actions for the title bar.

Hope this works for you.

On the black glob issue, it could be plot lines around the pixels. If so, try 'shading flat'.

---

### Post by amateur-scientist on 2007-12-12
Ah well, after a short matlab session and initially trouble free the problem re-appeared, sorry.

---

### Post by swapnasarit on 2008-05-19
I have the exactly same problem I made the fixes export AWT toolkit and install matlab. But i can't type anything in the command window or in the editor once move the mouse to another window. But I can only copy paste from the menu. I installed Matlab 7.5 r2007b .using compiz-fusion in ubuntu 7.10 in a T40 machine

---

### Post by jeneverboy on 2009-09-10
He

> But i can't type anything in the command window or in the editor once move the mouse to another window

I have the same problem. Anyone with a solution? I know this is an old thread but..

Installed matlabR2007b with ubuntu 9.04 and have compiz and awn on.

Bye , Alex.

---

