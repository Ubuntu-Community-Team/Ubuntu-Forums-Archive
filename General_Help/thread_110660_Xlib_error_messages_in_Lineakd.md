---
title: "Xlib error messages in Lineakd"
date: 2005-12-31
forum: General Help
---

### Post by mattG on 2005-12-31
Hello!

I use a Microsoft Natural Multimedia Keyboard and try to get the additional keys working in Ubuntu with the help of the lineak package.

After configuring lineakd with

```
lineakd -c MMNK
```

I tried to start the daemon. I then get a lot of error messages:

```
*** Xlib error caught ***
Major opcode of failed request: 33 (XKEYBOARD)
Minor opcode of failed request: 0 (XkbSetMap)
Resource ID of failed request: 96
Serial number of failed request: 13
Error code: 10
Type: 0
Maybe we should exit now?
*** Xlib error caught ***
Major opcode of failed request: 33 (XKEYBOARD)
Minor opcode of failed request: 0 (XkbSetMap)
Resource ID of failed request: 96
Serial number of failed request: 14
Error code: 10
Type: 0
Maybe we should exit now?
```

and so on...

I tried the lineakd version from the packet manager, the most current precompiled version from the lineak-Homepage and also the source code version. None of them worked.

What might be my problem here? Any ideas?

Many thanks in advance for your help!

---

### Post by pheaver on 2006-06-10
I have the exact same problem with my Logitech iTouch.  I am on and amd 64-bit system.

---

### Post by pheaver on 2006-06-19
* bump *

---

### Post by Shi Sun on 2007-05-02
Same Keyboard (MMNK), same problem :(

---

### Post by clemente on 2007-05-11
It won't help anyone, but with cherry cymotion master: Same problem.

---

