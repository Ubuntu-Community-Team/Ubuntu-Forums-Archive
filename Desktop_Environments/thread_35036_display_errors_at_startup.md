---
title: "display errors at startup?"
date: 2005-05-17
forum: Desktop Environments
---

### Post by brandan on 2005-05-17
i just installed ubuntu, and everything seemed to go well.  when the system is booted it starts gnome automatically, but the display is way messed up.  all i can see normally is the mouse cursor, but everything else is garbled and i can't seem to find any key combinations to exit gnome.

i'm wondering if there is a way for me to start ubuntu without starting gnome automatically, and if anybody here knows what the problem might be.  my video card is an ati radeon 9200.  thanks.

---

### Post by blueplazma on 2005-05-17
To drop to a terminal if X is not working you need to hit CTRL+ALT+F1 and then you can login normally.  If possible, try posting your xorg.conf file as well as any error messages you can get from running ```
sudo /etc/init.d/gdm restart
```

---

### Post by brandan on 2005-05-17
thanks, i'll try that.

---

### Post by brandan on 2005-05-17
i tried what you suggested, however it seems that when x starts up my keyboard stops functioning.  i can still move the mouse cursor around, but as there is nothing but noise i can't really do much with it.

i was able to boot to console by using the 'recovery mode' in the grub boot menu, but i can't find a console web browser to use while i'm there, so posting my config is pretty much out of the question (unless i write everything down, then type it after i switch hard drives and boot to windows :\).

are there specific configuration files i should be looking for in certain directories?

---

### Post by Sam on 2005-05-17
[QUOTE=brandan]i tried what you suggested, however it seems that when x starts up my keyboard stops functioning.  i can still move the mouse cursor around, but as there is nothing but noise i can't really do much with it.

i was able to boot to console by using the 'recovery mode' in the grub boot menu, but i can't find a console web browser to use while i'm there, so posting my config is pretty much out of the question (unless i write everything down, then type it after i switch hard drives and boot to windows :\).

are there specific configuration files i should be looking for in certain directories?[/QUOTE]
You can use lynx, it's a console based web browser :wink: (apt-get install lynx)

---

### Post by brandan on 2005-05-17
oh, this is my first time using ubuntu, so i'm not too familiar with the package system.  i've got elinks now, but for some reason i can't let me use another terminal (tried alt+f1 and ctrl+alt+f1).

---

