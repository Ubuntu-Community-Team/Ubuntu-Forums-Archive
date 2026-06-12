---
title: "Hardy: How do I make panels appear above all other windows when using Sawfish WM?"
date: 2011-02-23
forum: Desktop Environments
---

### Post by x1a4 on 2011-02-23
Hi,

I really would like to use the Sawfish window manager as my default WM in Xfce, but the panels, which I keep autohidden, are opening below other windows.  How do I make the panels always open above all other windows?  

Xfce version: 4.4.2
Sawfish version: 1.3.1


Thank you.

EDIT:  Solved it!  

The problem seems to occur only when the 'autohide' property is set.  When unset, Sawfish recognizes the panels as a dock just fine.  Luckily, the awesome nature of Sawfish allows me to set a multitude of rules for every window.  In this case I set the panel's depth to 16 which will guarantee they're always on top.  

I don't know why I haven't been using Sawfish as my default WM earlier, but it's the default now.  The amount of customization is huge.

---

