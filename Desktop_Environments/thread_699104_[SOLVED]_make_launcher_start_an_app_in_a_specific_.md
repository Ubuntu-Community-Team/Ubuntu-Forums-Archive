---
title: "[SOLVED] make launcher start an app in a specific folder"
date: 2008-02-17
forum: Desktop Environments
---

### Post by eilu on 2008-02-17
Is there a way to open an app so it starts from a specific folder or location? I know you can set it to "open in terminal" but how about other places? I need to launch an app from /usr/games/powder100/

---

### Post by eilu on 2008-02-17
nevermind... I wrote a shell script to do it instead.

---

### Post by Hero of Time on 2008-04-21
What did you set in the script? It would be useful to note the things you did. I want to run something similar. I just can't seem to get it to run properly.

Edit:
Found it out. Made a typo on the first try :X. For those who are also trying this, put the following in a script:
```
#/bin/sh
cd /path/to/executable
executable
```

---

