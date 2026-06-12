---
title: "emacs is broken under Xglx"
date: 2006-08-21
forum: Desktop Environments
---

### Post by Burke on 2006-08-21
I installed Xgl and suddenly emacs won't work. Here's what it looks like.
[ATTACH]14632[/ATTACH]

When I load a regular GNOME session, it works fine. What's going on?

---

### Post by Burke on 2006-08-21
Ah, I fixed it. I had to insert this into ~/.Xresources:

Emacs*font: -*-sony-*-*-*-*-*-*-*-*-

---

