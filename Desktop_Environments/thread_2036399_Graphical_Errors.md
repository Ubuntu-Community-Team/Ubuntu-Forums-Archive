---
title: "Graphical Errors"
date: 2012-08-01
forum: Desktop Environments
---

### Post by linuxyogi on 2012-08-01
Hi,
Problem is my Xubuntu installation shows a black cross in place of the mouse pointer. The window border is gone (minimize/maximize/close) Alt +Tab is not working.

---

### Post by Toz on 2012-08-01
Might be a corrupted cache session.

Try logging out, going to the first tty (Ctrl+Alt+F1), logging in to the text sessions, deleting your cache:
```
rm -rf ~/.cache/sessions
```
...(be extra careful with the above command - its a delete command), going back to the gui (Ctrl+Alt+F7) and logging in again.

Is this a fresh install of Xubuntu?

---

### Post by linuxyogi on 2012-08-01
> **Toz said:**
> Might be a corrupted cache session.

Try logging out, going to the first tty (Ctrl+Alt+F1), logging in to the text sessions, deleting your cache:
```
rm -rf ~/.cache/sessions
```...(be extra careful with the above command - its a delete command), going back to the gui (Ctrl+Alt+F7) and logging in again.

Is this a fresh install of Xubuntu?

Thanks a lot.

---

