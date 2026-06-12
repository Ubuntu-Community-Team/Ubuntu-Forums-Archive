---
title: "Debmirror missing files error"
date: 2006-10-02
forum: Desktop Environments
---

### Post by black_771 on 2006-10-02
Hello all. I'm trying to mirror an apt repo using debmirror. I've downloaded 95% of the packages, but I get 155 "file missing" errors. If I manually go to the repo and check the files that it says are missing, they are actually there. I've tried different repos to mirror, but each gives me the same errors. The missing files are completely random as well. 

Is this normal?

---

### Post by black_771 on 2006-10-06
The problem ended up being an issue with updating using the rsync protocol. When I switched it over to http or ftp, it downloaded everything correctly and also solved my pgp signature error issue.

---

### Post by ArneLovius on 2006-10-10
Hi, 

Are you installing Ubuntu from your local repository, or just updating (and installing new packages) ?

Cheers

---

### Post by grolm on 2007-12-05
I have the same problem with the script 
> /usr/bin/debmirror --nosource -m --passive --host=ua.archive.ubuntu.com \
	--root=:ubuntu --method=rsync --progress \
	--dist=gutsy,gutsy-security,gutsy-updates,gutsy-proposed \
	--ignore-release-gpg --section=main,restricted,multiverse,universe \
	--arch=i386 /media/Linux/Ubuntu/mirror/

I have tried different repositories like ubuntu.org.ua but still have the problem. 

> 
Downloaded 40 MiB in 211s at 191.34 kiB/s
Failed to download files (38251 errors)!

but the files (at least some of them) definitely exists in the repositories.
I use "Ubuntu 7.10, Gutsy Gibbon" with all recommended updates installed.

---

### Post by grolm on 2007-12-05
I am sorry but I did not note 
> sh: Syntax error: "(" unexpected
The problem is that /media/Linux/Ubuntu/mirror/ is really link on /media/DATA(Ext3)/Downloads/Linux/Ubuntu/mirror/. It has '(' symbol.Thus the debmirror script does not download to path with '(' symbol or at least to volume with name containing     '(' symbol (because in my case 'DATA(Ext3)' is mount point) ](*,).

I have tried mirroring to other volume and it works fine. \\:D/

---

