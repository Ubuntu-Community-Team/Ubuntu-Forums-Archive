---
title: "DosBox cycles up/down"
date: 2019-04-29
forum: Emulators
---

### Post by emians on 2019-04-29
Hi,

I installed DosBox form terminal on Ubuntu Studio.

It runs but I can't modify cycles nor frame skipping with the ctrl+Fn command.

I can modify cycles from the .dosbox file script txt, but hard to manage games with it.

Any idea how I could make this work?

cheers

---

### Post by TheFu on 2019-04-30
Just a thought, create a startup script for each program?
```

dosbox -conf gameA.conf

dosbox -conf gameB.conf

dosbox -conf gameC.conf
```

---

### Post by Holger_Gehrke on 2019-04-30
Ubuntu Studio ? I do believe this uses XFCE as its DE. Check that the window-Manager doesn't swallow up the key-combination. On my XUbuntu system ctrl-F11 was set to 'switch to workspace 11'  and ctrl-F12 to 'switch to workspace 12' (who sets up 12 workspaces ? Honestly !). Removing those definitions from the window manager settings made the keys work in dosbox.

Holger

---

### Post by deadflowr on 2019-04-30
*Thread moved to **Emulators***

---

