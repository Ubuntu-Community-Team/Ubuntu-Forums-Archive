---
title: "How to disable new applications to steal focus?"
date: 2009-05-03
forum: General Help
---

### Post by abcuser on 2009-05-03
Hi,
I use terminal very often, then I start some other program like gedit, firefox etc. This new started programs steal focus from terminal. It is difficult to type anything in terminal if other application is trying to steal focus. Is there any way I could set that no program on Ubuntu should steal focus?
Regards

---

### Post by Brucevdk on 2009-05-03
If you're using Metacity you just have to set */apps/metacity/general/focus_new_windows* to *strict* which results in windows started from the terminal not being given focus. Potentially you could also write up a custom script that uses libwnck to hide the window, then you'd start applications using something like *nofocus gedit*.

---

### Post by abcuser on 2009-05-04
Hi,
can you please provide more info. Where do I set this settings in which program, file, etc?

As I understand this will prevent applications to not steal focus when started from terminal. But what about all other applications that are not started from terminal?
Regards

---

### Post by Brucevdk on 2009-05-04
*/apps/metacity/general/focus_new_windows* is a gconf key so use gconf-editor to modify it. I'm not sure how this will affect focus stealing overall so you'll have to check for yourself.

---

### Post by abcuser on 2009-05-04
Hi,
thanks for help. I have tried this settings and started "firefox &" command and Firefox still steals focus. Is this Firefox specific?
Regards

---

