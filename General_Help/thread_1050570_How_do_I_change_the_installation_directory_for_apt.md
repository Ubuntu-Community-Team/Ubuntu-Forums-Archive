---
title: "How do I change the installation directory for apt-get? How do I use dpkg to install?"
date: 2009-01-25
forum: General Help
---

### Post by Panarchy on 2009-01-25
Hi

I'm building my linux distribution, and I have 195 'items' to install. 65 of them are Debian packages.

I would like all 65 of my .deb to be installed into a certain directory. 

When running this command; 
```
dpkg -i --instdir=/tools/debian hexedit_1.2.12-3_i386.deb
```

I get the following error;

```
root@panarchy:/home/ubuntu/Desktop/Debian Packages# dpkg -i --instdir=/tools/debian hexedit_1.2.12-3_i386.deb
(Reading database ... 83164 files and directories currently installed.)
Preparing to replace hexedit 1.2.12-3 (using hexedit_1.2.12-3_i386.deb) ...
Unpacking replacement hexedit ...
dpkg (subprocess): unable to execute old post-removal script: No such file or directory
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new post-removal script: No such file or directory
dpkg: error processing hexedit_1.2.12-3_i386.deb (--install):
 subprocess new post-removal script returned error exit status 2
dpkg (subprocess): unable to execute new post-removal script: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 hexedit_1.2.12-3_i386.deb 
```

How do I fix this error? 

Or how do I change the default install directory for apt-get?

Please reply,

Thanks in advance,

Panarchy

---

### Post by x22 on 2009-01-26
from man dpkg:

"--root=dir | --admindir=dir | --instdir=dir

Change default directories. admindir defaults to
/var/lib/dpkg and contains many files that give
information about status of installed or uninstalled
packages, etc. instdir defaults to / and refers to the
directory where packages are to be installed. instdir
is also the directory passed to chroot(2) before
running pack&#8208;age’s installation scripts, which means
that the scripts see instdir as a root directory.
Changing root changes instdir to dir and admindir to
dir/var/lib/dpkg"

probably should copy /var/lib/dpkg/* to your new admindir

---

### Post by Panarchy on 2009-01-26
Thanks. Seems complicated. I'll do my best.

Panarchy

---

