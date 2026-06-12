---
title: "[SOLVED] Update Manager please help"
date: 2008-11-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Pappalnator on 2008-11-30
Ive been having an issue all day and because of it I cant upgrade to Intrepid Ibex via Update Manager nor receive updates

No matter what source file I use (ive tried 3-4, all defaults from different people)(have also tried 2 variations of the dell.mini.canonical)
, no matter how hard I try, I cant get Update Manager to connect to my sources.

While *trying to Manage its Updates, during downloading, I press the tab to reveal individual files, and about a hundred files go by in 20 seconds saying some Hit, but most have Miss then Failed

At the end I get an error code that looks like this (varies depending on which sources.list I use, but all have the same "404 Not Found):

> Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-lpia/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-lpia/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-lpia/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-lpia/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-lpia/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-lpia/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-lpia/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-lpia/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-lpia/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Before you say anything:
[COLOR="Red"]I am sure I have a working 100% internet connection when Im doing this.

I am running Ubuntu Dell Release 8.04.1 for Mini 9

ANY Help Is Appreciated!![/COLOR]

P.S. Noob-friendly gets extra plusses! :)

---

### Post by Pappalnator on 2008-11-30
I just installed using a CD-rom

---

