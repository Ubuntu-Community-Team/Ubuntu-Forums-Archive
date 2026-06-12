---
title: "gnome-screensaver and compiz"
date: 2007-08-30
forum: Desktop Effects &amp; Customization
---

### Post by Chymera on 2007-08-30
I have the following settings in my ccsm, under >animations>open&close

> 
Burn for "(type=Normal | Utility)"
Fade for "(type=Menu | ModalDialog | Dialog | PopupMenu | DropdownMenu) & !(name=gnome-screensaver)"


I believe that the screensaver should fade in and out.... however, even though before the screensaver starts the screen fades to black, the screensaver opens/closes with the burn effect.

WHY?
and most importantly, how do i get it to open/close properly=

---

### Post by Inxsible on 2007-08-30
You have an exclamation mark in front of (name=gnome-screensaver) which represents a negation.
So what you are basically saying is Fade for "blah" & where name is not equal to gnome-screensaver.

Remove the exclamation mark and try that. I am not 100% sure it will work tho :(

---

### Post by Chymera on 2007-08-31
10x for the tip... i dont have any time to wait for my screensaver to appear naturally now.... but i hope it works :) .... i really need to catch up on my coding :lol: 

Do you have any idea how i could tell ccsm to close maximized windows with face, whilst closing any other windows with burn?

---

