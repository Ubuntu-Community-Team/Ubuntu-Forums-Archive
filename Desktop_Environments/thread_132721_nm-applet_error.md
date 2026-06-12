---
title: "nm-applet error"
date: 2006-02-18
forum: Desktop Environments
---

### Post by neoflight on 2006-02-18
i installed network manager and when i am running nm-applet nothing happens. i put it at startup and nothing comes in the gnome panel too. 

i cannot start nm-applet using application launcher...

but nm-applet is there.. i can get it using tab when typing. 
no error until i did this...

```
sudo chmod u+s /usr/bin/nm-applet
```

after that when i run nm-applet i get this...

[HTML]name@ubuntu:~$ nm-applet

(nm-applet:8707): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:
    http://www.gtk.org/setuid.html
Refusing to initialize GTK+.[/HTML]

any clue ???:-k

---

### Post by neoflight on 2006-02-18
ok solved it. its working as of now. (reinstalled [all three packages from here]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Multiple_Wireless_Profiles"))anyway have to try different locations to see if it actually works when needed,

thanks...

---

