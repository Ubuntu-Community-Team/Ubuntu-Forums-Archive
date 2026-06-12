---
title: "can't start gnome"
date: 2005-12-31
forum: General Help
---

### Post by bigblop on 2005-12-31
I have just changed them in gnome-theme-manager and now gnome does not anymore.

When I log in, the welcome sound starts but then the panel in the top and buttom just blinks and a wierd sound (like a drum) goes on and off at various intervals.

I can still use fvwm (another window manager) but when I open an xterm and type firefox I get:

mos@ubuntu:~$ firefox
Segmentation fault
mos@ubuntu:~$ 

I have also tried:

mos@ubuntu:~$ rhythmbox
Segmentation fault
mos@ubuntu:~$ 


konqueror works though and is the one that I use to type this message. Hope someone can help

---

### Post by AdotB on 2006-04-11
I had this sam exact problem earlier today. But i found out (after a long time searching) that it was the gtk-qt that i had installed a couple of days ago ( i had been using kde for the passed couple days). I uninstalled it and gnome loaded fine. I don't know if that helps you at all, I don't know excactly what the problem is.

Let me know if you figure it out.

---

