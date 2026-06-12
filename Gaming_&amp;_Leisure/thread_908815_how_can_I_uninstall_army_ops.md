---
title: "how can I uninstall army ops?"
date: 2008-09-02
forum: Gaming &amp; Leisure
---

### Post by Kain000 on 2008-09-02
Hey everyone, 
I've been looking arround for some fun games for linux and found america's army.    I've downloaded the file armyops250linux.run and ran it in the terminal, installed, or so I thought.  I used 
sudo ./armyops250linux.run 
After the install I found it under applications>other>armyops with it's own icon, So I had thought it worked but when i click to launch it nothing happens.  
when run in the terminal
armyops
I get:

./armyops-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
 I want to try to uninstall and reinstall but not sure how to remove it.

any ideas how to get this to work?

---

### Post by tuxxy on 2008-09-02
Open a terminal and type

```
sudo apt-get install libstdc++5 libstdc++5-3.3-dev
```

Now run try and run the game again

---

### Post by boterbram on 2009-02-16
But it's working on my system but I don't like it, so how to remove anyway?

---

### Post by Dizzle7677 on 2009-02-17
sudo ./armyops250linux.run --uninstall or sudo ./armyops250linux.run -uninstall ? Otherwise, check on their site for info.

---

