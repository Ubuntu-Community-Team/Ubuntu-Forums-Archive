---
title: "Can you change the computer's name after install?"
date: 2010-03-01
forum: Desktop Environments
---

### Post by hislordship on 2010-03-01
Hello mates, on installing Ubuntu Karmic I have made a silly spelling error when giving a name to the computer. It appears every time when I boot the system on the login screen. It drives me nuts... Is there a way to change the computer's name once the installation is complete without having to reinstall everything?
Thanks, Sascha

P.S I use the Gnome desktop environment

---

### Post by Arkitekt on 2010-03-01
To make a permanent change edit your hostname file with

```
gksudo gedit /etc/hostname 
```

Do the same to /etc/hosts or you will have sudo issues

Make sure to reboot after for the changes to take effect

Hope this helps

---

### Post by hislordship on 2010-03-01
Thanks Architekt, that`s worked like a charm!

---

