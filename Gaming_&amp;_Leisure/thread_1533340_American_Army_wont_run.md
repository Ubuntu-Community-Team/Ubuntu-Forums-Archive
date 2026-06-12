---
title: "American Army wont run"
date: 2010-07-17
forum: Gaming &amp; Leisure
---

### Post by Simdog1 on 2010-07-17
well ive installed american army and all that but then when i go in folder and doublw click armyops it doesnt do anything (ive made it executble) any help pklease? i saw on a different topic that i should typi in armyops in terminal i did and i get this error
./armyops-bin: /usr/lib/libstdc++.so.5: version `GLIBCPP_3.2' not found (required by ./armyops-bin)
./armyops-bin: /usr/lib/libstdc++.so.5: version `CXXABI_1.2' not found (required by ./armyops-bin)

help please

---

### Post by angryfirelord on 2010-07-17
It may be missing some libraries, so try installing this package:
```
sudo apt-get install libstdc++6
```

---

### Post by Simdog1 on 2010-07-18
ye figured it out i had to get the ++5 one ill find link is post it here so people will see but thanks for quick reply

---

### Post by crjackson on 2010-07-19
Don't waste your time my friend. The latest Linux version is 2.50, then you have to search for and install libstdc++5 from an older version of Ubuntu to make it even start in Lucid.

Next you will find that punkbuster won't let you log into a server because you version is out dated (and manual updates don't work), THEN.... you can find/download/install/run pbsetup and browse to your ~/.armyops250 folder (from pbsetup) and it will update punkbuster.

After you have completed all the training and corrected all the other issues, you will find 2 servers for ONE working deployment. Neither server will have ANY players because they are using MS-Win and newer versions of AA.

It's just not worth the hassle.

---

