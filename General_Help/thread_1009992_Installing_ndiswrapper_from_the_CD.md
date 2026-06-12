---
title: "Installing ndiswrapper from the CD"
date: 2008-12-13
forum: General Help
---

### Post by Scimu on 2008-12-13
Hi,
Im trying to get wireless working on the ubuntu PC (WPN111 is the wireless USB) and basically I ran
```

sudo apt-get install ndiswrapper

```
And it installed

Then when I try "ndiswrapper -v" it says:
Error: no ndiswrapper utils found

So I try
```

sudo apt-get install ndiswrapper-utils

```
and it says:
> 
Package ndiswrapper-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted or is only available from another source.
However the packages replace it:
ndiswrapper-common
E: Package ndiswrapper-utils has no installation candidate


I dont have internet connection on that PC as that is what im trying to get, so I cant use the online repos.

Any ideas?

---

### Post by Titan8990 on 2008-12-13
On Ubuntu 7.10 it was:

sudo apt-get install ndiswrapper-utils-1.9

---

### Post by Scimu on 2008-12-13
Brilliant fixed! Thanks

---

