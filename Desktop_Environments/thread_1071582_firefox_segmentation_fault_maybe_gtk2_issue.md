---
title: "firefox segmentation fault maybe gtk2 issue?"
date: 2009-02-16
forum: Desktop Environments
---

### Post by bazzer on 2009-02-16
When opening a page with a smidge of javascript in it (onload=self.print();), sometimes Firefox crashes. Just completely shuts down. I've chased my tail a little, opening FF from the terminal, where the crash just causes 'Segmentation fault' to pop up.
I thought it may have been due to the gtk2 dialogue box provided by gtk2 so I found and fixed a few dependencies, but it seems to still be happening.

Are there any proper ways I can tell exactly what code is causing FF to crash? It's not *every* page that causes it to crash, but it is repeatable when it happens - when I try the page again.

---

### Post by jpmeijers on 2009-08-29
I currently have the same problem with my firefox. I tried reinstalling FF3.5, but it still gives the segfault on those specific pages.

Ubuntu 9.04
up to date to the ubuntu main repo's

Will add fix here if I find it.

---

