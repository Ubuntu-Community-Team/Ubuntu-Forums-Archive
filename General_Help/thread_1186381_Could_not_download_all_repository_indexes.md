---
title: "Could not download all repository indexes"
date: 2009-06-13
forum: General Help
---

### Post by Agent ME on 2009-06-13
Whenever I try to check for updates in Update Manager (or reload in Synaptic, etc), I get this error:
> **Could not download all repository indexes**
The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
```
Failed to fetch http://archive.canonical.com/ubuntu/dists/jaunty-i386/partner/binary-amd64/Packages  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/main/binary-amd64/Packages  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/restricted/binary-amd64/Packages  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/universe/binary-amd64/Packages  404 Not Found
Failed to fetch http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/jaunty-i386/main/binary-amd64/Packages  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/multiverse/binary-amd64/Packages  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-i386/main/binary-amd64/Packages  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-i386/restricted/binary-amd64/Packages  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-i386/universe/binary-amd64/Packages  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-i386/multiverse/binary-amd64/Packages  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/main/binary-amd64/Packages  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/restricted/binary-amd64/Packages  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/universe/binary-amd64/Packages  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/multiverse/binary-amd64/Packages  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports-i386/main/binary-amd64/Packages  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports-i386/restricted/binary-amd64/Packages  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports-i386/universe/binary-amd64/Packages  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports-i386/multiverse/binary-amd64/Packages  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed-i386/restricted/binary-amd64/Packages  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed-i386/main/binary-amd64/Packages  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed-i386/multiverse/binary-amd64/Packages  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-proposed-i386/universe/binary-amd64/Packages  404 Not Found [IP: 91.189.88.140 80]
Some index files failed to download, they have been ignored, or old ones used instead.
```
I notice if I try to go to any of the URLs in a browser, I get a 404. But if I remove the "-i386" part, it works fine.
[list=1][*]Why was this change made? It used to work fine a week or two ago.
[*]Why do I seem to be the only one affected by this?
[/list]
There also seem to be other problems with my repositories, looking under Software Sources. On the Ubuntu software page, everything is checkmarked, as I made it, but the Ubuntu 9.04 LiveCd appears twice. On the 3rd Party Software page, it seems to show all of my software repositories, including the main Ubuntu ones (main, restricted, universe, multiverse, security), with the "-i386" string in it.
I think I'll go through apt's files and hand-fix everything, but any idea how this happened?

**EDIT:** I just looked under /etc/apt. I'm kinda confused.
/etc/apt/sources.list
/etc/apt/foreign/sources.list
/etc/apt/native/sources.list
The ones in foreign and native look identical and correct (?) so I think I'm going to delete the foreign folder (well, move it somewhere else first, just in case).

The /etc/apt/sources.list file is odd though. It has the ubuntu partner and deluge PPA entries in it, like the other two, but it also has a section called "### ia32-apt-get entries ###", and below this are all of the incorrect jaunty-i386 entries, along with the deluge PPA and the main Ubuntu repositories again.

Argh this probably had to do with the ia32-apt-get package I installed while trying to get a 32-bit library (on 64-bit system), but then removed when it wasn't what I wanted. Going to do the "Complete Removal" option now on that package. Under the list of its installed files, it has /etc/apt/foreign and /etc/apt/native listed.

Complete removal did not kill those folders, so I think I will move /etc/apt/native/sources.list to /etc/apt/sources.list, overwriting the bad one, and then kill the native and foreign folders.

**FINAL EDIT:** That seems to have fixed every problem in my post; guess I solved it on my own. Note to anyone else: STAY AWAY FROM THE ia32-apt-get PACKAGE!

---

