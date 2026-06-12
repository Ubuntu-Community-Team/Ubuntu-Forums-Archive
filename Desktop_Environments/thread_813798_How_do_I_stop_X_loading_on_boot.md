---
title: "How do I stop X loading on boot?"
date: 2008-05-31
forum: Desktop Environments
---

### Post by neilneil2000 on 2008-05-31
A while ago I installed Mythbuntu on my machine and all was lovely, since then I have ended up using the machine as a headless server and used UPnP to access the media on it.

I have recently switched out the hardware for a new Intel Atom board and everything works fine except X won't load and has a hissy fit on boot.

How can I stop it trying to load X?

I am guessing something like removing gdm or x11-common from /etc/init.d might do the trick but I don't want to brick my server!

---

### Post by Aearenda on 2008-05-31
Unless Mythbuntu does something different from ordinary Ubuntu, X is started as part of the GDM startup, linked in /etc/rc2.d. I usually just do ```
sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/K30gdm
```when I want to disable it (there are better commands to do this 'properly' but I can never remember them) and ```
sudo mv /etc/rc2.d/K30gdm /etc/rc2.d/S30gdm
``` to put it back.
On your system the number in the name (30 here) may be different.
Doing this won't break your system.

---

### Post by neilneil2000 on 2008-05-31
Thanks very much I'll give it a whirl!

---

