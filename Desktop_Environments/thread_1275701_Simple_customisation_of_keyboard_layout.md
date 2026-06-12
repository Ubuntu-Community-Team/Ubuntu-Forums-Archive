---
title: "Simple customisation of keyboard layout"
date: 2009-09-26
forum: Desktop Environments
---

### Post by brianmc on 2009-09-26
I have a fairly standard international keyboard layout. There's the € symbol on the "5" key and I have that working finally.

However, I'm now in the UK and would also like to get the pound sign, say via Alt-Gr 4 (to match that having the $ on it and being a sensible place to get my currency symbol.

I don't want to have to create a full-blown custom layout. What's the simplest way to achieve my goal? All the shortcut setup stuff I see is for key combinations to execute commands/launch programs.

---

### Post by bobince on 2009-09-26
I'm not aware of a *simple* way... I did it by editing ‘/usr/share/X11/xkb/symbols/(country code)’; you can change the layout there or add your own (if the latter, you'll then have to add it to the ‘/usr/share/X11/xkb/rules/evdev.*’ (and possibly base.*) files before you can pick it from the keyboard prefs interface.

If it's only the pound sign you're worried about it's probably far easier to just use one of the existing methods. If you're using the standard US keyboard you already have £ on Shift+AltGr+4 which is nearly where you want it. There's also the Compose key: Compose,L,= gives you £; Compose,E,= is €.

---

### Post by brianmc on 2009-09-26
Well, for now I've settled for turning the left Windows key into compose.

That way I can deal with all the European accented characters too, at least on the rare occasions I need them.

---

### Post by julio prada on 2009-10-16
Hi, every time somebody tells me an email over the phone, i can not type the @.
Its a "small" issue if you dont multiply it by the times you have to type an @.
I would love to exchange the "[" symbol, that I NEVER use.

Shouldnt it be as easy as going to the "english" configuration file and exchanging the 2?

Please help


Note:
Spanish keyboards are worse, they have the ç sign that is used only in some part of Spain as a first key, and for the @ you need both hands! (AltGr-2)

---

