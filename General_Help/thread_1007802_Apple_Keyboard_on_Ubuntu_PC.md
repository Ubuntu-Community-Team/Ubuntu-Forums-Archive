---
title: "Apple Keyboard on Ubuntu PC"
date: 2008-12-10
forum: General Help
---

### Post by Mega__ on 2008-12-10
I've found plenty of solutions to problems on this forum, so I think its time I give something back. I was in the market for a new keyboard and the apple keyboard really caught my eye. I did a quick search at the store and found nothing saying it wouldn't work in Ubuntu. After plugging it in, I found a few problems. First, no "Insert" key, which I missed greatly for pasting into terminal. More importantly I found that the numpad only functioned as a cursor control. After searching for a few hours I came across no clear fixes, but I did come across the keycode command. Here is a fix to allow the usage of the Apple keyboard in Ubuntu.

Put the following commands into the ~/.xmodmaprc 

```

 keycode 94 = asciitilde
 keycode 182 = Insert
 keycode 0x5A = 0
 keycode 0x57 = 1
 keycode 0x58 = 2
 keycode 0x59 = 3
 keycode 0x53 = 4
 keycode 0x54 = 5
 keycode 0x55 = 6
 keycode 0x4F = 7
 keycode 0x50 = 8
 keycode 0x51 = 9
 keycode 0x5B = period
 keycode 0x6C = Return
 keycode 0x56 = plus
 keycode 0x52 = minus
 keycode 0x3F = asterisk
 keycode 0x70 = slash

```


The number pad should now function properly. "Insert" is now mapped to F13 above the "Fn" key. Also, the tilde symbol is mapped to the key directly above tab. If you want to change which keys these are mapped to, you can experiment with the command "xev" to get the keycodes from different key presses. 


I hope someone finds this helpful, enjoy the classy keyboard! ):P

---

