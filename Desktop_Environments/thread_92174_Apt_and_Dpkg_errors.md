---
title: "Apt and Dpkg errors"
date: 2005-11-18
forum: Desktop Environments
---

### Post by grahamer on 2005-11-18
**E: /var/cache/apt/archives/sanekonsole_0.2-0ubuntu1_i386.deb: files list file for package `kdenetwork-filesharing' is missing final newlin**e

I have search this form and google and found alot of the same errors but no real fixes. I installed kde everything went ok. Now when i try to install or uninstall anything I get the same error.

I tryed 
apt-get clean
dpkg and apt force and a alot more and still the same error.
i dont want to have to reinstall I have alot of junk setup and a lotof work on this system.

I know rpm has a database rebuild command but i havent been able find anything like that for debs.

Any help would be great

---

### Post by adwait on 2005-11-18
How about running
```
sudo apt-get update
```

?? Does that change anything?

EDIT: Sorry didn't read the question properly........plz ignore this.

---

### Post by grahamer on 2005-11-18
et:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Fetched 1B in 0s (2B/s)
Reading package lists... Done
i found a post that said maybe the source file is wrong so i 
deleted everything out of source file except main. No problems updating.

---

