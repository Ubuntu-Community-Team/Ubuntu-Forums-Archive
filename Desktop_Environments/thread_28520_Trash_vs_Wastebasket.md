---
title: "Trash vs Wastebasket"
date: 2005-04-20
forum: Desktop Environments
---

### Post by matthewn on 2005-04-20
I've got two machines running Hoary. One has been running Hoary since before the final release, but has been updated to all the latest packages. On that machine, the trash applet in the panel is called Wastebasket, and when I select "Add to Panel..." the trash item in that dialog is called Wastebasket.

On the other machine, which had the Hoary final release installed on it directly, the trash applet is called Trash, and the selection for it in "Add to Panel..." is also called Trash.

Why the discrepancy? How to fix? I've searched throughout gconf to no avail...

---

### Post by Alexander Kirillov on 2005-04-20
Funny - never paid attention to it. Indeed, on my machine (downloaded as pre-release, then updated) it is wastebasket. The only place I can possibly see this coming from is the file 
/usr/share/locale-langpack/en_GB/LC_MESSAGES/nautilus.mo

But why is this file used if my locale is en_US.UTF-8? Mystery...

BTW: what is your locale?

---

### Post by ignavia on 2005-04-20
I would bet money that it's a British thing. IIRC, on British OS's, it's called Wastebasket. As for how to change, I'm lost.

---

### Post by matthewn on 2005-04-22
This did in fact turn out to be a locale issue.

/etc/environment turned out to be the key file here. the first line had read:

LANGUAGE="en_US:en_GB:en"

I changed it to:

LANGUAGE="en_US:en_US:en"

...and now the Wastebasket is the Trash. Thanks for the pushes in the right direction.

---

