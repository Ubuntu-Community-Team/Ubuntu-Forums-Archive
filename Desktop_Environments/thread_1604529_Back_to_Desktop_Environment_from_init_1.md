---
title: "Back to Desktop Environment from init 1?"
date: 2010-10-24
forum: Desktop Environments
---

### Post by x19290 on 2010-10-24
Hello.

I have been using Debian desktop environment for years. There, I can sudo init 1; do maintenance; exit to desktop environment again. But when I `resume' from Ubuntu-10.10's maintenance mode, I can just Ctrl-Alt-F1 to login and there seems not an interesting process running.

What can I do?

Thank you.

Hiroki Horiuchi

---

### Post by Alessandro.g89 on 2010-10-24
after login, try
```
startx
```
you should get you DE ;)

---

### Post by x19290 on 2010-10-25
Sorry to be late.

I get it:) But DE through gdm and DE through startx are not exactly the same. For example, a speaker icon on the panel is disabled in the former. Such a difference is not acceptable.

What can I do?

Hiroki Horiuchi

---

### Post by x19290 on 2010-10-25
s/former/latter/****

---

### Post by Alessandro.g89 on 2010-10-31
you're right, that happened to me too. this should work better: 
```
sudo gdm
```

---

