---
title: "Various issues with compiz and no taskbar"
date: 2009-04-14
forum: Desktop Environments
---

### Post by kuxpac383 on 2009-04-14
I'm running Xubuntu 8.10 and after turning on my computer after coming back from a short vacation, I noticed that my top taskbar is no longer visible.  Usually I have to restart compiz with the compiz fusion icon which is located on the taskbar.  However, since there is no taskbar I can't restart compiz and now I lack boarders around my windows (meaning I don't have a close, minimize, expand window boarder).  This has never happened before.  How do I regain the taskbar at the top?  Also anyone know of a way to restart compiz without having access to the compiz fusion icon?  
Thanks,

---

### Post by kuxpac383 on 2009-04-14
nevermind, i solved this myself.

---

### Post by Jimmynemo2 on 2009-04-15
We'd love to hear how you did it, so future folks with the same issue can have something to try?

Thanks, and glad you got it fixed in just a few hours there. Sorry we couldn't be of more help.

---

### Post by jedistorm on 2009-04-15
Does anyone know how to reactive the panels in Xubuntu running Xfce. After a reboot they will not reopen and the panel control will not respond either.

Thanks to all in advance

---

### Post by Jakey_TheSnake on 2009-04-15
Try: ```
xfwm4 --replace
``` in a terminal. If that works, it will probably stop after you close the terminal. Add it to your startup options in System > Administration/Preferences > Sessions. 

That's where they are for a gnome-desktop anyway.

^ that is assuming you meant the part at the top of the window, with the close/open buttons.

---

