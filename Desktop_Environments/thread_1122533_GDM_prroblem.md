---
title: "GDM prroblem"
date: 2009-04-11
forum: Desktop Environments
---

### Post by adimania on 2009-04-11
hi...my problem is that my gnome display manager does not load at startup. When I write 
sudo gdm
then I get the following error message:
symbol lookup error /usr/lib/libgio-2.0.so.0:undefined symbol: g_thread_gettime

please help...

---

### Post by Ratscallion on 2009-04-11
Try going into the console mode (control + alt + F1 - F6) then running nautilus to see if you can get the X server running on there. If you can, just run nautilus again, and see what happens. You should get into a graphical display from there.

---

### Post by adimania on 2009-04-11
My computer is starting in terminal mode only. And when I type:
nautilus or sudo nautilus
I get the same error message as above.i.e.
symbol lookup error: /usr/lib/libgio-2.0.so.0:undefined symbol: g_thread_gettime

---

### Post by Ratscallion on 2009-04-11
Are you connected to the Internet, if you are, try using sudo apt-get install and sudo apt-get autoremove to uninstall then reinstall gnome/kde.

---

### Post by adimania on 2009-04-11
I was connected to net through college proxy which means I have to login after opening my browser window. Now I cannot do that. Can I download a .deb package from somewhere and install it in my laptop?
If yes then please can you give me the link?

---

### Post by Ratscallion on 2009-04-12
Urm, sure I'll try, but how are you using the Internet to use the forums, if you can somewhat transfer the *.deb file on this link: 
[http://ubuntu.blueyonder.co.uk/archive/pool/universe/m/meta-gnome2/gnome-desktop-environment_2.22.2~4ubuntu2_all.deb](http://ubuntu.blueyonder.co.uk/archive/pool/universe/m/meta-gnome2/gnome-desktop-environment_2.22.2~4ubuntu2_all.deb)
to the Ubuntu PC and try installing it from there, it should help. After downloading, use the terminal to cd to the directory you stored it in, and use ```
dpkg -i (package name) 
``` to install. I'm not sure what the official package name is, I think it's either ```
 gnome-desktop 
``` or ```
 gnome-desktop-environment
```

---

