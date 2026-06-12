---
title: "How to disable gnome-shell?"
date: 2010-01-23
forum: Desktop Environments
---

### Post by user333 on 2010-01-23
I like the idea of gnome shell, but I'm not quite so sure I will actually like it, and I am really not so sure about entering "gnome-shell --replace" without knowing how to undo that... Could someone tell me how I would disable it and revert back to regular gnome if it slows my computer too much?

---

### Post by MichaelRX8 on 2010-01-23
When you restart it will go back to normal untill you do "gnome-shell --replace" again.

---

### Post by MichaelRX8 on 2010-01-23
Also, I always have to enter "gnome-shell --replace" twice to get it to change completely (don't know if this is just me).

---

### Post by user333 on 2010-01-23
Thanks for the reply :D But is there a command in case this doesn't work?

---

### Post by dyltman on 2010-01-24
> **user333 said:**
> Thanks for the reply :D But is there a command in case this doesn't work?

If it wouldn't work I think you'd get a blank screen.

Really if it doesn't work it's just too reboot the computer.

---

### Post by VeeDubb on 2010-01-25
> **user333 said:**
> Thanks for the reply :D But is there a command in case this doesn't work?

I know that adding "--replace" at the end of a command sounds serious, but it's not.  All that does, is tell gnome shell to "replace" the currently running window manager.  It does not make any changes to your file system, and has absolutely ZERO chance of sticking after a reboot.

Also, all you have to do is go back to the terminal window you used to enter "gnome-shell --replace" and hit ctrl-c and your original desktop pops right back up.

---

### Post by ementos on 2010-08-28
Ok... but you can also (when gnome-shell is run) run terminal, write "gnome-shell --replace" again and next to ctrl+c. Normal Gnome back!

---

