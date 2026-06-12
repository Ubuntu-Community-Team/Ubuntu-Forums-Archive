---
title: "KMenu icons lost"
date: 2009-04-19
forum: Desktop Environments
---

### Post by James78 on 2009-04-19
I run Kubuntu Intrepid Ibex (8.10), and I was playing with Lancelot, when I realized that some of the sub-menus that had many icons in them wouldn't scroll down. I proceeded to try to fix it, but was never successful. Somewhere along the line, I was in my KDE Menu Editor, and I had already tried various things like restoring the menu, which I didn't fix anything. Well, I eventually deleted it all, then restored it again, simply to find out that most of my KDE applications now do not have links to them anymore! My custom application links I can handle putting back in, there's like 2, but I'm missing most of my program entries now! Is there any possible way I can get this all back. Also, anyone know the issue with Lancelot, and it not showing the scrollbar..?

---

### Post by txcrackers on 2009-04-20
Look in the directory $HOME/.config/menus

This contains your basic edits of the menus and any "extra" things you've installed (like Wine programs). If you delete everything in this directory, you **should** have a clean menu. Make a backup copy of this directory just in case.

---

