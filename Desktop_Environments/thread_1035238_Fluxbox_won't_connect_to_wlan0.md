---
title: "Fluxbox won't connect to wlan0"
date: 2009-01-09
forum: Desktop Environments
---

### Post by kr651129 on 2009-01-09
Alright so I upgraded my system to ubuntu 8.10 and decided to give fluxbox a try.  And I llove it, I'll soon be removing the gnome desktop after I get 100% use to this.  But there is one problem.  For fluxbox to connect to my wireless network I must first log into gnome, let it connect, sign out, then sign into fluxbox.  Any ideas?  Thanks!

---

### Post by kr651129 on 2009-01-09
*bump*

---

### Post by kerry_s on 2009-01-09
put " nm-applet --sm-disable & " in your fluxbox startup so it can use the networkmanager.

---

### Post by kr651129 on 2009-01-09
Thank you!

---

