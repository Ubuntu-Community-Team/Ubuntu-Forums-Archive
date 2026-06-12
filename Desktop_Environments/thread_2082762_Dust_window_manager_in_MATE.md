---
title: "Dust window manager in MATE"
date: 2012-11-10
forum: Desktop Environments
---

### Post by Riffronan on 2012-11-10
I love the dust window manager theme and I installed the dust folder into the hidden '.themes' folder but when I change themes (right click desktop, change desktop background, theme), the selected theme lets you change fonts, icon sets, colors BUT the window manager stays on Ambiance no matter what theme you choose.  Maybe I could reinstall the Dust theme, but I don't get why the included themes won't change the window decoration (open, close, minimize buttons).  I'm running compiz, not marco and would surely appreciate your help on this!

---

### Post by Riffronan on 2012-11-10
I dug around for a few hours and found this workaround.    "I solved it by using gconf editor. Go to /apps/metacity/general and change the Theme value to whatever theme you want."  Here's the link : [http://askubuntu.com/questions/179661/cannot-change-window-border-theme-in-mate](http://askubuntu.com/questions/179661/cannot-change-window-border-theme-in-mate)  I hope this helps someone else too!  *SOLVED* until the MATE team resolves this

---

