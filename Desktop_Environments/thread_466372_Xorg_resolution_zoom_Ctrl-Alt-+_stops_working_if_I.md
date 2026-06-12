---
title: "Xorg resolution zoom Ctrl-Alt-+ stops working if I set UK keyboard in Xorg.conf"
date: 2007-06-06
forum: Desktop Environments
---

### Post by woodbeez13 on 2007-06-06
Hi, when I add the line;

Option "XkbLayout"  "uk"

to my Xorg.conf file in order to get my keyboard layout right, it stops the Xorg resolution zoom facility working.

This is where you can zoom in and out by pressing Ctrl Alt + or Ctrl Alt -

The Ctrl Alt and + keys do still work individually but no longer activate the zoom facility unless I remove the above line from my xorg.conf.

Any ideas?

I'm running Openbox3 on Feisty Fawn.

Thanks in advance.

Mark B.

---

### Post by woodbeez13 on 2007-06-06
Sorry, I've found the answer another way.

I hadn't got a .xsession file in my \home dir.

I've created one now and it's allowing me to use the Gnome-Panel to configure things in a GUI way which seems to have solved my keyboard layout problem.

Thanks

Mark B.

---

