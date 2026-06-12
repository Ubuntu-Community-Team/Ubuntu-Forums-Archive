---
title: "Super key not working*"
date: 2007-12-28
forum: Desktop Environments
---

### Post by shrndegruv on 2007-12-28
this is on an inspiron 6000.
In gnome, the super key (the windows key) works like a champ.
Im trying to try awesome wm, and it does nothing.  

Mod4 is the super key, right?

any help/insight is appreciated...

---

### Post by bingoUV on 2007-12-28
What do you expect it to do? Have you assigned some action to the key in awsome wm?

---

### Post by shrndegruv on 2007-12-28
Yes

by default Mod4+enter opens an xterm.

Am I correct in assuming the Mod4 is the super key (and that this is the windows key?)

---

### Post by bingoUV on 2007-12-28
May not be true. Let us verify. On command line, run the command xev. Press your windows key and keep it pressed. Look at the output of xev, the field root should be something like 0x73. Whatever it is, write it down.

Now run 
```

xmodmap -pm

```
In the output, look at mod4. It should include the thing you wrote down, e.g. 0x73(and maybe more keys) if mod4 is indeed the key you are trying to use.

---

### Post by shrndegruv on 2007-12-28
xev
```

KeyPress event, serial 31, synthetic NO, window 0x3e00001,
    root 0x52, subw 0x0, time 573717784, (1343,267), root:(1346,316),
    state 0x0, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,


```


xmodmap
```

mod4        Super_L (0x7f),  Hyper_L (0x80)

```

---

### Post by bingoUV on 2007-12-28
windows key does not seem to be the mod4 for you. What if you do the same in gnome?

---

### Post by shrndegruv on 2007-12-28
that was in gnome.  without the windows key, i cant open any programs in dwm/awesome

---

### Post by Perpetual on 2007-12-28
Have you tried going to System > Preferences > Keyboard and selecting Dell 6XXX (I believe that is an option) and restarting X (ctrl+alt+backspace)?

---

### Post by shrndegruv on 2007-12-28
there is 

dell
dell 101 key pc
dell lattitude

dell does not work

---

### Post by Perpetual on 2007-12-28
> **shrndegruv said:**
> there is 

dell
dell 101 key pc
dell lattitude

dell does not work

Hmm, maybe it's Fedora where I saw the Dell 6XXX.  I have a Latitude which is listed.  Did you try anything under Keyboard Preferences > Layout Options > Alt/Win key behavior?

---

### Post by shrndegruv on 2007-12-28
I dont see an option to map the win key to mod4

---

### Post by bingoUV on 2007-12-29
But you said it works fine in gnome? Why do you want an option to map the win key to mod4 in gnome?

---

### Post by mali2297 on 2007-12-29
> **shrndegruv said:**
> xev
```

KeyPress event, serial 31, synthetic NO, window 0x3e00001,
    root 0x52, subw 0x0, time 573717784, (1343,267), root:(1346,316),
    state 0x0, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,


```


xmodmap
```

mod4        Super_L (0x7f),  Hyper_L (0x80)

```

The output looks good, but did you get this when using Awesome (and not Gnome)?

---

### Post by shrndegruv on 2007-12-30
i cannot do anything in awesome because mod4 does not work.  I suppose i can change the awesomerc to use another key and run xev.

---

### Post by mali2297 on 2007-12-30
> **shrndegruv said:**
> i cannot do anything in awesome because mod4 does not work.  I suppose i can change the awesomerc to use another key and run xev.

Mouse-click with right button when cursor is on the root window (desktop) should also open xterm.

---

### Post by shrndegruv on 2007-12-31
mouse click did not work, but i changed to config temporarily to use alt (Mod1).

xev for super is 

> 
KeyPress event, serial 26, synthetic NO, window 0xa00001,
    root 0x52, subw 0x0, time 842996345, (750,297), root:(751,323),
    state 0x0, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,


and xmodmap
[quote]

mod4        Super_L (0x7f),  Hyper_L (0x80)

[quote]

---

