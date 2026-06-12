---
title: "php installation,  error: Cannot find libz"
date: 2006-09-15
forum: Desktop Environments
---

### Post by baosheng on 2006-09-15
I wanna install php onto my Ubuntu dapper.

Configured by command " ./configure --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql --with-gd --with-zlib --with-bz2"

But the shell prompt outputed:

Configuring extensions
checking for OpenSSL support... no
checking for Kerberos support... no
checking for PCRE support... yes
checking for ZLIB support... yes
checking if the location of ZLIB install directory is defined... no
configure: error: Cannot find libz

How to install the libz? I tried search it in Synaptic but no result.

---

### Post by marianom on 2006-09-15
Check /usr/local/lib to find if you have zlib installed.

In my php install I added in the configuration command: --with-zlib-dir=/usr/local/lib

If it fails you can find libz here:

[http://freeware.sgi.com/Installable/libz-1.1.4.html](http://freeware.sgi.com/Installable/libz-1.1.4.html)

and more about zlib here:

[http://www.zlib.net/](http://www.zlib.net/)

---

### Post by marianom on 2006-09-15
According with the error messages you seem to have zlib installed but the configuration script fails to find it, so the additional command "--with-zlib-dir" might point out the correct working directory

---

