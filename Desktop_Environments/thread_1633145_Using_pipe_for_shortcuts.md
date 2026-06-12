---
title: "Using pipe for shortcuts"
date: 2010-11-28
forum: Desktop Environments
---

### Post by tetebueno on 2010-11-28
Hey, maybe a silly question, but I'm trying to set a shortcut using the pipe key ("|", this one...) like "<Ctrl>|" and no luck. Is there any special way to set this like <Ctrl><Pipe> or <Ctrl>|| or something?
Thanks.

Cheers.

---

### Post by asmoore82 on 2010-11-28
For me, the pipe on the keyboard is on the backslash key: <Ctrl>backslash

---

### Post by tetebueno on 2010-11-28
No luck with that one, thanks though.
I have a latin american keyboard where the pipe key is the one just below the Esc key, above the Tab key and by the side of the "1" key. Pressing just that one you get "|", holding shift you get "°" and with AltGr you get "¬".
Maybe this helps... me.
Cheers.

---

### Post by tetebueno on 2010-12-26
Got it!
Run: ```
xev
``` ... in a terminal and a window will popup, whenever you hit a key you'll get info in console, when hitting the pipe key I got:


```
KeyPress event, serial 33, synthetic NO, window 0x5a00001,
    root 0x1a7, subw 0x0, time 44557160, (-500,-562), root:(760,103),
    state 0x10, keycode 49 (keysym 0x7c, bar), same_screen YES,
    XLookupString gives 1 bytes: (7c) "|"
    XmbLookupString gives 1 bytes: (7c) "|"
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x5a00001,
    root 0x1a7, subw 0x0, time 44557244, (-500,-562), root:(760,103),
    state 0x10, keycode 49 (keysym 0x7c, bar), same_screen YES,
    XLookupString gives 1 bytes: (7c) "|"
    XFilterEvent returns: False

```

... what you see in the line that begins with "state", just before closing parenthesis is how the key is called, in this case "bar".
I needed to configure parcellite with the shortcut ctrl+| so it ended like: "<Ctrl>bar".
Hope this helps someone else.
Cheers.

---

