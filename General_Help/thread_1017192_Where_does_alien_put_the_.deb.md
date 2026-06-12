---
title: "Where does alien put the .deb"
date: 2008-12-20
forum: General Help
---

### Post by kkruecke on 2008-12-20
I am trying to install my Canon MP600 printer. The instructions (at [http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html]("http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html")) explain how to convert the .rpms to .debo:
```
$ sudo alien -i --scripts cnijfilter-common-*.rpm cnijfilter-mp600-*.rpm
```

I did this, but I don't see any .deb's in the same directory as the  .rpms that were inputted?

Any help is appreciated.

---

### Post by howefield on 2008-12-20
is there a /tmp folder in the alien folder ?

---

### Post by stoneage on 2008-12-20
From the man page - >  -i, --install
           Automatically install each generated package, and remove the package file after it has been installed.


It looks like you told alien to install the .debs and then remove them, but you also didn't tell alien what file extension to use(it can convert to various file types), so chances are it did nothing. (I think)


Run ```
man alien
``` in a terminal for the manual pages on alien to get information on how to.

Usage - SYNOPSIS
        alien [--to-deb] [--to-rpm] [--to-tgz] [--to-slp] [options] file [...]

EXAMPLES
       Here are some examples of the use of alien:

       alien --to-deb package.rpm
           Convert the package.rpm into a package.deb

So, I guess you would want to run ```
alien --to-deb package.rpm -i --scripts
```Which would convert and install the package and then remove the .debs

---

### Post by kkruecke on 2008-12-21
Thanks for the reply. Yes, it does look like .debs were created, installed (and deleted). I got confused because the instructions didn't make things clear. Anyway,
```
 dpkg -l |grep cnijfilter

ii  cnijfilter-common      2.70-2   IJ Printer Driver Ver.2.70 for Linux
ii  cnijfilter-mp600       2.70-3   IJ Printer Driver Ver.2.70 for Linux

```

---

### Post by drs305 on 2008-12-21
In the absence of other switches alien will convert it to the deb format.

---

### Post by stoneage on 2008-12-21
> **drs305 said:**
> In the absence of other switches alien will convert it to the deb format.

Aha! Thank you, I didn't know that. (Didn't read the manual properly!)


@ kkruecke - Glad it's working - and I learned something.

---

### Post by stoneage on 2008-12-21
Double post.

---

### Post by kkruecke on 2008-12-21
Yes, alien did successfully install the packages, but my Canon MP600 still wouldn't print. So I installed the driver for the Canon MP500. That worked. I can now print.

---

