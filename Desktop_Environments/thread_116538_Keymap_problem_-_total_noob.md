---
title: "Keymap problem - total noob"
date: 2006-01-12
forum: Desktop Environments
---

### Post by cdanr on 2006-01-12
Let me preface by saying I'm a total Ubuntu noob but I'm having a very annoying problem. I'm using Breezy 5.10and I have my keyboard layout set to US-104 (MS Natural Keybd Pro) and all the keys and even multimedia keys seem to work except for the tilde key. That key produces the grave (`) symbol whether I shift or not. I've had a look at the layout file in the /etc/X11/symbols directory and it seems to be properly set to asciitilde symbol but I can't seem to get it to work.

If anyone has any ideas I'd appreciate it.

Cheers,

---

### Post by frodon on 2006-01-13
You can try to remap your key.

Run "xev" and press the key you want to use and get its keysim, exemple of a xev output : ```
KeyRelease event, serial 26, synthetic NO, window 0x3000001,
    root 0x46, subw 0x0, time 1191598958, (119,52), root:(1217,847),
    state 0x10, **keycode 49** (keysym 0x60, grave), same_screen YES,
    XLookupString gives 1 bytes:  "`"
```

Then run this command to map the key :```
xmodmap -e "keycode xx = grave notsign"
```(replace xx by the keycode of the key you want to map).
Add this command in the "startup session commands" or in your .bashrc to do it automatically on each startup.

Let me know if it works.

---

