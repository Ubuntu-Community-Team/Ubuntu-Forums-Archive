---
title: "[SOLVED] blank theme &amp;quot;customize&amp;quot; menu in Gutsy"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by berZirker on 2007-10-21
Just installed ubuntu 7.10 64 on my emachines m6809.  Nearly everything is working beautifully.  One remaining issue is the theme menu.  The "Appearances Preferences" window acts very sluggish (to the point that, if any other window started acting like that, I would think it was frozen and reboot) and when I click on customize it brings up a window (not sluggishly for some reason) which has no information.  If anybody can give me a lead as to why this might be it would be greatly appreciated.  Anybody else having this problem too?

I ran TOP just to check, and it showed the user window "Appearances Preferences" using over 90% of the CPU.  Am I really the only one having this problem?

In case anybody needs it, I solved this problem with
> sudo apt-get remove gtk-qt-engine

Thanks to Askeptykal and eltadcirad1on this post:
[http://ubuntuforums.org/showthread.php?t=574463&highlight=gutsy+appearances](http://ubuntuforums.org/showthread.php?t=574463&highlight=gutsy+appearances)

---

