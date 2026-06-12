---
title: "[SOLVED] A Couple of odd settings"
date: 2008-07-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Gizmo688 on 2008-07-25
Ive got a few assorted questions.

1)I use rdesktop to access a windows desktop on a regular basis. One day, the sound just stopped working. I am using the sound:local thing, and have tried reinstalling rdesktop. Is this a error on the windows machine?

2)How can i set my startup to automatically initalize a specific kernel?

3)Ever since upgrading from 7.10 to 8.04, the ubuntu splash screen(the screen before it asks me to login) looks fubar. Any suggestions to make it look like normal?

---

### Post by Gizmo688 on 2008-07-27
bump?

---

### Post by gbrainin on 2008-07-27
Regarding #2: If you edit your /boot/grub/menu.lst file (you will need to sudo this), there is a line there that says something like:
default   0
Change that number, and it changes the default kernel that gets booted.  It goes in the order that the kernels (or other boot options) are listed, starting with 0.

---

### Post by Gizmo688 on 2008-08-18
any ideas on the rdesktop issue?

---

