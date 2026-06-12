---
title: "Clipboard data &amp; Gnome"
date: 2005-05-25
forum: Desktop Environments
---

### Post by jcooper on 2005-05-25
As most are aware, clipboard management in Gnome is a bit hit and miss. Applications only support copy + paste while they are open. Gnome-Clipboard-Manager was an initial attempt at rectifying this problem, but it has [serious shortcomings](http://pvanhoof.be/blog/index.php/2005/05/24/29-combatting-the-many-x11-clipboard-issues) .

I've just read [this post](http://svenfoo.geekheim.de/index.php/2005-05-24/clipboard/) at Planet Gnome and would like to open discussion on not only including this functionality with the next release of Ubuntu, but also providing support for it in Hoary as an official Ubuntu package.

[Code](http://people.imendio.com/andersca/archives/clipboard-manager-0.3.tar.gz)  for the new and improved clipboard manager is available. Not being a c programmer myself, would it take a lot of effort to update applications to use the [fd.o spec](http://www.freedesktop.org/wiki/Standards_2fclipboard_2dmanager_2dspec) and GTK+ API ([gtk-clipboard-set-can-store](http://developer.gnome.org/doc/API/2.0/gtk/gtk-Clipboards.html#gtk-clipboard-set-can-store))?

Perhaps a bounty would be appropraite for this sort of work? Or is it a case of waiting for applications to use the API, and more importantly, move to GTK+ 2.6?

---

### Post by Burgundavia on 2005-05-25
Clipboards are messy issue, due to lots of legacy apps. Basically you need a clipboard that ties in with what exists transparently.

They haven't nailed this one down, and I doubt there will be something in the Breezy timeframe, but possibly Breezy+1

Corey

---

