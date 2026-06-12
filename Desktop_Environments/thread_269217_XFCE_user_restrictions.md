---
title: "XFCE user restrictions"
date: 2006-10-01
forum: Desktop Environments
---

### Post by wea on 2006-10-01
Hi!
How can I prevent users from starting any software which is not tagged as "allowed" by me? For example only OO, Firefox and the Printer should be startable by this user.
I think about using Ubuntu for a public PC at a library. As this it not a high-end mashine I switched a standard 6.06 installation to XFCE desktop with "sudo apt-get install xubuntu-desktop". And I don't want to use XFCE's kiosk mode as it is known to be buggy.
But how can the users rights be restriced to prenvent him entering shell and filemanager or altering menues and desktop.
Is it possible to do a auto login for this user?

Regards,
  Andreas Weller

---

### Post by lagagnon on 2006-10-01
I would first remove all the menu items you do not want the user to see. Then restrict terminal use by making things like xterm, aterm, xfterm etc executable by root only. You should also remove virtual consoles by commenting out the appropriate lines in /etc/inittab. Autologin with xfce I don't know about - I would reask the question at the xfce forums/mailing lists.

---

