---
title: "chess"
date: 2009-06-02
forum: General Help
---

### Post by stud125 on 2009-06-02
Hi I just installed Ubuntu 9.04 on my system.

i tired to switch the chess to 3d mode and afterwards whenever i tried to run it , it would crash when i first clicked on it.

I tried to uninstall then reinstall it but now when i install the gnome game pack it installs all the games except the chess.

Anyone know how to reinstall it on the menu, perhpas through the terminal?

Thanks.

---

### Post by steeleyuk on 2009-06-02
Its a known bug in the chess game. [This Launchpad thread]("https://bugs.launchpad.net/gnome-games/+bug/350850") has a solution which involves turning 3D off outside of the game (using gconf-editor). It means that you won't be able to use the 3D mode until its fixed however.

---

### Post by stud125 on 2009-06-05
This one?

$ gconftool-2 --toggle /apps/glchess/show_3d

---

### Post by stud125 on 2009-06-05
Also for some reason I dont have chess in my gnome menu anymore. Even when i reinstall it its not there.

---

### Post by Soul-Sing on 2009-06-05
reinstall gnome-games?
```
sudo apt-get install gnome-games
```

the default chessgame = gnuchess

---

