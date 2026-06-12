---
title: "Stalled gnome-panel"
date: 2009-02-26
forum: Desktop Environments
---

### Post by skotos on 2009-02-26
I run Compiz with a linked second monitor (another LCD or the TV as well).
In the last few weeks a strange problem arose on my laptop.

If Firefox is open on a monitor, I cannot open on the second one, that is: once you have called it on an X display, it cannot be called in the other; whatsmore, a popup with just an ok button comes up and never goes away, the gnome-panel instances seem to be locked and you cannot navigate any menu, nor click onto any applet in them.

The rest runs fine: the open applications are responsive, the keyboard regularly answers any shortcut...

If I have to regain control over the gnome-panel and make the empty popup disappear, I have to go to the command line and issue a ```
kill `pidof gnome-panel`
```Any suggestion on  what is going on? Thanks in advance

---

