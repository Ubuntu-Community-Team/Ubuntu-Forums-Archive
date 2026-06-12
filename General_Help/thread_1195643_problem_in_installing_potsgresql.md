---
title: "problem in installing potsgresql"
date: 2009-06-24
forum: General Help
---

### Post by babbar.ankit on 2009-06-24
I tried installing postgresql and using the ubuntu documentation 
I am new to ubuntu do i have to install any special package for it....
It ask me for cd when i insert it say mcheck failed (i recently installed ubuntu from this cd )
Plz help asap

Here is what i did and errors:

dspace@dspace:~$  sudo apt-get install postgresql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libpq5 postgresql-8.2 postgresql-client-8.2 postgresql-client-common
  postgresql-common
Suggested packages:
  oidentd ident-server postgresql-doc-8.2
The following NEW packages will be installed:
  libpq5 postgresql postgresql-8.2 postgresql-client-8.2
  postgresql-client-common postgresql-common
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4613kB of archives.
After unpacking 18.1MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/pool/main/p/postgresql-8.2/libpq5_8.2.5-1.1_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/pool/main/p/postgresql-common/postgresql-client-common_78_all.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/pool/main/p/postgresql-8.2/postgresql-client-8.2_8.2.5-1.1_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/pool/main/p/postgresql-common/postgresql-common_78_all.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/pool/main/p/postgresql-8.2/postgresql-8.2_8.2.5-1.1_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/pool/main/p/postgresql-8.2/postgresql_8.2.5-1.1_all.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by iponeverything on 2009-06-24
Since this was recently a fresh install, I would strongly recommend going with nothing older than 8.10 -

7.10 is no longer supported and does not receive security or critical fixes.

---

### Post by nexes128 on 2009-06-24
What does your sources file look like. (hit Alt-F2 when the run dialog shows up type "gksu gedit /etc/apt/sources.list" with out the quotes)

---

### Post by ybardagi on 2009-06-24
Try removing the cd entrance in /etc/apt/sources.list

---

### Post by babbar.ankit on 2009-06-26
I cant install postgresql in anyway, i also downloaded the 8.1 version but it ask me for super privilege:confused::( when I double click on it... Plz help me providing any way to install postgresql itz urgent

---

### Post by babbar.ankit on 2009-06-26
I tried the recommendation etc/.....
But the terminal ::confused:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package postgresql

---

