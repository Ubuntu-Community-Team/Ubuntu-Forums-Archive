---
title: "Fedora: Upgrade to Fedora9 caused apache issues"
date: 2008-06-12
forum: Fedora/RedHat and derivatives
---

### Post by amitst on 2008-06-12
Hi,

I know this is an Ubuntu forum but I hope a Fedora query will be welcome here. I upgraded a Fedora7 machine to Fedora9 and face the issue with the apache. It wouldn't start.

I had to do the following steps to make it working,
```

$ su
# cd /lib
# ln -s libssl.so.7 libssl.so.6
# ln -s libcrypto.so.7 libcrypto.so.6
# ln -s libexpat.so.1 libexpat.so.0

```

Clearly there is a mismatch between the openssl and the apache version. But I want to know why is this inconsistency and how to resolve it (I am not for this hack in the long term).

Thanks in advance,
Amit

---

### Post by PmDematagoda on 2008-06-12
This thread has been moved to the Fedora/Red Hat section.

---

### Post by amitst on 2008-06-12
The above stage was present two days ago. When I checked again after making the above post I was happy (and puzzled) to notice that the httpd has been updated with the new dependencies.

```

# ldd /usr/sbin/httpd
        linux-gate.so.1 =>  (0x0012e000)
        libm.so.6 => /lib/libm.so.6 (0x0012f000)
        libpcre.so.0 => /lib/libpcre.so.0 (0x00158000)
        libselinux.so.1 => /lib/libselinux.so.1 (0x00182000)
        libaprutil-1.so.0 => /usr/lib/libaprutil-1.so.0 (0x0019e000)
        libcrypt.so.1 => /lib/libcrypt.so.1 (0x001b8000)
        libldap-2.4.so.2 => /usr/lib/libldap-2.4.so.2 (0x001ea000)
        liblber-2.4.so.2 => /usr/lib/liblber-2.4.so.2 (0x0022c000)
        libdb-4.6.so => /usr/lib/libdb-4.6.so (0x0023b000)
        libexpat.so.1 => /lib/libexpat.so.1 (0x00383000)
        libapr-1.so.0 => /usr/lib/libapr-1.so.0 (0x003aa000)
        libpthread.so.0 => /lib/libpthread.so.0 (0x003d3000)
        libdl.so.2 => /lib/libdl.so.2 (0x003ec000)
        libc.so.6 => /lib/libc.so.6 (0x003f1000)
        /lib/ld-linux.so.2 (0x00110000)
        libuuid.so.1 => /lib/libuuid.so.1 (0x0055a000)
        libresolv.so.2 => /lib/libresolv.so.2 (0x0055e000)
        libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0x00573000)
        libssl.so.7 => /lib/libssl.so.7 (0x0058c000)
        libcrypto.so.7 => /lib/libcrypto.so.7 (0x005d7000)
        libgssapi_krb5.so.2 => /usr/lib/libgssapi_krb5.so.2 (0x00725000)
        libkrb5.so.3 => /usr/lib/libkrb5.so.3 (0x00754000)
        libcom_err.so.2 => /lib/libcom_err.so.2 (0x007f4000)
        libk5crypto.so.3 => /usr/lib/libk5crypto.so.3 (0x007f7000)
        libz.so.1 => /lib/libz.so.1 (0x0081c000)
        libkrb5support.so.0 => /usr/lib/libkrb5support.so.0 (0x00830000)
        libkeyutils.so.1 => /lib/libkeyutils.so.1 (0x00839000)

```

So this thread can be marked as closed.

---

### Post by amitst on 2008-06-13
No. Looks like I was fooled. As soon as I removed the softlinks in /lib directory the issue cropped up again. I have marked this thread as unsolved.

```
# /usr/sbin/apachectl start
httpd: Syntax error on line 209 of /etc/httpd/conf/httpd.conf: Syntax error on line 7 of /etc/httpd/conf.d/php.conf: Cannot l
oad /etc/httpd/modules/libphp5.so into server: libssl.so.6: cannot open shared object file: No such file or directory

```

---

### Post by amitst on 2008-06-14
The issue has been solved (partially) after doing the following,

```

# yum clean all
# yum update

```

The apache is now working. However the Trac on it is giving svn related error.

---

### Post by igknighted on 2008-06-16
how did you upgrade from fedora7 to fedora9?  Did you use anaconda and the new (preupgrade? i forget the name) or use yum (as you would do w/ apt in a debian based distro).  If you used the later, that's your problem.  Do a fresh install.  If you did the former... I would still lean towards a fresh install.  The upgrade software was really in beta form at best for this release, as it wasn't finished until very late.  Also remember you skipped a version too.

I realize that this isn't really helpful in solving the problem per se... just trying to point out that the system wasn't really designed for this, so there may not be a perfect solution

---

### Post by amitst on 2008-06-21
Thanks for your pointers.

I booted from the Fedora9 CD and selected the upgrade option. So I guess I used anaconda.

For now I have resolved the svn related error by first creating a link to existing library file. Then updating one of the files in the Trac installation specifically,
```
/usr/lib/python2.5/site-packages/trac/versioncontrol/cache.py
```

I typecasted the number in the postgres query to str and then it started working.

---

