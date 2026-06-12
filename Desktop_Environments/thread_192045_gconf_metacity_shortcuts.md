---
title: "gconf metacity shortcuts"
date: 2006-06-08
forum: Desktop Environments
---

### Post by frying_fish on 2006-06-08
I am trying to make metacity perform a certain command when I press some of the keys on my laptop.


I want them to perform for example :
```

audtool playback-pause

```

when I press the "pause" key on my laptop.

The key is recognised, and it can be set in keyboard shortcuts to do the pause action, but the player doesn't interact with these yet, and I would like to make the keys just run the above command.

I have disabled the action in keyboard shortcuts so that there aren't conflicts, however, no matter what I set for the "run_command_1" key it doesn't seem to perform what I want it to when using my XF86AudioFOO keys.

It does however work if I set another keyboard combination, such as 
```
<ctrl><alt>p
```

That works fine, so does anyone know why it won't accept
```

XF86AudioNext

```
as the key to press to perform this action?

---

### Post by frodon on 2006-06-08
I think it's not seen as a valid keycode, use **xev** to know the valid keycode for this key.
You will get an output like that :  > KeyRelease event, serial 29, synthetic NO, window 0x3a00001,
    root 0x113, subw 0x0, time 4022236, (565,168), root:(583,316),
    state 0x50, keycode 115 (keysym 0xffeb, **Super_L**), same_screen YES,
    XLookupString gives 0 bytes:

---

### Post by frying_fish on 2006-06-08
ok, so they have "NoSymbol" I think
```

KeyPress event, serial 26, synthetic NO, window 0x3a00001,
    root 0x4c, subw 0x0, time 3021471675, (406,343), root:(426,488),
    state 0x0, keycode 153 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 26, synthetic NO, window 0x3a00001,
    root 0x4c, subw 0x0, time 3021471675, (406,343), root:(426,488),
    state 0x0, keycode 153 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:

```

this is for one of the keys,  however, when in the keyboard shortcuts in preferences if I press this same key it shows up first time with a hexcode
```

0x99

```
and then if I press it again it calls it XF86AudioNext.  So where do I go from here.

---

### Post by frodon on 2006-06-08
It's quite strange, sorry i have no idea there.
This guide may provide you some workarounds : [http://doc.gwos.org/index.php/MultimediaKeys](http://doc.gwos.org/index.php/MultimediaKeys)

---

### Post by frying_fish on 2006-06-08
That guide provided exactly what I needed to get it to work correctly,  thank you very much. Now when I get back off holiday I can do the same thing to my desktop computer that has a remote (if I can't get lirc to do what I want with it).

---

