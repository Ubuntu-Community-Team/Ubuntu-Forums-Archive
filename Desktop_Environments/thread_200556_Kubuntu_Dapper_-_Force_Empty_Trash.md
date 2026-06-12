---
title: "Kubuntu Dapper - Force Empty Trash"
date: 2006-06-20
forum: Desktop Environments
---

### Post by neko18 on 2006-06-20
Sometimes my trash is a little buggy and won't empty, so I made a small script to empty it as root. Will someone verify this is correct, please? It appears to work fine, but I'd like to make sure I'm not missing anything.
```
#!/bin/bash
sudo rm -r $HOME/.local/share/Trash/files/*
sudo rm -r $HOME/.local/share/Trash/files/.*
sudo rm -r $HOME/.local/share/Trash/info/*
sudo rm -r $HOME/.local/share/Trash/info/.*
```

---

### Post by carla on 2006-11-09
I can't get it to work under Edgy, but the problem could totally be between the chair and the keyboard. :D

Did you find success with the final script?

---

### Post by the ev on 2006-11-16
Looks like the directories have changed, so rather

```
#!/bin/bash
sudo rm -r $HOME/.Trash/*
sudo rm -r $HOME/.Trash/.*

```

Worked for me on Edgy 6.10.  Figured this out by [this]("http://www.ubuntuforums.org/showthread.php?t=217258&highlight=force+empty+trash") post.

Hope that helps!

---

### Post by aysiu on 2006-11-16
Sounds to me as if this would be a better solution: ```
sudo chown -R neko:neko /home/neko
```

---

