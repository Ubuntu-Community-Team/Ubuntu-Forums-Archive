---
title: "HELP!!!! i uninstalled nautilus from ubutnu"
date: 2011-04-11
forum: Desktop Environments
---

### Post by xenosaga456 on 2011-04-11
ok i uninstalled nautilus and all the software that comes with it from my ubuntu via synaptic and now my problem is when i try to login i noticed i cant select a session and after i login i get blackscreen and then it goes right back to login????

how do i fix this in recovery mode.....its my only option

---

### Post by Random_Dude on 2011-04-11
Have you tried?

```
sudo apt-get install nautilus
```

---

### Post by Copper Bezel on 2011-04-11
Also, you wouldn't really need to go into recovery mode - just hit Ctrl+Alt+F1 to switch to a console and run the command (and Ctrl+Alt+F7 to get back to the login screen.)

---

### Post by xenosaga456 on 2011-04-11
see i have tryed that but i need the internet and my only internet source is wifi...is there any way to connect using wifi from prompt screen

---

### Post by 3Miro on 2011-04-11
Network Manager Command Line Interface (nmcli)

[http://manpages.ubuntu.com/manpages/maverick/man1/nmcli.1.html](http://manpages.ubuntu.com/manpages/maverick/man1/nmcli.1.html)

It may not be installed by default. If it is not, then download it on another machine and move it with a flash drive.

---

### Post by swapnilchitnis360 on 2011-04-11
You can install thunar or any other file manager from the synaptic package manager. (I think this should help)

---

### Post by ajgreeny on 2011-04-11
Just in case nautilus took too many things with it when you uninstalled it, try using a cable connection to the web if possible then ```
sudo apt-get install --reinstall ubuntu-desktop
```

---

