---
title: "Grub help default boot!"
date: 2006-08-28
forum: Desktop Environments
---

### Post by chuckyp on 2006-08-28
Alright I've edited grub's menu.1st so that windows boots by default (the wife would kill me otherwise).  However, anytime the kernel updates I have to re-edit the menu.1st to change the option back to windows.  Is there anyway to set it so that it will always default to windows regardless of its position on the list.  Hopefully the question makes sense to someone.  I see something in grub about 'saved' and 'savedefault' but I don't quite understand it.

---

### Post by reacocard on 2006-08-28
just move (or copy) the windows section in menu.lst to above the "Debian automagic kernel" divider. now set the default to 0. XP will now always be first on the menu, and the default.

---

### Post by h00s on 2006-08-28
In /boot/grub/menu.lst see option:
```

default         0

```
That set the default option where first is numbered with 0.

But, I suggest that you backup your menu.lst to something like menu.lst_safecopy and when kernel updates just copy back menu.lst_safecopy to menu.lst

---

### Post by chuckyp on 2006-08-28
That makes sense.  Sometimes I find myself over thinking problems.

---

