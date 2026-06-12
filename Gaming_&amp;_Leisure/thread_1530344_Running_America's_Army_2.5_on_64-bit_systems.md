---
title: "Running America's Army 2.5 on 64-bit systems?"
date: 2010-07-13
forum: Gaming &amp; Leisure
---

### Post by User-007 on 2010-07-13
Hi

I have successfully installed AA 2.5. When trying to run it, an error message will appear:

> ./armyops-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory 

I have downloaded and installed libstdc++5_3.3.6-17ubuntu1_amd64.deb package, Many people report here that just installing that libstdc++5 is enough to successfully run AA2.5 on 32-bit systems. My questions is that how to get it working on 64-bit systems since it seems that only just installing that package is not enough?

Ah, I'm using Lucid.

Thanks!
User JB

---

### Post by User-007 on 2010-07-13
For your all knowledge, I just found an answer from a thread related to other software. Just downloaded 32-bit version deb package of libstdc5 and manually extracted them to /usr/lib32/.

After that everything works like a charm.

---

### Post by crjackson on 2010-07-19
Don't waste your time my friend. The latest Linux version is 2.50, then you have to search for and install libstdc++5 from an older version of Ubuntu to make it even start in Lucid.

Next you will find that punkbuster won't let you log into a server because you version is out dated (and manual updates don't work), THEN.... you can find/download/install/run pbsetup and browse to your ~/.armyops250 folder (from pbsetup) and it will update punkbuster.

After you have completed all the training and corrected all the other issues, you will find 2 servers for ONE working deployment. Neither server will have ANY players because they are using MS-Win and newer versions of AA.

It's just not worth the hassle.

---

### Post by bosshoff on 2010-08-22
I agree, the server load is definitely a bit light, but I used to play this game all the time, and even a couple of servers with people in them is enough to satisfy my nostalgia.  It is the only game I spent a long time learning every trick of, and I don't plan on "investing" that time again on another game any time soon.

---

