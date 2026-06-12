---
title: "gnome keyboard mapping enter problem"
date: 2011-11-15
forum: Desktop Environments
---

### Post by matej.dunik on 2011-11-15
I've got general problem with keyboard of my notebook (lenovo g550). Both Enter keys (main one and numpad one) send signal of the numpad enter when pressed. No matter which I press I always get numpad enter signal.

This is hardware problem (I had the same when using win7 which was delivered with the pc). So  I'm not sure if there is any way for OS to distinguish between two enters, but if it's not, I would prefer the OS to assume I pressed the main Enter.

So is there any "mapping setting" which would change behavior of a specific key?

Thank you guys in advance.

---

### Post by Copper Bezel on 2011-11-17
Yeah, look into _[xmodmap]("http://www.xfree86.org/4.2.0/xmodmap.1.html")_. You can run a command to alter the keycode sent for any particular key, like 

```
xmodmap -e "keysym [whatever the key is sending] = Return"
```

and put that command in your Startup Applications to apply on login.

To get the keycode being sent by any particular key now, use [font="Courier New"]xev[/font].

---

