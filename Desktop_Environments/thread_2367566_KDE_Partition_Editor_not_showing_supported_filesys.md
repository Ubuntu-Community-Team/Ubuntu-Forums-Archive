---
title: "KDE Partition Editor not showing supported filesystems"
date: 2017-08-01
forum: Desktop Environments
---

### Post by Brandon_MacEachern on 2017-08-01
On two new machines, installed from the latest 17.04 Kubuntu 16-bit ISO, it appears that KDE Partition Editor is not properly showing the supported file system list.

Here's a screenshot showing what I mean.  It almost looks like this may be some problem regarding themes, because the them is certainly not Breeze.  In fact, I can replicate this by running systemsettings5 with kdesudo, no icons load, and the same wrong theme appear, and KDE Partition Editor by default, loads as super user.

What's going on here?

[http://i.imgur.com/PUJDeiY.png](http://i.imgur.com/PUJDeiY.png)

When I load partitionmanager from the terminal, it looks fine: [http://i.imgur.com/lCjWlI9.png](http://i.imgur.com/lCjWlI9.png)

But clearly when running it through the application menu, it is not.

EDIT:  Looks like adding the line: XDG_CURRENT_DESKTOP="KDE"
to /etc/environment solves this.

What package do I file this bug under?  Because it doesn't seem to be related to the KDE Partition Editor.

---

### Post by Brandon_MacEachern on 2017-08-03
*crickets*
Seriously, no one knows what package to file a bug under?  It's a clear usability feature when you can't even see the GUI elements.

---

### Post by vasa1 on 2017-08-03
If you don't get help here, try [https://www.kubuntuforums.net](https://www.kubuntuforums.net) or [https://forum.kde.org](https://forum.kde.org).

BTW, a plain bump is sufficient.

---

### Post by Brandon_MacEachern on 2017-08-04
Plain bumps are usually rude, a reason for the bump is sufficient in my book.

I filed a bug under partitionmanager, I'll let you guys sort it out.

---

