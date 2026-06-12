---
title: "Icon Help"
date: 2009-03-12
forum: General Help
---

### Post by untappedpilot2 on 2009-03-12
Every time I reinstall my system or change a bunch of things around I go through this problem when I try to get everything back to normal. Where are the icons kept in Ubuntu for the various programs that are installed? I know there are some in the /usr/share/icons area but that doesn't encompass all of them. Where can I look to find the rest of them? I would really like to know where some of the KDE based programs keep there icons as well. Thanks!

-Derek

---

### Post by MaxIBoy on 2009-03-12
As far as I know, it's all in /usr/share/icons.


If you drag and drop a launcher into a folder, then open it with a text editor, you can find the icon it's using.

---

### Post by untappedpilot2 on 2009-03-12
what are the exact paths for /usr/share/icons are they in exactly. And most of these launchers I'm making I make myself.. meaning I have to input the name, command, and icon path so I don't have a launcher to drag and drop into a folder.

---

### Post by MaxIBoy on 2009-03-12
Ah, that could be a problem.

In that case, I'd suggest using "find" to find the icons you need. 

As in "find /usr/share/icons office" or "find /usr/share/icons solitaire." 

You'll need to look for variations on the names, of course. But it should be easier than doing it by hand.

---

### Post by blackened on 2009-03-12
Some applications even still use the largely deprecated /usr/share/pixmaps directory (and subdirectories).

Still others put icons wherever the heck they want, like Firefox, the icon for which resides in /usr/lib/Firefox-*versionNum*/icons with a symlink in /usr/share/pixmaps.

For some real fun, try tracking down various status icons across different icon themes. 

The possible problems (listed from most to least likely) are:

**1.** Naming convention standards so decentralized and/or incoherent that many don't bother paying any attention to them.
**2.** No standards at all.
**3.** Icon creators and application developers exact a large amount of pride from crapping all over aforementioned standards, fictitious or otherwise.

1. and 3. might even be able to be switched, who knows. Keep in mind that this is all tongue-in-cheek and not meant to be taken to heart by those of you with thinner skins.

---

