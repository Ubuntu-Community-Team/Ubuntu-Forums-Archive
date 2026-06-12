---
title: "Can't make desktop entry execute a command in terminal"
date: 2011-07-09
forum: Desktop Environments
---

### Post by Mortesins93 on 2011-07-09
Hello,
I created this custom desktop entry in Lubuntu 11.04 which doesn't work:
```

[Desktop Entry]
Name=DocumentiAxel
Exec=sudo pcmanfm /mnt/data/.DocumentiAxel
Terminal=true
Type=Application
Icon=/usr/share/icons/elementary/places/48/folder.svg

```
If I change it like this:
```
[Desktop Entry]
Name=DocumentiAxel
Exec=gksudo pcmanfm /mnt/data/.DocumentiAxel
Terminal=false
Type=Application
Icon=/usr/share/icons/elementary/places/48/folder.svg

```

It works, but I want it to run in terminal. I tried creating other entries but they never work if I put "Terminal=true" even if the execution command works in the terminal if I paste it manually.
Why is this?
Hope you can help me.

---

### Post by koleoptero on 2011-07-09
Try changing the exec to something like:

Exec=gnome-terminal -e "gksudo pcmanfm /mnt/data/.DocumentiAxel"

If you use some other terminal then change the gnome-terminal with whatever that is (xfce4-terminal, terminator, etc).

---

### Post by Mortesins93 on 2011-07-10
Thank you so much, it works even though I don't get why it can't be automatically run in the terminal like in Ubuntu and Xubuntu. Anyways, I had searched around and I knew the command lxterminal -e would open a terminal and then run a command but I forgot about the "". Thank you so much again.

---

### Post by koleoptero on 2011-07-10
> **Mortesins93 said:**
> Thank you so much, it works even though I don't get why it can't be automatically run in the terminal like in Ubuntu and Xubuntu. Anyways, I had searched around and I knew the command lxterminal -e would open a terminal and then run a command but I forgot about the "". Thank you so much again.

Glad I could help :) The "" are needed if the command contains spaces, if you just wanted to run for example top, you wouldn't need them :)

---

### Post by Mortesins93 on 2011-07-10
Ok, thanks that make more sense

---

