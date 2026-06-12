---
title: "[KDE] Window flashes when scrolling?"
date: 2007-01-27
forum: Desktop Environments
---

### Post by Shane N on 2007-01-27
When I use Konqueror or any application where I need to scroll at all, the application seems to refresh it everytime. It makes me feel like I'm trying to run windoze XP on a 64MHz machine with 16Mb of memory. I scroll, it redraws/refreshes the contents.

This a common problem? Or did I really screw something up?

I recently uninstalled compiz & beryl and reinstalled xserver-xorg. After fighting just to get it working again, this is the result.

Any ideas?

---

### Post by taurus on 2007-01-27
When you reinstalled xserver-xorg again, did you remember to install a driver for your graphic card?  That could be the problem there.

---

### Post by Shane N on 2007-01-27
You mean vesa != fglrx? ;) Thanks for the tip, sir.

That fixed that. I do have another question. What would cause kmix to pop up every time I login asking for root access?

---

