---
title: "MX Revolution + xbindkeys/xmacroplay - Executing mouse-context sensitive key macros"
date: 2008-12-28
forum: General Help
---

### Post by MdSalih on 2008-12-28
Hello all,

I have currently set up my MX Revolution mouse to run specific key macros when I press specific buttons through xmacroplay.

For example, I have configured two of the keys to rotate my desktop:
```

#Rotate Right
"echo 'KeyStrPress Alt_L KeyStrPress Control_L KeyStrPress Right KeyStrRelease Right KeyStrRelease Alt_L KeyStrRelease Control_L' | xmacroplay :0"
b:13

#Rotate Left
"echo 'KeyStrPress Alt_L KeyStrPress Control_L KeyStrPress Left KeyStrRelease Left KeyStrRelease Alt_L KeyStrRelease Control_L' | xmacroplay :0"
b:15

```

However, I wanted to know if I could make this context sensitive, so if I hit a button and my mouse was hovering over a Firefox window, it'd run a different key macro than if my mouse had been hovering over a gnome terminal or just the desktop (i.e no window).

As I'm effectively running a command when a button is pressed, it seems it should be possible to write a script to do this, however I don't know how I could get information about the active window through the command line :(. Could anyone point me in the right direction, or let me know if there's a way to get the window my mouse is hovering over from the command line?

Note, I'm running gnome.

Thanks in advance.

MdSalih

---

### Post by MdSalih on 2008-12-29
Bump...

MdSalih

---

