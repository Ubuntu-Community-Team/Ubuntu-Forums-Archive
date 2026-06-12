---
title: "BZFlag Won't Run"
date: 2008-06-13
forum: Gaming &amp; Leisure
---

### Post by Abras on 2008-06-13
I grabbed it from the repos fyi. I usually try to solve simple things by myself but I don't even know where to begin with this one. So here's the error I get when I try to run it in the terminal.

X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x1a6
  Serial number of failed request:  148
  Current serial number in output stream:  150

---

### Post by Cannaregio on 2008-06-14
Try in a terminal, from /usr/games

```
bzflag -window -geometry 1280x1024+0+0
```

and let us know if it works

---

### Post by Abras on 2008-06-15
Yes, it did work, thanks. But am I going to have to run it in windowed mode from now on? Also, the mouse cursor doesn't go away, which is a bit annoying. Anyways, it works so thanks :)

---

