---
title: "XGL installed, ALT -key is not working"
date: 2006-06-21
forum: Desktop Environments
---

### Post by incidence on 2006-06-21
I installed XGL with this guide: 
[http://www.ubuntuforums.org/showthread.php?t=148860](http://www.ubuntuforums.org/showthread.php?t=148860)
and when I ran command: xmodmap /usr/share/xmodmap/xmodmap.fi
My alt key stopped working, like, I can't alt+tab, I can't drag windows by holding alt etc.

Here's the xmodmap.fi -file: [http://paste.ubuntu-nl.org/16165](http://paste.ubuntu-nl.org/16165)

---

### Post by seanleblanc on 2006-11-12
Did you ever get this fixed? I have the same exact problem.

---

### Post by Jenda on 2006-11-15
Very similar problem here... lemme try commenting out the alt bits in my xmodmap...

---

### Post by Jenda on 2006-11-15
Aha.
Fixed.
Open a terminal, type: [code]xev[code]press alt - it should give you something like (emphasis added):
> KeyPress event, serial 29, synthetic NO, window 0x3200001,
    root 0x52, subw 0x0, time 3978593716, (697,513), root:(711,565),
    state 0x0, **keycode 64** (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x3200001,
    root 0x52, subw 0x0, time 3978593805, (697,513), root:(711,565),
    state 0x8, **keycode 64** (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

Open your xmodmap file, find a line which says:
> keycode 64
or, more likely in hex:
> keycode 0x40
Comment that line out with a !, like this:
> ! keycode 0x40
Find the line that contains > Add Mod1 = Alt_L
And comment it out as well. Restart X with Ctrl+Alt+Backspace.

Done? :)

---

### Post by didobuntu on 2006-11-16
Hello,

Are you using Gnome or KDE.

If you use GNOME, the fix is to add the line 
"xmodmap /usr/share/xmodmap/xmodmap.(country keyboard, i.e. fr or es or dk ..etc)". If this does not resolve the problem then dunno.

If you use KDE, then the fix is not given by the above line. I saw a solution for this elsewhere here in this forum.

---

