---
title: "Problems with subversion on intrepid (with a fix)"
date: 2009-03-19
forum: General Help
---

### Post by Copperblade on 2009-03-19
I was getting this message when using svn on intrepid:

```

svn: error while loading shared libraries: libldap-2.3.so.0: cannot open shared object file: No such file or directory

```

I searched online, and I wasn't able to find others having this problem, so maybe I'm the only one.  But just in case, I found that linking to later versions of the libraries seems to work fine.  For example, for svn I had to do:

```

sudo ln -s /usr/lib/libldap-2.4.so.2 /usr/lib/libldap-2.3.so.0
sudo ln -s /usr/lib/liblber-2.4.so.2 /usr/lib/liblber-2.3.so.0
sudo ln -s /usr/lib/libdb-4.6.so /usr/lib/libdb-4.2.so
sudo ln -s /usr/lib/libneon.so.27 /usr/lib/libneon.so.26

```

---

