---
title: "Shortcut help."
date: 2006-01-09
forum: General Help
---

### Post by Rahu on 2006-01-09
I'm trying to make a shortcut to launch my HL server. The location of the files is ~/Programs/HLDS/hlds_run, and it has to be launched from ~/Programs/HLDS to find the game files. Is there any way I could make a shortcut to launch it from this directory so it runs properly?

---

### Post by matthinckley on 2006-01-09
create a script like this

```
#!/bin/bash
cd ~/Programs/HLDS/
~/Programs/HLDS/hlds_run
```


then you can run it from any directory

edit: make sure you chmod +x it so you can run it

---

### Post by Rahu on 2006-01-09
Thanks, that works :)

---

