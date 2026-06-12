---
title: "Conky not working..."
date: 2010-06-15
forum: Desktop Environments
---

### Post by c0rsana on 2010-06-15
Ubuntu 10.4, working nVidia graphics card w/ driver.
I tried:
```
sudo apt-get install conky
```
it installed, I created a file in the $HOME directory with the correct prefix and configuration settings...at least I think they're the right configuration settings...

Anyway, when I try to run it from the terminal I get this:
```
c0rsana@c0rsana-laptop:~$ conky
Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
	This program is calling the Imlib call:

	imlib_context_free();

	With the parameter:

	context

	being NULL. Please fix your program.

```

Any way to fix this? Conky looks and sounds awesome, but so far I've failed to determine why it won't run...

---

### Post by gingivere0 on 2010-06-15
can you post the contents of your .conkyrc?

---

### Post by c0rsana on 2010-06-15
Wow, nevermind... Turns out reinstalling it reset the .conkyrc file. Who knew? o.O

---

