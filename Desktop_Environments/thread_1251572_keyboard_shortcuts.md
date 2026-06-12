---
title: "keyboard shortcuts"
date: 2009-08-27
forum: Desktop Environments
---

### Post by jomex on 2009-08-27
i was customizing my keyboard shortcuts which is quite a pain in the A55 because the Super key is not supported in "Keyboard Shortcuts" and in gconf-editor the shortcuts are distributed offer hundred folders you don't know. nevertheless, i accidentally deleted the "Keyboard Shortcuts" in "Main Menu" which i would need however for a few last custom shortcuts. pressing "revert" doesn't bring it back.

1. how do i get "Keyboard Shortcuts" back?
2. which process is "Keyboard Shortcuts"?
3. where do i find the keybindings for "shutdown" and "lock" in gconf-editor?

---

### Post by dimitris. on 2009-08-27
i don't if i am in the right thread but i would like to ask if anyone can help me with my stupid problem!!
i just install ubuntu on my pc and when i plugged in my HHD i send to the trace an important file which i don't know how to restore.
It's like e part of my HHD is in the trace but not delete 
help me please i'm going to have a panic attack!!

---

### Post by jomex on 2009-08-27
well actually you posted in a random thread
go to [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)
click on [new thread] and repost your problem
btw: what do you mean by trace?

---

### Post by dimitris. on 2009-08-27
sorry!!
i mean the recycle bin :$

---

### Post by dimitris. on 2009-08-27
let me ask u something..
is there any chance I'm  looking for thn Ctrl+Z key combination??

---

### Post by jomex on 2009-08-28
open the recycle bin in the lower right corner, right click on the files you want to restore and click on "restore". [ctrl]+[Z] is not yet implemented for undoing file deletion.

---

### Post by VCoolio on 2009-08-28
> **jomex said:**
> i was customizing my keyboard shortcuts which is quite a pain in the A55 because the Super key is not supported in "Keyboard Shortcuts" and in gconf-editor the shortcuts are distributed offer hundred folders you don't know. nevertheless, i accidentally deleted the "Keyboard Shortcuts" in "Main Menu" which i would need however for a few last custom shortcuts. pressing "revert" doesn't bring it back.

1. how do i get "Keyboard Shortcuts" back?
2. which process is "Keyboard Shortcuts"?
3. where do i find the keybindings for "shutdown" and "lock" in gconf-editor?

1. Right click menu and click "edit menus" (or run "alacarte" which is the same). Maybe you can reactivate "Keyboard shortcuts" in system > preferences or else add it again using "gnome-keybinding-properties" as the command.
2. gnome-keybinding-properties
3. no idea, but to make keybindings for yourself, the commands are 

lock screen: "gnome-screensaver-command --lock"
logout: "gnome-session-save --logout" (--logout-dialog for, well, the dialog)
shutdown: "gnome-session-save --shutdown-dialog"

Hope that helps.

---

### Post by jomex on 2009-09-16
thank you VCoolio :)

---

