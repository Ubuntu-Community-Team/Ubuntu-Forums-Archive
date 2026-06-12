---
title: "Steam Upodate problem"
date: 2015-09-22
forum: Gaming &amp; Leisure
---

### Post by afrancis-ozonline on 2015-09-22
I tried to install Steam using the Terminal Command:
sudo apt-get install steam
Then after install I typed
steam
The update seemed to be OK until it completed and the following came up:
Steam Update UI:
An X Error occurred
X error of failed request: Bad Value (integer parameter out of range for operation)

Is there a fix for this problem?

---

### Post by sandyd on 2015-09-22
If your using Ubuntu 15.04, run
```

find $HOME/.steam/root/ubuntu12_32/steam-runtime/*/usr/lib/ -name "libstdc++.so.6" -exec mv "{}" "{}.bak" \; -print
```

(from [http://askubuntu.com/questions/614422/problem-with-installing-steam-on-ubuntu-15-04/614458#614458](http://askubuntu.com/questions/614422/problem-with-installing-steam-on-ubuntu-15-04/614458#614458))

---

### Post by afrancis-ozonline on 2015-09-23
THANKS> That worked, but I am a little confused do I have to run that command in terminal each time I want to play a Steam Game or only when I want to update Steam?

---

### Post by Bucky Ball on 2015-09-23
*Thread moved to **Gaming & Leisure**.*

---

