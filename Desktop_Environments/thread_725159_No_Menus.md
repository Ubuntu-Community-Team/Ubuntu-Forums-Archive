---
title: "No Menus"
date: 2008-03-15
forum: Desktop Environments
---

### Post by pbhill on 2008-03-15
Yesterday when I booted up Gutsy, I had no desktop menus or desklets. Nothing but the wallpaper and desktop icons.  After a reboot they were back. This AM the same thing, except a reboot doesn't do it. No way to access my apps. I'm not even sure how to open a terminal screen. Any suggestions? Thanks in advance!

---

### Post by dje on 2008-03-15
Can you do Alt + F2 to get a run dialog? If so run the following in it:
```
gnome-panel
```
That should solve the problem for that login (if you can get the run dialog)

dje

**EDIT: Ah yes, I mean Alt + F2 not Ctrl + F2**

---

### Post by pbhill on 2008-03-17
I tried Ctrl-F2 to no avail, but Ctrl-Alt-F2 brings up the terminal. Typed in "gnome-panel" but it says thats not a command. 
..It just feels so wrong to have to use Windows to access Ubuntu forums!

---

### Post by Lord Illidan on 2008-03-17
I believe the run program dialog is ALT + F2, not CTRL + F2, at least by default.

However, this is interesting, when you typed gnome-panel into the terminal, did it tell you command not found? 

I think you might have removed some gnome packages by mistake.

---

### Post by pbhill on 2008-03-17
> **Lord Illidan said:**
> I believe the run program dialog is ALT + F2, not CTRL + F2, at least by default.

However, this is interesting, when you typed gnome-panel into the terminal, did it tell you command not found? 

I think you might have removed some gnome packages by mistake.

I had to reboot and check it all again...
I could not bring up the run program dialog.
The only way I could get the terminal screen was Ctrl-Alt-F2.
But I did give wrong information... the message was "Cannot open display, run gnome-panel --help" I saw nothing in the help section that I could use.
If I have removed some packages by mistake, how should I proceed to restore Gnome to it's former usefulness?

---

### Post by pbhill on 2008-03-18
Well, I got brave and did some research in the forums. Found several posts with similar problems and tried a few things. As usual, I am now out of the frying pan and into the fire! I seem to have completely disabled my GUI and only have command line, which I am not very familiar with. Any help would be appreciated!

---

