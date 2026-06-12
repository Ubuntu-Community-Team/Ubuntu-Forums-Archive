---
title: "run level"
date: 2005-05-11
forum: Desktop Environments
---

### Post by baza41 on 2005-05-11
Hi,

how do I change the default run level so my Hoary server boots to console rather than Gnome?

Thanx

Baza

---

### Post by RastaMahata on 2005-05-11
"Please do not post questions here. This is for HOWTO's and FAQs only."
It says so in the top of the forum.
Please, read and search before posting, and if you do post, do it in the right forum.

---

### Post by thecrimsonking on 2005-05-12
sudo gedit /etc/inittab

find where it says:
# The default runlevel.
id:2:initdefault:

If memory serves me right 3 is multiuser console.  So change the 2 to a 3.

---

