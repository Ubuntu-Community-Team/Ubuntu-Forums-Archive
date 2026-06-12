---
title: "Ubuntu won't finish boot"
date: 2009-04-25
forum: General Help
---

### Post by joey-elijah on 2009-04-25
I'm using Ubuntu Jaunty x64bit.

I installed KDE-Desktop, which installed fine. However, upon logging out, so i could change session to try kde, is when this issue came about.

Instead of logging out i got 'text' on screen about powermanagement. I normally get this for a split second or two logging out, however this time it stuck. 

I hit Alt+f2 (no idea why!) which dropped me to log in. However it then just froze. 

I had no choice but to hard-reboot.

Botting back up it just gets stuck on the splash screen about 1/2 way through the progress bar.

Booting into recovery mode also seems to have issues and it too just freezes, ending on:

run-init: /sbin/init: No such file or directory
Kernel Panic - Not Syncing: Attempted to kill init!
Dumping ftrace buffer:
(ftrace buffer empty)

So it's missing 'init' which causes it to have a nervous breakdown and 'freeze', yes?

Any ideas how to fix this? What did i do wrong in the first place?

---

### Post by joey-elijah on 2009-04-25
After reading around various threads, confirming that my 'init' file was still intact, the right 'size' and where it should via a live disc, it seems there's no alternative to a fresh install.

I hope i don't cause this to happen again. I'd love to try KDE out, but i can't keep reinstalling Ubuntu everytime i try to install it.

---

