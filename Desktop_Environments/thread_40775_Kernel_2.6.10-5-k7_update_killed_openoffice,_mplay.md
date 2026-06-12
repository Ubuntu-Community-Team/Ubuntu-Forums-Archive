---
title: "Kernel 2.6.10-5-k7 update killed openoffice, mplayer?"
date: 2005-06-10
forum: Desktop Environments
---

### Post by wylfing on 2005-06-10
After updating linux-image-2.6.10-5-k7 to 2.6.10-34.2, I seem to have lost openoffice and mplayer. Both of those applications segfault on startup. I installed openoffice2 but that segfaults too. I can stare at a strace all day and not really know what it's telling me, so I'll post it here:

[http://www.wylfing.net/ooo-strace.txt](http://www.wylfing.net/ooo-strace.txt)

I've tried reinstalling, but that's about as far as I can go without knowing any more about the problem. Anyone have a clue?

---

### Post by desdinova on 2005-06-10
[QUOTE=wylfing]After updating linux-image-2.6.10-5-k7 to 2.6.10-34.2, I seem to have lost openoffice and mplayer. Both of those applications segfault on startup. I installed openoffice2 but that segfaults too. I can stare at a strace all day and not really know what it's telling me, so I'll post it here:

[http://www.wylfing.net/ooo-strace.txt](http://www.wylfing.net/ooo-strace.txt)

I've tried reinstalling, but that's about as far as I can go without knowing any more about the problem. Anyone have a clue?[/QUOTE]
 I've just installed the same k7 - both OO2 and mplayer working fine - sorry

---

### Post by wylfing on 2005-06-10
Wrong culprit. Almost at random, I tried glxgears, which segfaulted. So somehow my OpenGL libs got boffed, and Ooo.org uses them. I uninstalled and reinstalled my nvidia drivers and all seems well now.

---

### Post by desdinova on 2005-06-10
[QUOTE=wylfing]Wrong culprit. Almost at random, I tried glxgears, which segfaulted. So somehow my OpenGL libs got boffed, and Ooo.org uses them. I uninstalled and reinstalled my nvidia drivers and all seems well now.[/QUOTE]
 Now you got me paranoid - just ran it myself - glxgears seems ok ;-)

---

### Post by Joeb on 2005-06-10
[QUOTE=wylfing]Wrong culprit. Almost at random, I tried glxgears, which segfaulted. So somehow my OpenGL libs got boffed, and Ooo.org uses them. I uninstalled and reinstalled my nvidia drivers and all seems well now.[/QUOTE]


Yeah, that's something to remember, if you've installed commercial video drivers.  Since they are tied directly to the kernel, whenever you upgrade your kernel, you need to redo your video drivers (with the free drivers, you don't have to do this).  I'm not sure you actually had to uninstall and reinstall instead of just run the nvidia configuration (it's run automatically when installing, though).

---

