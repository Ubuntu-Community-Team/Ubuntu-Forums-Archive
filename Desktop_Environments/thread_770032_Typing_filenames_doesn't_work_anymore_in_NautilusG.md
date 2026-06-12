---
title: "Typing filenames doesn't work anymore in Nautilus/Gnome"
date: 2008-04-27
forum: Desktop Environments
---

### Post by yang on 2008-04-27
Hi, in Nautilus and the Gnome file-opening dialog, I frequently use the ability to jump to a file by typing in its name.  However, after upgrading from 7.10 to 8.04, this no longer works.  Did this get disabled?  Can I enable it?  Thanks in advance for any help!

---

### Post by imon9 on 2008-04-27
+1

i am also facing the same problem. In fact, i had this problem everytime i upgrade ubuntu to a beta. It break before the release, and nevcer got finx when the release is out :(

please help

---

### Post by imon9 on 2008-05-12
i found the way to solved this problem!!!
after reading this thread, i found the solution!
[http://www.techtalkz.com/debian-linux/63008-q-nautilus-find-you-type-2.html](http://www.techtalkz.com/debian-linux/63008-q-nautilus-find-you-type-2.html)

it is due to scim

use the command:
im-switch -c
and choose "scim-immodule" instead of scim


it is due to scim

use the command:
im-switch -c
and choose "scim-immodule" instead of scim

---

