---
title: "Beryl manager"
date: 2007-03-03
forum: Desktop Environments
---

### Post by tagu on 2007-03-03
H&#305; all, I installed beryl couple of days ago but it does not work. I can run beryl manager but I cannot do the actions. By the way, there is something that is about beryl manager crash. When I right click the beryl manager and click "Launch fall back windows manager if beryl crashes" then beryl manager is disregarded and my default gnome window manager is in use. 

As a result, beryl does not work and I don't know how to make it work. If anyone knows here please help me.

---

### Post by petersjm on 2007-03-03
Can you paste this into a terminal and post the output, please?

```
glxinfo | grep direct
```

---

### Post by tagu on 2007-03-03
direct rendering: Yes

this is the result

---

### Post by tagu on 2007-03-03
Any help please...

---

### Post by petersjm on 2007-03-03
OKay, I don't know enough about getting these things to work, but can you try this? This is the only way I can get Beryl up and running (there must be an easier way!):

In terminal, type: beryl-manager --no-force-window-manager

Then hit enter and type: beryl-xgl --use-copy

Does that work? If it does, add both commands to your startup scripts under System > Sessions > Startup

---

### Post by tagu on 2007-03-03
Nope it did not work :(

---

### Post by petersjm on 2007-03-03
Have you installed a driver for your graphics card?

---

### Post by tagu on 2007-03-03
Yep ;

tagu@tagu-host:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6286 (8.33.6)

---

