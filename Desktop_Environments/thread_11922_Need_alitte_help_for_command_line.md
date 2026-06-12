---
title: "Need alitte help for command line"
date: 2005-01-20
forum: Desktop Environments
---

### Post by apoc on 2005-01-20
Hello, I managed to install mplayer via a script from this forum, now I would like to install some skins for it, but I cannot copy paste trough the grafic file tree, so I would like to know what the command for this is in the terminal. 

The skins are located in /home/apoc/mplyr skins/

---

### Post by Ste on 2005-01-20
[QUOTE=apoc]Hello, I managed to install mplayer via a script from this forum, now I would like to install some skins for it, but I cannot copy paste trough the grafic file tree, so I would like to know what the command for this is in the terminal. 

The skins are located in /home/apoc/mplyr skins/[/QUOTE]
 The copy comman in the terminal is cp.
Check you ./mplayer directory in home skins can be stored in there if I remember correctly.

Or try 

```
sudo cp /home/apoc/mplyr\ skins/* /usr/local/share/mplayer/Skin/
```

That could be wrong, I'm not the best at terminal commands.

---

### Post by Rule on 2005-01-20
you can still use the GUI in the tool bar (whats it called? brain not workin) just put a . in  front of the folder you want that is hidden like

/home/rule/.mplayer/Skins

hope this kinda helps  :D

---

### Post by apoc on 2005-01-20
Thanks, it helped me along :)

---

