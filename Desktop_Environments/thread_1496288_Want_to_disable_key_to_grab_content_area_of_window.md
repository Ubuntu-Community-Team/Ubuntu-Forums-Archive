---
title: "Want to disable key to grab content area of window"
date: 2010-05-29
forum: Desktop Environments
---

### Post by pmooney78 on 2010-05-29
There's a movement key option in the Preferences -> Window Preferences settings that lets me choose which key to use to move a window by the content area. Problem is, the only options are the Control, Alt, and Super keys, and none of these is a good option: I have at least one application that wants to use each of these keys for something else.

I'd like to disable this completely, if possible. I'm perfectly happy only grabbing windows by their title bars to move them. If that's not possible, can I remap the key to something unlikely and bizarre (like ctrl-alt-shift-tab)?

Any help is much appreciated.

I'm running Ubuntu 9.10 on an HP Pavilion dv6000 with 2GB of RAM and a Centrino Duo processor.

---

### Post by pmooney78 on 2010-05-31
bump

---

### Post by pmooney78 on 2010-06-01
bump

---

### Post by Zemblan on 2010-06-01
Press Alt+F2. Run the command 'gconf-editor'. In the left pane of the editor navigate to apps -> metacity -> general. The setting you need to change is 'mouse_button_modifier'. Double click it and put a value in there like 
```
<CONTROL><ALT><SHIFT>
```

Don't try to leave it blank, it has unfortunate effects.

---

### Post by pmooney78 on 2010-06-02
Excellent! It works! Thank you so much!

---

### Post by ppolleunus on 2010-07-21
I don't know if it's the same problem.
After upgrading to 10.04, when I hit the left alt key, the "move" action is activated (same as when selecting it in the window menu).
I can launch some shortcuts but not all. Maybe only the ones configured in Compiz. In applications, none work. (I'm of course talking only about shortcuts using the alt key)
I modified "mouse_button_modifier" as explained here but it doesn't change anything.

FYI, I'm on a MacBook Pro.

This is really annoying so please help :-(

---

### Post by pmooney78 on 2010-07-25
Sorry, no idea myself ... it always helps to check the obvious, though. Are you dead sure it's not a physical problem with your keyboard? Do you have a USB keyboard you can [borrow and] plug in to check to see if it still happens?

Sorry, I don't have any other suggestions, myself. If that's not it, you're likely to get noticed better if you start a new thread, though. ;)

---

