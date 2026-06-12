---
title: "gnome in wrong console after xserver restart"
date: 2008-01-30
forum: Desktop Environments
---

### Post by glennric on 2008-01-30
I have had this issue for a long time (since at least Dapper).  Whenever I restart the xserver, either by zapping with ctrl-alt-backspace or by sudo /etc/init.d/gdm restart gdm changes consoles and ends up in tty8 or tty9.  Once I think it even ended up in tty10.  So I have to use ctrl-alt-F[8-10] to get back to gnome after switching to another console.  Any ideas why this is happening and how to fix it so that gnome always ends up in tty7 as desired?

---

