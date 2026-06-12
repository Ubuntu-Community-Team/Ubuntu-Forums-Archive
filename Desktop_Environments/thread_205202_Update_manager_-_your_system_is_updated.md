---
title: "Update manager - your system is updated?"
date: 2006-06-28
forum: Desktop Environments
---

### Post by matjaz_pirnovar on 2006-06-28
I downloaded a new update after Ubuntu notified me that there is a new update.

After successful download and installation I pressed CHECK in Update Manager and I got a window popping out saying this:

"The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://security.ubuntu.com/ubuntu/di...6/Packages.gz:](http://security.ubuntu.com/ubuntu/di...6/Packages.gz:) Bad header line
[http://security.ubuntu.com/ubuntu/di...6/Packages.gz:](http://security.ubuntu.com/ubuntu/di...6/Packages.gz:) Bad header line
[http://security.ubuntu.com/ubuntu/di...ce/Sources.gz:](http://security.ubuntu.com/ubuntu/di...ce/Sources.gz:) Bad header line
[http://security.ubuntu.com/ubuntu/di...ce/Sources.gz:](http://security.ubuntu.com/ubuntu/di...ce/Sources.gz:) Bad header line
[http://security.ubuntu.com/ubuntu/di...6/Packages.gz:](http://security.ubuntu.com/ubuntu/di...6/Packages.gz:) Bad header line
[http://security.ubuntu.com/ubuntu/di...6/Packages.gz:](http://security.ubuntu.com/ubuntu/di...6/Packages.gz:) Bad header line
[http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:](http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:) Bad header line [IP: 85.133.25.8 80]
[http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:](http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:) Bad header line [IP: 85.133.25.8 80]
[http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:](http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:) Bad header line [IP: 85.133.25.8 80]
[http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:](http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:) Bad header line [IP: 85.133.25.8 80]"

After clicking CHECK again everything was okay, my system was OK and up-to-date.

This note happened before too.

Any ideas what that might be? I don't have any connection problems. What does bad header line mean?

Thanks.

Matjaz

---

### Post by matjaz_pirnovar on 2006-06-28
I was reading "repositiry connection problem" posting below wher it says it could be proxy involved.

I do use manual proxy setting - because of my service provider NTL.

Could that be a problem?

xo

---

### Post by araz on 2006-06-28
What hapens when you type> sudo apt-get update
any errors found?

---

### Post by matjaz_pirnovar on 2006-06-28
[QUOTE=araz]What hapens when you type
any errors found?[/QUOTE]


Hi,

Thanks!

Here is what I got after typing sudo apt-get update


matjaz@PCPlus:~$ sudo apt-get update
Password:
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Errhttp://security.ubuntu.com dapper-security/main Packages
  Bad header line
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Errhttp://security.ubuntu.com dapper-security/restricted Packages
  Bad header line
Errhttp://security.ubuntu.com dapper-security/main Sources
  Bad header line
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Errhttp://security.ubuntu.com dapper-security/restricted Sources
  Bad header line
Errhttp://security.ubuntu.com dapper-security/multiverse Packages
  Bad header line
Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Errhttp://security.ubuntu.com dapper-security/universe Packages
  Bad header line
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release [30.9kB]
Get: 5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release [34.8kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Get: 6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages [95.2kB]
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources [1478B]
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages [37.9kB]
Get: 9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get: 10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources [22.2kB]
Get: 11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get: 12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/multiverse Packages [866B]
Get: 13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/universe Packages [8592B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Get: 14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages [619kB]
Get: 15 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages [4571B]
Fetched 857kB in 3s (239kB/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/bin](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/bin) ary-i386/Packages.gz  Bad header line
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restrict](http://security.ubuntu.com/ubuntu/dists/dapper-security/restrict) ed/binary-i386/Packages.gz  Bad header line
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/sou](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/sou) rce/Sources.gz  Bad header line
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restrict](http://security.ubuntu.com/ubuntu/dists/dapper-security/restrict) ed/source/Sources.gz  Bad header line
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiver](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiver) se/binary-i386/Packages.gz  Bad header line
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe) /binary-i386/Packages.gz  Bad header line
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used  instead.
matjaz@PCPlus:~$



Any ideas??

Matjaz

---

### Post by araz on 2006-06-28
I think you have wrong adresses, like this
your repo:
> [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security


mine:> [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security *

To solve this problem all you've got to do is rebuild /etc/apt/sources.list and replace the wroong adresses.
for more info take a look at [http://www.ubuntuforums.org/showthread.php?t=185971](http://www.ubuntuforums.org/showthread.php?t=185971)

---

