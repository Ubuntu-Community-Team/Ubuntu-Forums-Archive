---
title: "Remap cursor keys to home row"
date: 2010-01-07
forum: Desktop Environments
---

### Post by kaig on 2010-01-07
I just stumbled across this posting:
[http://duartes.org/gustavo/blog/post/home-row-computing](http://duartes.org/gustavo/blog/post/home-row-computing)

I wanted to get this working on my Ubuntu system, too.  I tried what comment 14 said.  This got CapsLock+h working as cursor left, but I couldn't mark text CapsLock+Shift+h.

I also tried xmodmap, with the same result: Marking text with the shift key didn't work.  But the basic cursor keys worked.

Here is a stripped ~/.xmodmap:

```
clear mod5
keycode 66 = Mode_switch
keycode 43 = h H Left NoSymbol Left
add mod5 = Mode_switch
```

I tried some variants: With ISO_Level3_Shift instead of Mode_switch.  With different "keycode 43" lines:

```
keycode 43 = h H Left
keycode 43 = h H Left Left
keycode 43 = h H Left NoSymbol
keycode 43 = h H Left 0x0000
```

With the first one of these, CapsLock+Shift+h did nothing, with the second one, CapsLock+Shift+h behaved the same as without Shift.

All hints appreciated.

---

