---
title: "How do I kill a full screen game when it freezes?"
date: 2008-12-27
forum: General Help
---

### Post by weirddan455 on 2008-12-27
I'm running intel integrated graphics on my laptop so games aren't very stable.  Is there any way in linux to do a ctrl+alt+delete type thing like windows does with the task manager?  I know about ctrl+alt+backspace but that kills X, logs me out and kills all running applications (like transmission).  I've tried alt+tab but that doesn't do anything at all.

---

### Post by conscious on 2008-12-27
You can press Ctrl+Alt+F1, log in, kill the game with "killall", and then return to X session with Ctrl+Alt+F7.

---

### Post by weirddan455 on 2008-12-30
That's the same as doing ctrl+alt+backspace.  I'm looking to only kill the game without killing all the other X programs.

---

### Post by ju2wheels on 2008-12-30
> **weirddan455 said:**
> That's the same as doing ctrl+alt+backspace.  I'm looking to only kill the game without killing all the other X programs.

No, its not the same. If you were running OpenArena for example, running "killall openarena" will kill all process threads with that name.

Therefore once you do that, pressing CTRL+ALT+F7 would bring you back to your working X session.

---

### Post by RichardLinx on 2008-12-30
Try this: Alt+F2 then type "xkill" and click on whatever it is you want to close.

Edit: Weiddan445, I use to play OpenArena and had it freeze in full screen mode on me a few times and "xkill" always seemed to solve the problem for me. In some cases though It hasn't worked but "Ctrl + Q" and "Alt + F4" have come through for me.

---

