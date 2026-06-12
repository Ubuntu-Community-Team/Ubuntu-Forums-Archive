---
title: "can I put sudo ./configure-args  prefix together ?"
date: 2008-06-09
forum: Education &amp; Science
---

### Post by GreenLinux@R on 2008-06-09
I am trying this


greenlinux4r@greenlinux4r-desktop:/usr/lib/R/Rmpi$ sudo ./configure-args=--with-mpi=/usr/lib/R/bin/lam714 --prefix=/usr/lib/R/site-library/Rmpi

but it won't work and I got a message saying 

sudo: please use single character options
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...

Am I missing something or putting much stuff together?

---

### Post by GreenLinux@R on 2008-06-09
I figured it out like below.  

greenlinux4r@greenlinux4r-desktop:/usr/lib/R/site-library$ [COLOR="DarkGreen"]sudo R CMD INSTALL --configure-args=--with-mpi=/usr/lib/R/bin/lam714 -l /usr/lib/R/site-library Rmpi_0.5-4.tar.gz[/COLOR]

---

