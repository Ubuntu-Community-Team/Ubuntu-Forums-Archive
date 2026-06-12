---
title: "No task bar ... crippled system"
date: 2008-05-13
forum: Desktop Environments
---

### Post by SalishSeaSailor on 2008-05-13
I am unable to get  task bar on boot into either normal GNOME or failsafe GNOME. I cant create launcher to launch a shell, and I can only run firefox, etc. from command line in failsafe terminal. I am completely hooped. I note existing forums on problems with nautilus and bonobo activitation server, but still not working for me.  
System is 32 desktop running on dual-headed AMD64 chip with NVIDIA. Help appreciated. System is essentially useless now.

---

### Post by VMC on 2008-05-13
> **SalishSeaSailor said:**
> I am unable to get  task bar on boot into either normal GNOME or failsafe GNOME. I cant create launcher to launch a shell, and I can only run firefox, etc. from command line in failsafe terminal. I am completely hooped. I note existing forums on problems with nautilus and bonobo activitation server, but still not working for me.  
System is 32 desktop running on dual-headed AMD64 chip with NVIDIA. Help appreciated. System is essentially useless now.

ALT-F2 
enter 'gnome-panel'

Is it the panel or xorg missing

---

### Post by SalishSeaSailor on 2008-05-16
Alt-F2 does not do anything. Switched to XFCE and this worked for about 2-3 days, then again no task bar. Back to running from failsafe terminal in XFCE.  Help!

---

### Post by rhenium3 on 2008-07-29
I had a similar problem, somehow the gnome-panel got deleted so I just reinstalled it

sudo apt-get install gnome-panel I think was the code... if you enter gnome-panel in the terminal it will tell you if you don't have it and how to install it... just fyi...

---

### Post by anotherdisciple on 2008-07-29
Weird... I wish my gnome-panel would go away... I don't use it... but if I uninstall it... bye-bye ubuntu-desktop, my ability to use alt+F2, etc...

I would venture to guess that reinstalling gnome-panel would fix it.

---

