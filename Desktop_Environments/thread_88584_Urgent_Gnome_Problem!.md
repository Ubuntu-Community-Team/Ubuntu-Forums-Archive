---
title: "Urgent Gnome Problem!"
date: 2005-11-10
forum: Desktop Environments
---

### Post by Zhukov on 2005-11-10
Hi!
Ive just started my laptop (ubuntu only) and i receive a message saying that gnome-panel ended unexpectadly! I hit restart app and the error is back again!
Ive changed to a terminal and did sudo kill gdm and restarted it. Ctrl+alt+backspace gave me no solution, neither rebooting! Im desperate! This is my working box, no way i can re-install ubuntu now!
Help me out! Urgent! :S

---

### Post by ssam on 2005-11-10
will gnome failsafe work. choose it from the sessions menu at the login screen

---

### Post by Zhukov on 2005-11-10
No, gnome failsafe failed as well... Im going crazy... #-o

---

### Post by ssam on 2005-11-10
ok, switch to a terminal and run

```
sudo apt-get install xubuntu-desktop
```

when that has finish try go back to the login screen and choose xfce from the session menu. (you may need to restart gdm for it to be in the sessions menu).

that should give you a graphical interface to keep you going until this is fixed.

---

### Post by teaker1s on 2005-11-10
you could start kernel without window manager and use apt-get to reinstall ubuntu -desktop or kubuntu-desktop this will reinstall windows without erasing your data thats how I cured my corrupted gnome

---

### Post by aysiu on 2005-11-10
These links may or may not help, but they're worth checking out:
[http://72.14.207.104/search?q=cache:koLl5ld4V5AJ:ubuntuforums.org/archive/index.php/t-37659.html+gnome-panel+ended+unexpectedly&hl=en](http://72.14.207.104/search?q=cache:koLl5ld4V5AJ:ubuntuforums.org/archive/index.php/t-37659.html+gnome-panel+ended+unexpectedly&hl=en)
[http://72.14.207.104/search?q=cache:rnYAhWdW8JIJ:https://www.redhat.com/archives/fedora-list/2005-October/msg01688.html+gnome-panel+ended+unexpectedly&hl=en](http://72.14.207.104/search?q=cache:rnYAhWdW8JIJ:https://www.redhat.com/archives/fedora-list/2005-October/msg01688.html+gnome-panel+ended+unexpectedly&hl=en)

---

### Post by Zhukov on 2005-11-10
No good. Reinstalled ubuntu-desktop and the error persists.
:S Any suggestions?

---

### Post by ssam on 2005-11-10
reinstalling ubuntu-desktop wont do much as it is just a metapackage. it does not contain any files, it just makes sure lots of other packages are installed. when you uninstall it then nothing is actually removed.

---

### Post by Zhukov on 2005-11-11
Ive reinstalled the entire system, but it was a conf problem... So i had to erase my home folder too :S
Now its working. Thanks everyone.

---

