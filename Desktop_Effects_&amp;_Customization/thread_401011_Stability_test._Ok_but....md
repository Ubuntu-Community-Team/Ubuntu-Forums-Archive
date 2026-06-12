---
title: "Stability test. Ok but..."
date: 2007-04-04
forum: Desktop Effects &amp; Customization
---

### Post by f3ua on 2007-04-04
Hy guys,

i'm testing my ubuntu system with gnome and beryl ad default wm. I turned on the pc about 5 days ago, and left it open with a normal use (my normal use is about 10 programs open per desktop) and all works perfectly. The system is stable, a crash of a program didn't freeze the desktop manager... so i'm very happy.

BUT there is a little (big) problem. This morning I noticed that I have about 800 MB of allocated ram (not cache!) and about 214MB are allocated py the process Xorg. But if i open the same number of applications on a fresh boot session the memory amount is extremly lower.

Why? Is there some unallocated garbage in xorg?

Thanks

---

### Post by xopher on 2007-04-04
That's called a memory leak, and it's considered a bug. Fix it by restarting X.org (CTRL+ALT+Backspace or logging out/in)

---

### Post by f3ua on 2007-04-04
I'm a programmer and I know very well memory leaks. In your opinion I have to submit the bug?

---

