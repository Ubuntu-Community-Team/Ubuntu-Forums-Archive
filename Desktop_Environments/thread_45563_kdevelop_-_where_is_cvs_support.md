---
title: "kdevelop - where is cvs support"
date: 2005-06-30
forum: Desktop Environments
---

### Post by Manfred on 2005-06-30
Hello,

may I ask for help ? I am a new but happy user of kubuntu and installed kdevelop and cervesia.
know i would like to have the cvs support in kdevelop enabled - unfortunately only
clearcase, subversion .. are showing in the project settings.

kdevelop3-plugins and cvs are installed and cervisia is happy exporting modules 
from my server.

what am I missing  ](*,)  ](*,) ?

Manfred from Munich
[www.regele.org](www.regele.org)

---

### Post by petan on 2005-07-22
I subscribe to this. I have also SuSE and for that I get the CVS on. I tried various changes including a full upgrade to KDE 3.4.1 but the kdevelop remained still on the 3.2.0. I am running out of options here :(

I will check with the debian packages if it has the same problems and come back to the issue if I get it solved.

Cheers,
Petan

---

### Post by petan on 2005-07-22
[QUOTE=petan]I subscribe to this. I have also SuSE and for that I get the CVS on. I tried various changes including a full upgrade to KDE 3.4.1 but the kdevelop remained still on the 3.2.0. I am running out of options here :(

I will check with the debian packages if it has the same problems and come back to the issue if I get it solved.

Cheers,
Petan[/QUOTE]
 Ok. I found the fix. You need to install the kdevelop 3.2.1 that is from the pool. I am in Finland so I used this mirror:
[http://ftp.funet.fi/pub/mirrors/ftp.kde.org/pub/kde/stable ](*,) /3.4.1/kubuntu/pool/kdevelop/](http://ftp.funet.fi/pub/mirrors/ftp.kde.org/pub/kde/stable ](*,) /3.4.1/kubuntu/pool/kdevelop/)


Then, I don't know a better way to do it but to download the kdevelop3, kdevelop3-plugins and kdevelop3-data on: /home/petan/*some_directory*.

Next, use this command:
```

# dpkg-scanpackages *some_directory* .|gzip > *some_directory*/Packages.gz.

```
Edit your /etc/apt/sources.list and add this line:
```

deb file:/home/petan *some_directory*/

```
Then, proceed and remove the old kdevelop3, kdevelop3-data, kdevelop3-plugins with:
```

# apt-get remove kdevelop3, kdevelop3-data, kdevelop3-plugins
# apt-get update
# apt-get install kdevelop3, kdevelop3-data, kdevelop3-plugins

```
Let me know if you run into troubles during the install. Anyway, after that, the new kdevelop was having unde projects, version control the demanded CVS Integration (Cervisia) menu. HURRAAA!  \\:D//

---

