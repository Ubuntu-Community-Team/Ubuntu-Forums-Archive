---
title: "How to get the latst pgAdmin III"
date: 2006-08-21
forum: Desktop Environments
---

### Post by depi on 2006-08-21
Hi all!

I would like to install the lates pgAdmin III. The version in repositories is really old (1.2.2?)

I tried to build it by my own, but I get this error message: 
```
configure: error: you must specify a valid pgsql installation with --with-pgsql=DIR
```

I tried to set: ```
--with-pgsql=/usr/lib/postgresql
```, or ```
--with-pgsql=/var/lib/postgresql
``` but either of them worked.

So what is the best and cleanest way to install the newest pgAdmin III?

Another question: How is it possible that some packages are so old in repositories?

---

### Post by andersmusikka on 2006-10-29
I did:

./configure --disable-pgsql_ssl_libpq --with-pgsql-include=/usr/include/postgresql/


(all on one line)

and then it worked.

---

### Post by pavelkunc on 2007-04-17
Hi,

I was able to run compilation pgAdmin 1.6.3 now.

The key thing is to have all dependencies. It's not mentioned anywhere but you need not only standard postgres package, for me postgresql-8.2 but also **libpq-dev**. The libpq-dev contains desired **pg_config** which pgAdmin configure search for. libpq-dev will install into /usr/lib/postgresql/8.2 and this is dir you need.

This change has been done in postgresql package since postgresql-8.1 (8.1.0-2). So since this version you need to install libpq-dev.

Than ./configure --with-pgsql=/usr/lib/postgresql/8.2 and you can compile. Don't forget you need also libxslt-dev package.

Summary, suppose you have postgresql-8.2 installed.

```
apt-get install libwxgtk2.8-0 libwxgtk2.8-dev libxslt1.1 libxslt-dev  libpq-dev
```

And from you pgAdmin 1.6.3 source dir:

```
./configure --with-pgsql=/usr/lib/postgresql/8.2
```

Unfortunately... configure was OK but make all not. Compilation ended with error:

```
connection.o: In function `wxTransform2D::Transform(wxRect2DInt*) const':
connection.cpp:(.text._ZNK13wxTransform2D9TransformEP11wxRect2DInt[wxTransform2D::Transform(wxRect2DInt*) const]+0x96): undefined reference to `wxRect2DInt::operator=(wxRect2DInt const&)'
connection.o: In function `wxTransform2D::InverseTransform(wxRect2DInt*) const':
connection.cpp:(.text._ZNK13wxTransform2D16InverseTransformEP11wxRect2DInt[wxTransform2D::InverseTransform(wxRect2DInt*) const]+0x96): undefined reference to `wxRect2DInt::operator=(wxRect2DInt const&)'
collect2: ld returned 1 exit status
make[4]: *** [pgagent] Error 1
make[4]: Leaving directory `/media/media/Install/linux/pgadmin3-1.6.3/xtra/pgagent'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/media/media/Install/linux/pgadmin3-1.6.3/xtra/pgagent'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/media/media/Install/linux/pgadmin3-1.6.3/xtra'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/media/media/Install/linux/pgadmin3-1.6.3'
make: *** [all] Error 2

```

Regards

Pavel

---

### Post by pavelkunc on 2007-04-17
Actually this compile error is know issue.... see: [http://archives.postgresql.org/pgadmin-support/2007-04/msg00016.php](http://archives.postgresql.org/pgadmin-support/2007-04/msg00016.php)

---

### Post by handaxe on 2007-06-13
If you add:

```
deb http://ftp2.uk.postgresql.org/sites/ftp.postgresql.org/pgadmin3/release/ubuntu feisty pgadmin
``` to /etc/apt/sources.list you can download and install the latest version via synaptic/apt.

In case you need to know...

HA

---

