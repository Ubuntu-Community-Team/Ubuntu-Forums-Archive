---
title: "XF86 Keyboard Volume Problems"
date: 2006-07-27
forum: Desktop Environments
---

### Post by linkinpark342 on 2006-07-27
I'm stumped, I've done as much research as I could find and I still get a problem where the volume down on my keyboard works (logitech cordless desktop elite) but volume up + mute + anything else doesn't. When i say it doesn't work, i mean that it detects that there is a keypress and all that stuff but for some reason it just doesn't do anything. for example, if i go to any of the Configure Global Shortcuts and press volume up as the binding it will say  XF86AudioRaiseVolume, it just doesn't DO anything. no matter what I try its like something is superceding it. I get this output from xev:
```
KeyPress event, serial 31, synthetic NO, window 0x3800001,
    root 0x75, subw 0x0, time 3001472633, (593,-93), root:(597,884),
    state 0x10, keycode 176 (keysym 0x1008ff13, XF86AudioRaiseVolume), same_screen YES,
    XKeysymToKeycode returns keycode: 175
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x3800001,
    root 0x75, subw 0x0, time 3001472633, (593,-93), root:(597,884),
    state 0x10, keycode 176 (keysym 0x1008ff13, XF86AudioRaiseVolume), same_screen YES,
    XKeysymToKeycode returns keycode: 175
    XLookupString gives 0 bytes:

```
For volume down, i get a shiny volume control thing like i'm supposed to and the bar moves down but for volume up the screen does not show at all. any ideas?
[edit: geh, kubuntu 6.06. logitech cordless desktop elite (Logitech cordless MX Duo), i686]

---

### Post by linkinpark342 on 2006-07-29
Bump-ed

---

### Post by hopstah on 2006-09-14
i have the exact same problem as you, and am very frustrated by it.  i just switched to kde, and like it so far, but this problem is just ridiculous.  i have the exact same keycode results and errors.  any help from anybody at all would be great!

---

### Post by orb9220 on 2006-09-14
I use this has custom keymaps based on keyboard type like mine in ms digital pro.

[http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/)

They have adtional keyboard files that you can import.

Workd great for me.

---

### Post by turbojugend_gr on 2006-09-14
I have cordless Logitech keyboard mouse MX300, I have no issues, I thing gnome using is the reason...so my only help is the trivial have you tried to map the volume knob(volume up) under an similar to gnome's keyboard shortcuts? I guess you did...:(

---

### Post by Ciego on 2006-09-14
I am having the same problem.  Thi weird part is that all of my keys worked at one point.  I even had the other special keys doing what I wanted them to do.  I think that this is directly related to my instalation of XGL/Compiz for some reason. It seems that the keys stopped working correctly around that time.  It may have something to do with all of the shortcut keys used for XGL/Compiz.  What do you guys think?

---

### Post by Ciego on 2006-09-14
> **orb9220 said:**
> I use this has custom keymaps based on keyboard type like mine in ms digital pro.

[http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/)

They have adtional keyboard files that you can import.

Workd great for me.

That site isn't working for me.  Is the link correct?

---

### Post by orb9220 on 2006-09-14
Yes but sourceforge may be having problems. Try later Havn't been there is awhile. But I cannot connect either. Will keep trying later and Ill post if they are up again.

---

### Post by orb9220 on 2006-09-15
Site is up now

---

### Post by Ciego on 2006-09-15
orb, thanks for the tip. Keytouch works great .... all keys functioning correctly now.  I do find it strange that Ubuntu comes with a utility that is supposed to provide the same functions but it just doesn't work.

---

### Post by Al_maverick on 2007-06-20
I have the same problem. Though it appeared after I upgraded to latest KDE.
Is there any way to solve it other than installing another program?

---

