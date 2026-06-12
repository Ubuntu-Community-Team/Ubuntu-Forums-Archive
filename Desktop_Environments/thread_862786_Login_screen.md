---
title: "Login screen"
date: 2008-07-17
forum: Desktop Environments
---

### Post by mb125 on 2008-07-17
Ive just upgraded to 8.04, after booting and when ubuntu gets to the login and P/W screen it apears that it is zoomed in and the Login window if off in space. after putting in U/N and P/W my desktop comes up normal. How do i correct this?

---

### Post by mb125 on 2008-10-04
Is there a way to set the screen resolution for GDM ? the U/N P/W is lost in space off the screen. After login all is well

---

### Post by robc02 on 2008-10-06
I found this on the forums and it worked for me:

Edit the xorg.conf file by doing : sudo gedit /etc/X11/xorg.conf

Find the "Screen" section; at the end of it there is "Virtual" and next to that is a resolution. Change it to the resolution you want.

---

### Post by mb125 on 2008-10-10
Thats what i did and it worked...Thanks to all

---

