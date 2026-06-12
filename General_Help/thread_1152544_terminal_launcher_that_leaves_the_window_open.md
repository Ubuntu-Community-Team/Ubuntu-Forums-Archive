---
title: "terminal launcher that leaves the window open?"
date: 2009-05-07
forum: General Help
---

### Post by PCZahra on 2009-05-07
Hi,
I run this command:
sudo escputil -i -r /dev/usblp0
to get the level of ink in my printer because the printer properties window can't see it. I tried putting the command into a launcher so I don't have to type it, but the terminal window closes before I can see the result. Is there a way to run a terminal app and keep the window open after it ends? I found a global setting, but I was hoping for just a one-off thing.

---

### Post by kanikilu on 2009-05-08
If you are using gnome-terminal and the bash shell, you can try something like this:

```
gnome-terminal -e "sh -c 'sudo escputil -i -r /dev/usblp0 && bash'"
```

---

### Post by PCZahra on 2009-05-12
Thanks, that worked. I need more ink.

---

