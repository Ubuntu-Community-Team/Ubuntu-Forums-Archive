---
title: "[SOLVED] Repistory Index Error With Dell Mini 9"
date: 2008-12-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vegetarianshrimp on 2008-12-28
I was wondering how to fix this on the Dell Mini 9:
> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Some index files failed to download, they have been ignored, or old ones used instead.

This happens with the Update Manager, Software Sources, and Synaptic Package Manager. I think the problem is that I messed up my computer somehow, and now I don't have the Dell third-party software. Could you maybe tell me how to add it again?

Thanks.

---

### Post by sirebral on 2008-12-28
Actually I think the problem is the *lpia directories do NOT exist

[http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/)

Look and see for yourself.

---

### Post by vegetarianshrimp on 2008-12-28
> **sirebral said:**
> Actually I think the problem is the *lpia directories do NOT exist

[http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/)

Look and see for yourself.
 Well I know _that_, but I think the way to fix it is to get the dell third-party things back.

---

### Post by sirebral on 2008-12-28
Dude.  You cannot connect to a directory that doesn't exist.  Software or not.

Perhaps you are requesting the directory from a place that doesn't house it.  Or maybe they are working on the repositories for the -lpia entity.

But if the directory doesn't exist no amount of third party software is going to help.

Sorry. :(

---

### Post by sirebral on 2008-12-28
Do you think maybe this is where you are supposed to be looking for those -lpia directories?

[http://dell-mini.archive.canonical.com/ubuntu/dists/](http://dell-mini.archive.canonical.com/ubuntu/dists/)

It looks like that might be the place.

---

### Post by dragonmojo on 2008-12-29
Veggie,
I do not believe you are alone, as I too have been getting this message. I believe Siberal is correct that it is pointing to a non-existent location, or one that does not contain the contents requested. I am also a new Dell Mini9 user and new to linux/ubuntu.

I have a different problem (that may have been self-induced). I no longer have access to the synaptic pkg mgr or the service sources. Bummer.

---

### Post by vegetarianshrimp on 2009-01-02
[http://ubuntuforums.org/showthread.php?t=1027616](http://ubuntuforums.org/showthread.php?t=1027616)

---

