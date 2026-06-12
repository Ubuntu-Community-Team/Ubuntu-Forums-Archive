---
title: "cannot load graphic user interface(GNOME) !!"
date: 2005-10-24
forum: Desktop Environments
---

### Post by yhcheong on 2005-10-24
hi. i'm newbie in linux.i installed several months ago. recently when i start the ubuntu operating systems, it appeared cant find GUI. even after login, i type startx also cannot...what's the problem... HELP !!!!

---

### Post by jonesy on 2005-10-24
You're going to have to post an error message for us to even get started.  Possible places to start looking include /var/log/Xorg.0.log.  Does GDM even start (That's the graphical screen that lets you log in)?

---

### Post by yhcheong on 2005-10-24
what i'm loading at the moment is a black screen..without GUI. after login, i try to start the GNOME by typing  startx.. it appeared cant load x-server. anyone can help?

---

### Post by yhcheong on 2005-10-24
sorry.. should be x-windows

---

### Post by salsafyren on 2005-10-24
[QUOTE=yhcheong]sorry.. should be x-windows[/QUOTE]

Maybe you installed the server version?

If you did, try to type the following:

"sudo apt-get install ubuntu-desktop"

It will install all the desktop software. Wait, reboot and enjoy!

---

### Post by yhcheong on 2005-10-25
thank you. I will try. currently using windows, dual boot. :)

---

