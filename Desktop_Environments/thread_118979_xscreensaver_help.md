---
title: "xscreensaver help"
date: 2006-01-18
forum: Desktop Environments
---

### Post by Cybercool on 2006-01-18
Hello guys,

I want the next command to be run!!
I want to run the command:
xscreensaver-command -lock

But because i run the program in terminal (not in X) it doesn't work.
I have seen an other command: xscreensaver-command -lock -display host:display.screen

My question is, does this work from terminal (not in x)
And how does it work. i tried multible settings:

xscreensaver-command -lock -display 0:0
xscreensaver-command -lock -display 127.0.0.1:0.0

and some more.

Who can help me with this?

---

### Post by psychicdragon on 2006-01-18
It won't work outside of X.

---

### Post by Cybercool on 2006-01-18
[QUOTE=psychicdragon]It won't work outside of X.[/QUOTE]


isn't there an other way to call x or something??

---

### Post by psychicdragon on 2006-01-18
You want to start X just to lock the screen? Why not just log out?

---

### Post by 23meg on 2006-01-18
Try this ```
xscreensaver-command -display :0.0 -lock

```

---

### Post by Cybercool on 2006-01-18
[QUOTE=23meg]Try this ```
xscreensaver-command -display :0.0 -lock

```[/QUOTE]

When i try that command i get the next thing!!:

Xlib: connection to ":0.0" refused by server
Xlib: no protocol specified!!

---

