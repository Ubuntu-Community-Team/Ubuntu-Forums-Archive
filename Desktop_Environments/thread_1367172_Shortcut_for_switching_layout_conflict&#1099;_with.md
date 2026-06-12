---
title: "Shortcut for switching layout conflict&#1099; with others shortcuts with this keys"
date: 2009-12-29
forum: Desktop Environments
---

### Post by PiaFraus on 2009-12-29
Problem as I see it:

Keyboard layouts are switched by pressing keys. Not by releasing it.


This lead to situations like this:

If my key-sequence for switching is *Ctrl+Shift*, I couldn't use *Ctrl+Shift+Any other key* in Keyboard Shortcuts menu. Also *Ctrl+Shift+S* is not working for programs like GEDIT .

Same behaviour for others Keyb.layout.shortkeys.

Example:

In System->Preference->Keyboard->Keyboard->Layouts->Layouts options->Key(s) to change layout:
 *Shift+Alt*
In System->Preference->Keyboard shortcuts:

I choose any line and try to press *Shift+Alt+Z*, instead of this I get *Shift+Z*. If I press *Alt+Shift+Z*, I get *Alt+Z*.


I tried to find anything similar to this problem, but can't. Any ideas how to make layouts switching only by releasing *Ctrl+Shif*t?

My system: 
Asus eee 1000HE with Ubuntu 9.10

---

### Post by nETPOBu4 on 2010-01-11
I can confirm this: its affects me too.

---

### Post by Dmitri S on 2010-04-28
I've got the same problem in Lucid, Shift+Alt combination of switching keyboard languages conflicts with Eclipse refactor shortcuts. 
For example when I try to rename a method, using Shift+Alt+R, the keyboard language switches only. 

As I remember, in Karmic Shift+Alt and Alt+Shift combinations were different. And it allowed to use Eclipse shortcuts also, pressing Alt+Shift+R for example. But seems that now in Lucid it doesn't work.

---

### Post by simosx on 2010-05-07
> **Dmitri S said:**
> I've got the same problem in Lucid, Shift+Alt combination of switching keyboard languages conflicts with Eclipse refactor shortcuts. 
For example when I try to rename a method, using Shift+Alt+R, the keyboard language switches only. 

As I remember, in Karmic Shift+Alt and Alt+Shift combinations were different. And it allowed to use Eclipse shortcuts also, pressing Alt+Shift+R for example. But seems that now in Lucid it doesn't work.

This 'Alt+Shift' for switching layouts that works as soon as it is pressed is a known issue, and I think it will take long to fix. You need to investigate the X.Org project, the 'XKB' or 'XKB2' components.

Personally I got used to using 'LShift+RShift' to switch layouts, which solves all these issues. It should take you about a week to get used to Shift+Shift and never look back :-).

---

