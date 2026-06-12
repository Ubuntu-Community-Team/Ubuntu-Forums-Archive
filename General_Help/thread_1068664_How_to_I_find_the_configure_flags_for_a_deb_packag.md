---
title: "How to I find the configure flags for a deb package"
date: 2009-02-13
forum: General Help
---

### Post by praerien on 2009-02-13
Hi 

I'm trying to find out which configure flags that were used to compile the pure-ftp package. I can't find any compile logs in either the package or the source tar-ball. Is there a generel way to find these flags ? 

The configure flag I'm looking for in the pure-ftpd package is --without-usernames . 

Cheers
Rune

---

### Post by mc4man on 2009-02-13
You could go 
```
apt-get source pure-ftpd
```

Then in your home folder open up the pure-ftpd folder and look in debian -> rules

If you wanted to see the configure options available then cd to the source folder and run 
```
./configure --help
```


If you wanted to add --without-usernames  you could add it to the optflags= line and then build the package off of debian/rules
That will give you the exact same package(s)(in .deb form) as the repo version except for your configuration changes

---

