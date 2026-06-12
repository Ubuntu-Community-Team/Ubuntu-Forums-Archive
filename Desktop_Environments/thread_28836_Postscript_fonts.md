---
title: "Postscript fonts?"
date: 2005-04-21
forum: Desktop Environments
---

### Post by GTKpower on 2005-04-21
How do I install Postscript fonts (.AFM and .PFB files) in Gnome 2.10 (Hoary)?

Seems I only get the option to install TrueType fonts.  I tried to drag my Postscript fonts into usr/share/fonts, but they don't show up.  Is there some other font installer I'm missing?

Any help is appreciated.

---

### Post by GTKpower on 2005-04-21
Never mind, I fixed it.  Have to open usr/share/fonts as root.  I downloaded a bunch of   Postscript-related files from the repositories, and there's a "Type 1" folder in the /fonts.  I just dragged the files into there.  

GNOME 2.10 (and Linux in general) still doesn't handle Postscript fonts all that well (has problem displaying and printing Old Style Figures from the same set as Roman figures), but it's adequate for my needs, so I'm happy.

---

