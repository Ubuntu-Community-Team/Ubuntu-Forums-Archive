---
title: "Trying to edit system files...."
date: 2005-04-01
forum: Desktop Environments
---

### Post by waxle on 2005-04-01
I am trying to alter my PCMIA\Config.opts file to include support for my D-Link wi-fi reciever. Instructions are included at [http://tuxmobil.org/pcmcia_ci10092.html](http://tuxmobil.org/pcmcia_ci10092.html) . However, when I try to paste the edit over the original file, I get a "Permission not available, not the owner of this file". However, I am logged in as a root user. Help!

---

### Post by lukem on 2005-04-01
Sounds like you may not be root.  Try

sudo gedit filename

that should do it.  You might want to make a backup copy of the original first.  

good luck

---

