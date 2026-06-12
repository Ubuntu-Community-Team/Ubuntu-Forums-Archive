---
title: "How to uninstall ut2004"
date: 2009-05-25
forum: General Help
---

### Post by mgtech on 2009-05-25
How to uninstall ut2004.

The uninstall.sh is located in usr/local/games/ut2004. Synaptic and add/remove programs don't see ut2004. When I use the terminal and type 
sudo sh usr/local/games/ut2004/uninstall.sh       I get
sh: Can't open usr/local/games/ut2004/uninstall.sh
I am the same user who installed the game.

---

### Post by michy99 on 2009-05-25
Be sure to put / at the beginning of the path.```
sudo sh /usr/local/games/ut2004/uninstall.sh
```

---

### Post by mgtech on 2009-05-25
still:


sh: Can't open /usr/local/games/ut2004/uninstall.sh

---

### Post by mgtech on 2009-05-25
How could I eliminate ut2004?
 Is there a way to restore the computer x hours or days ago?

---

### Post by themusicalduck on 2009-05-25
Not sure, but perhaps you need to make it executable? Find the file, right click - properties. On permissions tab check the Execute box.

---

