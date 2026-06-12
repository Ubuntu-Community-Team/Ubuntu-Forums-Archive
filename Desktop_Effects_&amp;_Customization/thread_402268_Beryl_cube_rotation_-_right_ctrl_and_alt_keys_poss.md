---
title: "Beryl cube rotation - right ctrl and alt keys possible?"
date: 2007-04-05
forum: Desktop Effects &amp; Customization
---

### Post by iMav on 2007-04-05
I can not seem to find out how to assign my right ctrl and right alt keys for beryl cube rotation.  Key bindings in the manager simply say <Control> and <Alt> for these keys (not specifying left or right...even though it seems to imply left only).

Any help would be appreciated.

---

### Post by Belyel on 2007-04-05
The problem is that linux recognizes your right control and alt keys by different key codes than the left control and alt keys.  For example, if you type 'xev' into a terminal, it will show the key codes (and mouse movement and clicks) in the terminal for whatever you press while the program is executing.  On my computer, it have alt and control as Alt_L, Alt_R, Control_L, Control_R for the left and right keys, respectively.  You could probably set up Beryl to use the right alt and control if you could figure out what Beryl calls them, although on my machine, the right alt and control do work for rotating the cube.  Also, you can remap what your keys are called using 'xmodmap', search the forums or google for further instructions.

---

### Post by iMav on 2007-04-05
Got this resolved.  Check [this thread](http://ubuntuforums.org/showthread.php?t=287318&page=2) for details.

---

