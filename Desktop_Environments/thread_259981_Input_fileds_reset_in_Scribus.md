---
title: "Input fileds reset in Scribus"
date: 2006-09-18
forum: Desktop Environments
---

### Post by abelthorne on 2006-09-18
A problem has appeared on my system with Scribus-ng (1.3.3.3) : whenever I try to change anything in a input field (e.g. change the coordinates or the dimensions of a text box, or even creating a custom-size page), the value is reset to its minimal value : when creating a page, if I want to change the default value width to e.g. 120 mm, it gets 1 mm / if I create a text or image box in a document and want to move it to, say, x=100 mm & y = 230 mm, it gets x & y = 0.

I think the problem appeared after I installed / uninstalled KDE. It seems that it trashed my system far more that I imagined.

Any idea how to repair Scribus ? I already tried to uninstall and reinstall it, delete the .scribus directory, etc.

If I run it from a terminal, I get no specific error. The problem also appears if running it as root.

---

### Post by mrdocs on 2006-10-21
Known issue: [http://bugs.scribus.net/view.php?id=3826]("http://bugs.scribus.net/view.php?id=3826")

and Ubuntu bug: [https://launchpad.net/distros/ubuntu/+source/scribus/+bug/37711]("https://launchpad.net/distros/ubuntu/+source/scribus/+bug/37711")

---

