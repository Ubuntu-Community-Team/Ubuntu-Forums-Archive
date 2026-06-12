---
title: "Terminal launches with /usr/bin"
date: 2006-03-08
forum: Desktop Environments
---

### Post by Krigl on 2006-03-08
I've edited launch command of my Gnome-terminal launcher (on Xfce4 panel) and it began to launch with ```
krigl@Megatherion:/usr/bin$
```

I've tried to make it start with either "gnome-terminal" or "/usr/bin/gnome-terminal" but it's stuck to /usr/bin. How could I turn it back to start in my home directory?

---

### Post by evilgold on 2006-03-08
Change the command to
```

gnome-terminal  --working-directory=~
```

---

### Post by Krigl on 2006-03-08
Thanks a lot, it worked. Anyway, any suggestions why it behaved that way? The edit I commited was just adding "--borderless" option behind the launch command to see if it will work (didn't). I don't remember if I had just "gnome-terminal" or full path command before but I use both for launchers without any difference.

---

