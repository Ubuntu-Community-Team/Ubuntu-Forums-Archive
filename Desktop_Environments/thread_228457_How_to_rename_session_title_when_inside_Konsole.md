---
title: "How to rename session title when inside Konsole"
date: 2006-08-03
forum: Desktop Environments
---

### Post by linuxa on 2006-08-03
Hi there

In Konsole, does anyone know of a way to rename the current Session Title using a terminal command of some sort?

Pretty much duplicating the way the right click -> rename session works. But using command line instead.

I run Kubuntu 6.06.

Thanks in advance.

---

### Post by linuxa on 2006-08-03
Never mind. Found it :D

echo -e '\033]30;New Name\007'

will rename the session to "New Name"

---

