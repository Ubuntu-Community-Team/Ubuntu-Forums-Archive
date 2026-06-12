---
title: "Stumpwm"
date: 2009-03-26
forum: Desktop Environments
---

### Post by JGT on 2009-03-26
Hi

I've installed stumpwm on Ubuntu 9.04 and can select it from the login screen.

I can bring up the stumpwm menu "C-t ?" and emacs, but I can't seem to bring up a terminal, i.e. "C-t c" doesn't work - the frame remains stubbornly black. Therefore, I can't run any apps.

Is there something I'm missing? 

Cheers

John

---

### Post by JGT on 2009-04-17
...bump

---

### Post by dai_vernon on 2009-05-27
When you run the C-t ? command, look at what the C-t c command says.  It should say exec xterm.  For me, when I installed stumpwm through apt-get, it said exec x-terminal-emulator.  x-terminal-emulator isn't a command that does anything on a default system, so it has no response.  If you change it to say exec xterm, it should go fine.

You can also C-t ; and get to the colon prompt and type exec xterm there and get an xterm.

---

### Post by JGT on 2009-11-11
Thanks

---

