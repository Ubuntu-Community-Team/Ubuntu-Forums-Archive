---
title: "Gnome freezes after login window but KDE boots"
date: 2007-07-19
forum: Desktop Environments
---

### Post by LinAxed on 2007-07-19
Hello all,

Suddenly GMONE freezes after showing the login window. After entering password, I see quite a lot of hard disk activity followed by a beep sound. After that except for the mouse pointer, the screen remains blank. I have tried everything I can think of and find on support forums - reinstalling GDM, XORG, disabling dri, etc. 

But then I tried to change the session to KDE.  X starts normally, and all applications function normally. 

So, the bottom line is that KDE works but GNOME does not.

I tried to remove and reinstall GDM, but no success. Any pointer to enforce clean GNOME install and complete removal of old config files? 

Best regards and thank you.

:confused:

---

### Post by Frem on 2007-07-19
If you wait for like 5 minutes, does Gnome load? If so, this sounds a lot like the problem I'm having in [this thread]("http://ubuntuforums.org/showthread.php?t=495988").

---

### Post by pbcartwright on 2007-07-19
in your home folder you have a .kde and a .gnome directory. try renaming .gnome to something else, restart and try logging in with gnome dsktop.

---

