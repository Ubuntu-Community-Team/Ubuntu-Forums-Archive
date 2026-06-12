---
title: "recovering ubuntu after deleting some files"
date: 2009-04-10
forum: General Help
---

### Post by dyyyy on 2009-04-10
hi,
i accidently deleted some files from synaptic manager,
and when i restarted my PC, i couldn't log in normally, instead it showed me a command line desktop$
how can i recover my ubuntu?
more info :
- i'm not sure if what i deleted is the problem or because i installed xfce and kde on ubuntu.
- i tried to enter recovery mode but it's the same
thank you for your help

---

### Post by taurus on 2009-04-10
What happens if you type **startx** from the prompt?

---

### Post by dyyyy on 2009-04-10
i get a gray window, with an X instead of the mouse that i can move
and i can do nothing but type on the shell open on the left of the screen

---

### Post by utnubuuser on 2009-04-10
Hi - You could try > sudo dpkg-reconfigure xserver-xorgat the command line, and if that doesn't work,> sudo apt-get install --reinstall xserver-xorg-core

---

### Post by taurus on 2009-04-10
Sounds like you probably need to reinstall Gnome again.  Get back to the prompt and run

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by dyyyy on 2009-04-13
thanks it worked
althought it runs only ino low graphics mode can i also fix this?
just for info did this happen because i installed other desktop environments?

---

### Post by 3rdalbum on 2009-04-13
No, it likely happened because of whatever you deleted.

---

