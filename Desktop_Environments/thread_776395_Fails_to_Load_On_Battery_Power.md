---
title: "Fails to Load On Battery Power"
date: 2008-04-30
forum: Desktop Environments
---

### Post by LavianoTS386 on 2008-04-30
...Once AC is plugged in gnome then proceeds to load.

Anyone have any ideas what could be causing it?

Asus Eee PC

---

### Post by LavianoTS386 on 2008-05-01
Okay I've gone into fail safe terminal session and tried "startx" and got:

```
Fatal Server error:
Server is already active for display 0
If the server is no longer running, remove /tmp/.X0-lock and start again.
```


I did so and then tried again then X loaded. With AC power in. But on battery it's the same ad before gnome will not load until the AC is plugged in.

So how do I find out what's going on with gnome?

---

### Post by russo.mic on 2008-05-01
wierd.  Maybe this is a HAL issue?  or ACPI?

Type acpi from a terminal with the AC plugged in and give the output.  Then, why don't you plug in the AC, then unplug the AC and do it again?

Russo

---

