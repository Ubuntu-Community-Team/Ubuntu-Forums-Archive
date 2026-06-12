---
title: "Oops, screwed up my gnome-panel configuration and cannot restore it..."
date: 2008-03-15
forum: Desktop Environments
---

### Post by Keyper7 on 2008-03-15
Hi guys, I hope you can help me in this embarassing issue.

I tried to recompile the gnome-panel package to solve this bug.

  [https://bugs.launchpad.net/evolution/+bug/42115](https://bugs.launchpad.net/evolution/+bug/42115)

So I downloaded the source and patch from packages.ubuntu.com and, silly me,
I forgot to apply the patches before compiling and installing. While
I'm not sure if that was the cause, I ended up with a menu bar with the original
gnome layout (like the one debian uses, with "Exit" and "Shutdown" buttons, without
the "about Ubuntu" button, etc.).

I tried to solve this issue by compiling with patches and installing again. Didn't work.
Tried installing the .deb. Didn't work. I guess it's just a configuration issue, but where
is the corresponding configuration file or gconf entry?

Oh, by the way, the "add panel applet" window layout was affected too. Probably
other applets were too, but I didn't check each one.

Thanks in advance,
-Keyper7

---

### Post by Keyper7 on 2008-03-16
*bump*

Any ideas on this?

---

