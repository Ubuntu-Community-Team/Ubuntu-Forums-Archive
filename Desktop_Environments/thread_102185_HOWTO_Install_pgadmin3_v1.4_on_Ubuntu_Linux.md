---
title: "HOWTO: Install pgadmin3 v1.4 on Ubuntu Linux"
date: 2005-12-11
forum: Desktop Environments
---

### Post by jbuberel on 2005-12-11
For anyone else who would like to make use of the newer and much improved version of pgadmin3 (the postgresql administration and database development tool), I have written a short HOWTO here:

[Jason's HOWTO install pgadmin3 v1.4 on Ubuntu Linux]("http://www.buberel.org/serendipity/index.php?/archives/219-Building-and-installing-pgadmin3-v1.4-for-Ubuntu-Linux.html")

Hope this helps!

-jason

---

### Post by Roderik on 2006-02-25
I've been using this how to for a while now, but i had some time on my hands so i tried to modify the process to create a 1.4.1 version. Alas, i have no experience with creating debs so i looked through some of the files and i came up with this:

```

wget http://wwwmaster.postgresql.org/redir?ftp%3A%2F%2Fftp.be.postgresql.org%2Fpostgresql%2Fpgadmin3%2Frelease%2Fv1.4.1%2Fsrc%2Fpgadmin3-1.4.1.tar.gz
tar vxzf pgadmin3-1.4.1.tar.gz
cd pgadmin3-1.4.1
./configure --prefix=/usr --mandir=\${prefix}/share/man --infodir=\${prefix}/share/info --with-wx=/usr --with-wx-config=wx-config --with-pgsql-include="/usr/include/postgresql -I./include" --enable-gtk2 --enable-unicode
make
checkinstall

```

offcourse make sure you have got checkinstall build-essential etc

The resulting .deb can be found here: [http://www.vanderveer.be/pgadmin3-1.4.1_1.4.1-1_i386.deb](http://www.vanderveer.be/pgadmin3-1.4.1_1.4.1-1_i386.deb)

one remark, i noticed that the building with apt-get used a i486 host, while my way uses i686, so this deb might not work on other ix86 hosts.

---

### Post by jbuberel on 2006-03-10
Just tried using Roderik's instructions with version 1.4.2, and works quite well. The only issue that I ran into was needing to remove my previous pgadmin3 install prior to installing this new package:

dpkg --remove pgadmin3 pgadmin3-data

then:

dpkd --install pgadmin3-1.4.2_1.4.2-1_i386.deb

works great!

---

### Post by Roderik on 2006-03-12
Just did a clean ubuntu breezy install and i noticed that to use the instrictions above jou need some development files. 

You can install the deps with this command: 
```
apt-get build-dep pgadmin3 pgadmin3-data
```

---

### Post by chylek_marcin on 2006-09-10
pgadmin3 1.4.3
[http://blog.chylek.pl/ubuntu-dapper-instalacja-pgadmin3-14x](http://blog.chylek.pl/ubuntu-dapper-instalacja-pgadmin3-14x)

---

### Post by Leec on 2006-09-29
I've been trying to get pgadmin3 installed and I haven't been able to get the following to work in sources.list:

deb [ftp://ftp3.us.postgresql.org/pub/postgresql/pgadmin3/release/debian](ftp://ftp3.us.postgresql.org/pub/postgresql/pgadmin3/release/debian) stable pgadmin
deb-src [ftp://ftp3.us.postgresql.org/pub/postgresql/pgadmin3/release/debian](ftp://ftp3.us.postgresql.org/pub/postgresql/pgadmin3/release/debian) stable pgadmin

I get a message that says:  Failed to fetch [ftp://ftp3.us](ftp://ftp3.us).......
and then the message Could not resolve 'ftp3.us.postgresql.org'
Unknown error executing gpgv

Anyone have any other ideas as to what could be wrong with this?
Lee

---

### Post by zuzkins on 2006-10-17
Hello,
I had same problem, so i just searched their ftp for simillar directories and found that if you substitue repositories mentioned in the howto with:
deb [ftp://ftp.us.postgresql.org/pub/mirrors/postgresql/pgadmin3/release/debian](ftp://ftp.us.postgresql.org/pub/mirrors/postgresql/pgadmin3/release/debian) stable pgadmin
deb-src [ftp://ftp.us.postgresql.org/pub/mirrors/postgresql/pgadmin3/release/debian](ftp://ftp.us.postgresql.org/pub/mirrors/postgresql/pgadmin3/release/debian) stable pgadmin
you can get your pgadmin3 working in version 1.4.0
Hope it will help someone.

---

### Post by Roderik on 2006-11-17
1.6.0 is released, unfortunatly it depends on wxwidgets 2.7+ and i cant seem to get it compiled. Anybody else have any success?

---

### Post by jbuberel on 2006-11-17
Indeed - it does depend on a version of wxWidgets that is more recent than what is available in Edgy. I did try to install the .deb builds of wxWidgets v2.8, but I would definitely NOT suggest you take this approach. It didn't work, and I had to back out all of the upgrades.

I am going to try and build pgadmin v1.6 from source using a separate build (from source) of wxWidgets v2.8 into a safe location (/opt/wxwidgets-2.8/). I will let others know if that works.

-jason

---

### Post by jbuberel on 2006-11-18
This recipe unfortunately does not really follow the ubuntu/debian way of things (generating .deb files that are installed and managed), but it will get you a working version of pgAdmin3 v1.6 that runs quite nicely on Ubuntu 6.10/Edgy:

[LIST]
[*]Download pgAdmin v1.6 source archive
[pgAdmin v1.6]("http://wwwmaster.postgresql.org/download/mirrors-ftp?file=pgadmin3%2Frelease%2Fv1.6.0%2Fsrc%2Fpgadmin3-1.6.0.tar.gz")
[*]Download the wxWidgets v2.8 source archive
[wxWidgets v2.8.0]("http://prdownloads.sourceforge.net/wxwindows/wxWidgets-2.8.0-rc1.tar.bz2")
[*]Unzip, configure, compile and install wxWidgets
```
tar jxf wxWidgets-2.8.0.tar.bz2
cd wxWidgets-2.8.0
./configure --prefix=/opt/wxWidgets-2.8/ --with-gtk --enable-gtk2 --enable-unicode --enable-mimetype=no --debug=no
make
make install
```
[*]Unzip, configure, compile and install pgAdmin. Substitute your actual Postgres installation directory as appropriate, of couse.
```
tar zxf pgadmin3-1.6.0.tar.gz
cd pgadmin3-1.6.0
./configure --prefix=/opt/pgadmin-1.6 --with-wx=/opt/wxWidgets-2.8/ --with-wx=2.8 --with-pgsql=/opt/postgres-8.1.4/
make
make install

```
[*]Add the wxWidgets libraries to your system link/lib path by editing the '/etc/ld.so.conf' file (as root) and adding the path:
```
/opt/wxWidgets-2.8/lib
```
to the end of the file. Then rebuild the linker database:
```
sudo ldconfig
```
[/LIST]
You should now be able to run pgAdmin with the command:
```
/opt/pgadmin-1.6/bin/pgadmin3
```

---

### Post by Roderik on 2006-11-20
It almost worked, some changes to the configure lines though:

for wxWidgets
```

./configure --prefix=/opt/wxWidgets-2.8/ --with-gtk --enable-gtk2 --enable-unicode --enable-mimetype=no

```

for pgadmin
```

./configure --prefix=/opt/pgadmin-1.6 --with-wx=/opt/wxWidgets-2.8/ --with-wx-version=2.8  

```

edit: crap pgadmin does not compile :( 

```
In file included from ../src/include/pgAdmin3.h:22,
                 from ./pgAdmin3.cpp:13:
../src/include/ctl/ctlSQLBox.h:17:24: error: wx/stc/stc.h: No such file or directory

```

---

### Post by Homer on 2006-12-07
Hello,

I had the same problem...

Do this and it will work :)

```

cd wxWidgets-2.8.0-rc1/contrib
make
sudo make install
cd ../../pgadmin3-1.6.1/
make distclean
./configure --prefix=/opt/pgadmin-1.6.1 --with-wx=/opt/wxWidgets-2.8/ --with-wx-version=2.8
make
sudo make install

```

---

