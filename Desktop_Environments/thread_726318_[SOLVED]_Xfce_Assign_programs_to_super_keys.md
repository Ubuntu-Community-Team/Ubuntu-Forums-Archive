---
title: "[SOLVED] Xfce Assign programs to super keys"
date: 2008-03-16
forum: Desktop Environments
---

### Post by Bruce M. on 2008-03-16
Hi folks,

With Xubuntu 7.10 my two "Super Key" are dead.

I have a Microsoft Internet Keyboard Pro (Latin America) and as seen in the attachment the " Keyboard Shortcuts" is greyed out.

xev tells me:

```
KeyRelease event, serial 31, synthetic NO, window 0x2c00001,
    root 0x45, subw 0x0, time 3107711662, (-145,-162), root:(406,267),
    state 0x50, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 31, synthetic NO, window 0x2c00001,
    root 0x45, subw 0x0, time 3107716660, (-145,-162), root:(406,267),
    state 0x10, keycode 116 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

Thanks
Bruce

**EDIT:**  Hmm, put this in the wrong place, it should be in **General Help**. If you have the power to do so, and are so inclined, I would appreciate it if you move it.  Thanks, Bruce

---

### Post by solar george on 2008-03-16
You must click on "Add" to setup a copy of the shortcut profile which you can then edit.

---

### Post by Bruce M. on 2008-03-16
> **solar george said:**
> You must click on "Add" to setup a copy of the shortcut profile which you can then edit.

OK, I've added a "profile" and have xterm in there but no way to add the keystroke.

I right clicked on it, selected Edit, and that's the little window you see. It lets me edit the command only.

---

### Post by solar george on 2008-03-17
You must double click on the keyboard shortcut to change it.

---

### Post by Bruce M. on 2008-03-17
> **solar george said:**
> You must double click on the keyboard shortcut to change it.

Double clicking on Shortcut open a popup box that says:

Title:Set Shortcut
Options are: [Cancel] or [No Shortcut]

So while that box was there I tapped the left "Windows" key. (Super_L)

Now what I see is:
```
/user/bin/xterm  Super+Super_L
```

Hitting the left Windows Logo key does not start xterm  :(

Holding down the "Super_R" key and tapping the "Super_L" keys does.
I can live with that for now, although I'd like a one touch key.

Any other ideas?
Bruce

---

### Post by PoopSlayer on 2008-03-17
I have absolutely no idea. I can't assign ANY command to my super buttons (they just don't respond for SOME reason)

---

### Post by Bruce M. on 2008-03-18
> **PoopSlayer said:**
> I have absolutely no idea. I can't assign ANY command to my super buttons (they just don't respond for SOME reason)

Did you try the stuff above?

I have to use "both" for some reason, but better than nothing.

Applications > Settings > Keyboard Preferences

[LIST=1]
[*]Shortcuts > Add (the one on the left, above Remove) - Give it a name.
[*] Right click on any command > Add
[*] Click on the Icon to the right of the empty Command Box.
[LIST]
[*]It will take you to /usr/bin - find the program you want to use.
[*]    or just start typing the program name for fast access ie: xterm
[/LIST]
[*] Double click on the program name, you'll see: Command: /usr/bin/xterm - click - OK
[*] A new pop-up appears with:

```
Set shortcut for command:
/usr/bin/xterm
[Cancel] [No Shortcut]
```

[*] Do nothing except hit one of the Super Keys ( for this example the right one )
[/LIST]

Now you should see:

```
/usr/bin/xterm        Super+Super_R
```

I actually now have:

```

/usr/bin/xterm                Super+Super_R
/usr/bin/gnome-terminal       Super+Super_L

```

Let me know if it helps.
Bruce

---

