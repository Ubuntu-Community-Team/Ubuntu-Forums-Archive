---
title: "Rename strange behaviour after upgrade to 10.10"
date: 2010-10-16
forum: Desktop Environments
---

### Post by giropizza on 2010-10-16
Today I upgraded from 10.04 to 10.10 and I notice that the rename function is different from before. 
Now it select all the filename including the extension while before it select only the filename. How can I fix this problem? It's very uncomfortable rewrite the extension everytime or remove the extension from the selection.

Thanks

---

### Post by pebas on 2010-10-17
There's a bug in nautilus 2.32.0 when renaming using "List View" mode. 

Here's the bug report in launchpad: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/658555](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/658555)

You can use "Icon" or "Compact" until it get fixed (or an external file manager like ie: gnome-commander).

Hope it helps.

---

### Post by iDleR on 2010-10-17
> **pebas said:**
> There's a bug in nautilus 2.32.0 when renaming using &quot;List View&quot; mode. 

[...]

Thank God it's a bug. I thought it was a design choice and I redefined the concept of blasphemy.

---

### Post by telefono on 2010-10-21
I hope this will be fix soon : (

---

### Post by kakila on 2010-12-19
> **iDleR said:**
> Thank God it's a bug. I thought it was a design choice and I redefined the concept of blasphemy.

You said it, dude! In good words!

---

### Post by giropizza on 2011-02-09
But there's no solution? It's february and the problem isn't yet solved by the updates.
What I have to do to solve this?

Thanks in advance

---

### Post by Krytarik on 2011-02-10
You could in the meantime try

- Nautilus Elementary (it doesn't work for me, scrolling issue):
[http://www.makeuseof.com/tag/nautilus-elementary-simplifies-file-browsing-linux/](http://www.makeuseof.com/tag/nautilus-elementary-simplifies-file-browsing-linux/)

- or Thunar, it's in the official repos, looks stable so far

guide on how to replace it completely:
[https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)

---

