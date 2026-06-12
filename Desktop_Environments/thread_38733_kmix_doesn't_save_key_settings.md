---
title: "kmix doesn't save key settings"
date: 2005-06-01
forum: Desktop Environments
---

### Post by NTolerance on 2005-06-01
I am trying to bind the multimedia keys on my laptop to the volume up/down/mute functions in kmix.  It accepts the keys, one of which is detected as Win+Ctrl+Alt+E.  The keys will then work until I restart KDE.  After doing so all the settings are lost and don't show up in kmix.  Any ideas?

---

### Post by thrift on 2005-06-01
You may want to look into using xev to get the scan codes for your keys and the xmodmap to remap these keys to things like F13 F14 F15 and the like.  

Add a script to do the xmodmap on KDE startup once you understand how xmodmap works, then bind the keys to kmix.  That should work a bit better.

Good Luck.

---

### Post by NTolerance on 2005-06-02
Hmm...the problem is that each key generates 4 different keypresses:

```
KeyPress event, serial 27, synthetic NO, window 0x2e00001,
    root 0x48, subw 0x0, time 1024459, (-297,177), root:(387,220),
    state 0x0, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyPress event, serial 30, synthetic NO, window 0x2e00001,
    root 0x48, subw 0x0, time 1024466, (-297,177), root:(387,220),
    state 0x40, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyPress event, serial 30, synthetic NO, window 0x2e00001,
    root 0x48, subw 0x0, time 1024472, (-297,177), root:(387,220),
    state 0x48, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyPress event, serial 30, synthetic NO, window 0x2e00001,
    root 0x48, subw 0x0, time 1024479, (-297,177), root:(387,220),
    state 0x4c, keycode 26 (keysym 0x65, e), same_screen YES,
    XLookupString gives 1 bytes: (05) ""
    XmbLookupString gives 1 bytes: (05) ""
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x2e00001,
    root 0x48, subw 0x0, time 1024493, (-297,177), root:(387,220),
    state 0x4c, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes:

KeyRelease event, serial 30, synthetic NO, window 0x2e00001,
    root 0x48, subw 0x0, time 1024501, (-297,177), root:(387,220),
    state 0xc, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes:

KeyRelease event, serial 30, synthetic NO, window 0x2e00001,
    root 0x48, subw 0x0, time 1024520, (-297,177), root:(387,220),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes:

KeyRelease event, serial 30, synthetic NO, window 0x2e00001,
    root 0x48, subw 0x0, time 1024520, (-297,177), root:(387,220),
    state 0x0, keycode 26 (keysym 0x65, e), same_screen YES,
    XLookupString gives 1 bytes: (65) "e"
```

 ]

---

### Post by thrift on 2005-06-02
You mean to say that is all from one key?

I'm a little confused, if you could clarify what you hit for each keycode it would be vey helpfull.

If it is from one key, does it generate all 4 at one press or does it vary for each press?

---

### Post by NTolerance on 2005-06-02
[QUOTE=thrift]You mean to say that is all from one key?

I'm a little confused, if you could clarify what you hit for each keycode it would be vey helpfull.

If it is from one key, does it generate all 4 at one press or does it vary for each press?[/QUOTE]

That code above is just from one key.  It generates all 4 at once everytime I press the button.

---

### Post by thrift on 2005-06-02
Wow.  Umm what I would try to do is find out if you hit the different keys if some of the keycodes shown ar the same or not, then if i found one field that showed differences per key and only came up once when the key was hit I would xmodmap to that.  You should look up your exact model of keyboard and see if anyone else is having the same issue.  To me, this type of thing is unique.

---

