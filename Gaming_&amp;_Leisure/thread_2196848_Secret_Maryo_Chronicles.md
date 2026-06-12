---
title: "Secret Maryo Chronicles"
date: 2013-12-31
forum: Gaming &amp; Leisure
---

### Post by josh17 on 2013-12-31
I got a game called Secret Maryo Chronicles from the ubuntu software center, but it doesn't work :( When i run it, it goes to full screen, then crashes. I can't figure out why so if anyone has had this problem and has found a fix please let me know :)

---

### Post by josh17 on 2013-12-31
nvm i found a fix here: [https://apps.ubuntu.com/cat/applications/precise/smc/](https://apps.ubuntu.com/cat/applications/precise/smc/) just incase anyone else had this trouble

---

### Post by dannyboy79 on 2014-01-01
If you're using 12.04 you will need to make /usr/share/games/smc/campaign directory, otherwise game won't start. I just made it using sudo so it has the following permissions drwxr-xr-x
if you need the command it's 
```
sudo mkdir /usr/share/games/smc/campaign
```
ENJOY

---

