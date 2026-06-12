---
title: "weird remote desktop issue"
date: 2008-12-31
forum: General Help
---

### Post by Evil Wayz on 2008-12-31
This happened on not one but two of my computers.

One I crashed and the other i restarted , both while using remote desktop.

WHen they rebooted, I have no background.  I tried unchecking hte disable background in remote desktop box, didn't work.

When I log into these computers, the background shows up, only to immediately revert to the color that I would see if I was remotely connected.

IT's annoying and I want my desktop back.  Anyone have any ideas?

---

### Post by Retaliation on 2009-01-11
Hey, I too had this problem until very recently. In the console, type:

```
gconf-editor
```

then navigate to desktop > gnome > background and check the draw background box

hope that works for you! :p

---

### Post by Evil Wayz on 2009-01-19
It did work!!!  I just wish I knew what made it do that in the first place.

---

