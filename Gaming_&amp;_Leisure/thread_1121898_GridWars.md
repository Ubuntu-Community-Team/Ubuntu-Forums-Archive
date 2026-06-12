---
title: "GridWars"
date: 2009-04-10
forum: Gaming &amp; Leisure
---

### Post by HuXu on 2009-04-10
So i'm trying to run GridWars [http://gridwars.marune.de/](http://gridwars.marune.de/)

But i get this error

"
./gridwars: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

"

I compile C++ code on my system all the time and I checked and I have libstdc++6 installed.  Whats the issue?

---

### Post by Grishka on 2009-04-10
> **HuXu said:**
> So i'm trying to run GridWars [http://gridwars.marune.de/](http://gridwars.marune.de/)

But i get this error

"
./gridwars: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

"

I compile C++ code on my system all the time and I checked and I have libstdc++6 installed.  Whats the issue?

obviously, you need and older version of stdc++. do "sudo apt-get libstdc++5".

---

### Post by Vadi on 2009-04-10
[http://www.getdeb.net/search.php?keywords=gridwars](http://www.getdeb.net/search.php?keywords=gridwars)

---

