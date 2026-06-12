---
title: "Refencing software"
date: 2007-01-25
forum: Education &amp; Science
---

### Post by pwall on 2007-01-25
Hi all
 Im working on my masters and my University recommends the use of the procite  product to manage referencing and to manage the bibliographies.

There are two issues with this. One is  that it requires MS word and I run Open office and two is that I would prefer to run it under Linux.
Does anyone know of any  comparable LINUX software (or even open source) software ?

Thanks
Phill

---

### Post by akniss on 2007-01-25
***Bibus***
[http://bibus-biblio.sourceforge.net/wiki/index.php/Main_Page](http://bibus-biblio.sourceforge.net/wiki/index.php/Main_Page)

**Installation instructions**
    *  Add the following lines to your /etc/apt/sources.list 
```
deb http://switch.dl.sourceforge.net/sourceforge/bibus-biblio ./
deb-src http://switch.dl.sourceforge.net/sourceforge/bibus-biblio ./

```
    * Run the following commands:
```
sudo aptitude update
sudo aptitude install python-pysqlite2 bibus bibus-doc-en
sudo aptitude install mysql-server mysql-common mysql-client python-mysqldb 

```

---

