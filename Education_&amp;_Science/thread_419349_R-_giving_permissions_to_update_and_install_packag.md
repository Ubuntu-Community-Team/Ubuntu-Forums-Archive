---
title: "R- giving permissions to update and install packages?"
date: 2007-04-22
forum: Education &amp; Science
---

### Post by MacD on 2007-04-22
I am new to R and new-ish to Linux


I'm trying to install and update some packages in R.
R is not able to proceed due to not having permission to mkdir in /usr/lib/R/library

what is the sensible way to edit permissions for this directory?

Thanks.

Mac

---

### Post by akniss on 2007-04-23
There are two ways to install packages in R.

If you want to install directly from a CRAN mirror, you will need to start an R session as root.  DO NOT start modifying the permissions of the install directory... this can cause major problems and is a security issue.
```
sudo R
install.packages('pkg_name')
```
A window will then appear where you can choose the CRAN mirror to use.  Once selected, it will install everything with the proper permissions.  Once installed, exit R and start it again as a normal user.
```
q()
R
```

You may also install from a local source if you have downloaded the package to your computer.  This must also be done as sudo.
```
sudo R CMD INSTALL /home/username/pkg_name.tar.gz
```

---

### Post by MacD on 2007-04-23
Good advice, thank you.

I had just done my first chmod-ing based in this advice:

[http://osdir.com/ml/lang.r.debian/2006-03/msg00005.html]("http://osdir.com/ml/lang.r.debian/2006-03/msg00005.html")

but wasn't getting anywhere. Turns out I didn't know how permissions work.  Now I do thanks to this excellent resource:

[http://catcode.com/teachmod/index.html]("http://catcode.com/teachmod/index.html")

just changed all the permissions back.

---

