---
title: "Right-click doesn't work in Thunar unless holding button"
date: 2009-01-02
forum: Desktop Environments
---

### Post by coldwind777 on 2009-01-02
For some reason, when I right-click an icon (file or directory) in Thunar, the context menu only appears for as long as I'm holding the button. I have to right-click and hold instead of just right-clicking. It doesn't do this if I click on empty space, any of the icons in the side pane or in any other programs. It started doing this recently, and I've tried uninstalling and reinstalling. Anybody have this problem or have any ideas on how I should go about fixing it?

---

### Post by siafok on 2009-03-24
I have the problem too. Have you found any solution?

---

### Post by siafok on 2009-03-24
OK. I've found it. There is a bug in Thunar when you got in themes/.../gtkrc or in ~/gtk-2.0 entry: "gtk-menu-popup-delay =". I've only tried values from 0-2 with no success and finally I've comment it out so I dont know if with higher values right click menu in Thunar works.

---

### Post by jorgebadad on 2012-02-24
Thanks, very, very thanks **siafok** !

I am running fluxbox with thunar and I had the same problem; I was unistalling fluxbox, but I found your tip;  I commented the "gtk-menu-popup-delay =" in gtkrc file (in ~/.themes/theme_directory) and now I fixed the bug.

Thank you very much!

---

