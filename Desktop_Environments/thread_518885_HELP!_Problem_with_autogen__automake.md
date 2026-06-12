---
title: "HELP! Problem with autogen / automake"
date: 2007-08-06
forum: Desktop Environments
---

### Post by jackkerouac on 2007-08-06
Hello,

When I try to use ./autogen.sh on anything (not just one type of program), I get the following response:

```
Can't locate Automake/Config.pm in @INC (@INC contains: /usr/local/share/automake-1.10 /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 .) at /usr/local/bin/aclocal line 39.
BEGIN failed--compilation aborted at /usr/local/bin/aclocal line 39.
Can't locate Automake/Struct.pm in @INC (@INC contains: /usr/local/bin/automake-1.9 /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 .) at /usr/local/bin/automake line 48.
BEGIN failed--compilation aborted at /usr/local/bin/automake line 48.
autoreconf2.50: Entering directory `.'
autoreconf2.50: configure.ac: not using Gettext
autoreconf2.50: running: aclocal  --output=aclocal.m4t
Can't locate Automake/Config.pm in @INC (@INC contains: /usr/local/share/automake-1.10 /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 .) at /usr/local/bin/aclocal line 39.
BEGIN failed--compilation aborted at /usr/local/bin/aclocal line 39.
autoreconf2.50: aclocal failed with exit status: 2
```

Any ideas on what could help?

---

### Post by RedSquirrel on 2007-08-06
Do you have **libtool** installed? If not, try installing it.

```
sudo apt-get install libtool
```

---

