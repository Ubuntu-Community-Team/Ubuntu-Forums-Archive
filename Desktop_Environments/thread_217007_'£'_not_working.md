---
title: "'£' not working"
date: 2006-07-16
forum: Desktop Environments
---

### Post by Matthew Bartram on 2006-07-16
I have a UK keyboard, but shift+3 gives '3' not '£'. Does anyone know how to fix that? (I'm in gnome)

---

### Post by BuffaloX on 2006-07-16
Until you get it fixed, try using:
 right alt + 3.
That works for me.

---

### Post by Matthew Bartram on 2006-07-16
It doesn't for me. I can use a character palette on the panel in the meantime, but that's less than ideal.

---

### Post by Malac on 2006-07-16
Go to System->Preferences->Keyboard then choose Layouts 
Grab the bottom corner of the windows to increase the size so you can see the layout properly Choose United Kingdom -> International in the left pane and this should give you the £ sign.

---

### Post by BuffaloX on 2006-07-16
Is it just the £ that dosn't work, or are other keys affected too?

---

### Post by Matthew Bartram on 2006-07-16
I think it's just the '£' sign not working.

When I try changing things in the keyboard preferences I often get a box (or a few boxes) popping up with this mesage:[INDENT]Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70000000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
[/INDENT]

---

### Post by Matthew Bartram on 2006-07-17
Now I get that error message popping up when GNOME starts :-(

---

### Post by AZzKikR on 2006-07-17
Perhaps this thread is an solution to your issue:

[http://www.ubuntuforums.org/showthread.php?t=207603&highlight=XKB](http://www.ubuntuforums.org/showthread.php?t=207603&highlight=XKB)

---

### Post by Matthew Bartram on 2006-07-17
Thanks, that worked.

---

### Post by Matthew Bartram on 2006-07-17
Except I still get the error message on startup. But perhaps that's before the 'fixkeyboard' is loaded. The £ key works now, but it would be nice to get rid of the error message.

---

