---
title: "K-Menu help"
date: 2006-06-24
forum: Desktop Environments
---

### Post by linux_student_user on 2006-06-24
Is there a way I can change the menu button for KDE - its seriously ugly, i have a transparent bar and an ugly block for a button - can i replace it somehow? Thanks in advance.

Mike

---

### Post by MartinG on 2006-06-24
The icon lives in /usr/share/icons/default.kde/nnxnn/apps, and is called kmenu.png.  nnxnn depends on the size of your kicker panel.

What you need to do is replace the appropriately sized kmenu.png with your choice of icon (giving it the name kmenu.png).  Two gotchas: You might have to replace more than one, at different sizes, to find which one your computer is actually using. And, when you update KDE (I'm not sure which package, sorry) your icons will be overwritten -- so be sure to save copies in a safe place!

---

