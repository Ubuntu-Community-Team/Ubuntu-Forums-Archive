---
title: "keyboard special keys not detected with xev"
date: 2006-05-20
forum: Desktop Environments
---

### Post by [S|G] on 2006-05-20
Hello, I have a cheap BenQ (6514 GX) keyboard that has 7 special keys on it. I have read tutorials about how to set up the special keys on X, but I have a problem: xev doesn't recognize those keys being pressed.

Any ideas about how can I fix this?

---

### Post by niviche on 2006-05-20
This explained well in this thread:
[http://www.pclinuxonline.com/modules.php?mop=modload&name=Splatt_Forums&file=viewtopic&topic=5224&forum=18](http://www.pclinuxonline.com/modules.php?mop=modload&name=Splatt_Forums&file=viewtopic&topic=5224&forum=18)

basically, open a terminal, type
```

dmesg - c

```

then the key that doesn't do anything, then the same "dmesg -c" thing. You will get a code for that key. You then can assign it to do something (check the first to last post in this thread).

---

### Post by [S|G] on 2006-05-20
Thanks niviche. However, I followed the guide and got this message:

```

diego@SnowGust:~/.kde/Autostart$ sudo dmesg -c
[4327384.288000] atkbd.c: Unknown key pressed (translated set 2, code 0xa5 on isa0060/serio0).
[4327384.288000] atkbd.c: Use 'setkeycodes e025 <keycode>' to make it known.
[4327384.476000] atkbd.c: Unknown key released (translated set 2, code 0xa5 on isa0060/serio0).
[4327384.476000] atkbd.c: Use 'setkeycodes e025 <keycode>' to make it known.
diego@SnowGust:~/.kde/Autostart$ setkeycodes e025 59
Couldnt get a file descriptor referring to the console

```

I tried some other values to setkeycodes but none worked. Also, I can't map the hex code directly (well, according to the guide, it was expected; I had to do the setkeycodes thing above). Any ideas about the "Couldnt get a file descriptor referring to the console" message?

---

### Post by [S|G] on 2006-05-20
Ok, I managed to fix the error message... I just needed to run setkeycodes as root. Now I have my special keys working, thanks a lot!

---

### Post by niviche on 2006-05-21
You're welcome, good that it worked out.

---

