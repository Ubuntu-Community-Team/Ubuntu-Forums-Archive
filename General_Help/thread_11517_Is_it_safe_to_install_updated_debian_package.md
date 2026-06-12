---
title: "Is it safe to install updated debian package"
date: 2005-01-17
forum: General Help
---

### Post by mendicant on 2005-01-17
I use Ubuntu (warty) on a server running gallery (gallery,sourceforge.net).  I notice that debian sent out a security update on it today.  Is it safe in general to install the package from debian, assuming all the dependencies work out correctly (or building from source if necessary)?  I'll soon try this, unless I see dire warnings about it.

BTW: I upgraded this server from woody--very easy to do (except for one little thing regarding gs-esp, which refused to download correctly, and I had to find out where it was and download it manually).  

Thanks.

---

### Post by mendicant on 2005-01-19
Ah, silly me.  I just used the version in hoary, using the old change /etc/apt/sources.list, run aptitude, upgrade only gallery, then revert sources.list.

---

