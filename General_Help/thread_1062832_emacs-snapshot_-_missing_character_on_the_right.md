---
title: "emacs-snapshot - missing character on the right"
date: 2009-02-07
forum: General Help
---

### Post by regua on 2009-02-07
So, I've been using Emacs for some time, and decided to try the emacs-snapshot package to get the fancy fonts. I've read some tutorials on the intertubes, and created a file:

~/.Xresources
with the content: "Emacs.font: monospace-10"

The problem is that when wrapping lines, Emacs should display a small wrapping symbol both on the left and on the right side of the text. When launching emacs-snapshot, the symbol and one character on the right seems to be missing. When I start manually resizing the Emacs window, they appear.

I've attached two screenshots: one right after launching emacs-snapshot, and one after resizing the window and then going back to its initial size.

What can be the problem here? Thanks.

[img]http://img19.imageshack.us/img19/8819/emacs1ep4.png[/img]

[img]http://img19.imageshack.us/img19/5069/emacs2mg8.png[/img]

---

### Post by regua on 2009-02-07
Okay, I've just found out that this happens only if the toolbar is removed. A 'solution' is to remove the menu bar as well, apparently the margin shows correctly then.

---

