---
title: "Gnucash 2.0.1 build/install"
date: 2006-08-17
forum: Desktop Environments
---

### Post by Cable on 2006-08-17
How would I go about building and installing gnucash 2.0.1 via checkinstall?  I have the source, I went to the directory and did
```

./configure

```
and
```

make

```
but the install failed when I tried to finish up with...
```

sudo checkinstall

```
Guidance anyone??

---

### Post by philippe_carlo on 2006-08-17
Should you not do 
```
sudo make install
``` first?

---

### Post by DoktorSeven on 2006-08-17
No, checkinstall replaces make install by creating a debian package to install from.

What exactly is the output of sudo checkinstall?

---

### Post by Cable on 2006-08-17
> **DoktorSeven said:**
> What exactly is the output of sudo checkinstall?

It's kinda long, but here you go...
```

caleb@Cable:~/.installfiles/Gnucash/gnucash-2.0.1$ sudo checkinstall

checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]: n

Installing with "make install"...

========================= Installation results ===========================
./make-gnucash-potfiles > ./po/POTFILES.in
make  install-recursive
make[1]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1'
Making install in .
make[2]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1'
cd . && /bin/sh ./config.status gsf-config.h
true_fopen == 0 for fopen64("/proc/mounts", "r")
config.status: creating gsf-config.h
config.status: gsf-config.h is unchanged
cd . && /bin/sh ./config.status goffice-features.h
true_fopen == 0 for fopen64("/proc/mounts", "r")
config.status: creating goffice-features.h
config.status: goffice-features.h is unchanged
make[3]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c 'gnucash-config' '/usr/local/bin/gnucash-config'
true_fopen == 0 for fopen64("/proc/mounts", "r")
test -z "/usr/local/share/gnucash/doc" || mkdir -p -- "/usr/local/share/gnucash/doc"
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'AUTHORS' '/usr/local/share/gnucash/doc/AUTHORS'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'COPYING' '/usr/local/share/gnucash/doc/COPYING'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'ChangeLog' '/usr/local/share/gnucash/doc/ChangeLog'true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'ChangeLog.2005' '/usr/local/share/gnucash/doc/ChangeLog.2005'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'ChangeLog.2004' '/usr/local/share/gnucash/doc/ChangeLog.2004'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'ChangeLog.2003' '/usr/local/share/gnucash/doc/ChangeLog.2003'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'DOCUMENTERS' '/usr/local/share/gnucash/doc/DOCUMENTERS'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'HACKING' '/usr/local/share/gnucash/doc/HACKING'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'INSTALL' '/usr/local/share/gnucash/doc/INSTALL'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'LICENSE' '/usr/local/share/gnucash/doc/LICENSE'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'NEWS' '/usr/local/share/gnucash/doc/NEWS'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'README' '/usr/local/share/gnucash/doc/README'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'README.patches' '/usr/local/share/gnucash/doc/README.patches'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'README.dependencies' '/usr/local/share/gnucash/doc/README.dependencies'
true_fopen == 0 for fopen64("/proc/mounts", "r")
test -z "/usr/local/share/aclocal" || mkdir -p -- "/usr/local/share/aclocal"
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'gnucash.m4' '/usr/local/share/aclocal/gnucash.m4'
true_fopen == 0 for fopen64("/proc/mounts", "r")
make[3]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1'
make[2]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1'
Making install in doc
make[2]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/doc'
Making install in examples
make[3]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/doc/examples'
make[4]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/doc/examples'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/gnucash/doc/examples" || mkdir -p -- "/usr/local/share/gnucash/doc/examples"
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'Money95bank_fr.qif' '/usr/local/share/gnucash/doc/examples/Money95bank_fr.qif'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'Money95invst_fr.qif' '/usr/local/share/gnucash/doc/examples/Money95invst_fr.qif'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'Money95mfunds_fr.qif' '/usr/local/share/gnucash/doc/examples/Money95mfunds_fr.qif'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'Money95stocks_fr.qif' '/usr/local/share/gnucash/doc/examples/Money95stocks_fr.qif'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'README' '/usr/local/share/gnucash/doc/examples/README'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'abc-all.qif' '/usr/local/share/gnucash/doc/examples/abc-all.qif'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'abc.qif' '/usr/local/share/gnucash/doc/examples/abc.qif'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'bogus.qif' '/usr/local/share/gnucash/doc/examples/bogus.qif'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'cbb-export.qif' '/usr/local/share/gnucash/doc/examples/cbb-export.qif'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'currency.xac' '/usr/local/share/gnucash/doc/examples/currency.xac'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'currency_tree_xml.xac' '/usr/local/share/gnucash/doc/examples/currency_tree_xml.xac'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'every.qif' '/usr/local/share/gnucash/doc/examples/every.qif'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'ms-money.qif' '/usr/local/share/gnucash/doc/examples/ms-money.qif'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'quicktest.qif' '/usr/local/share/gnucash/doc/examples/quicktest.qif'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'splitdemo.xac' '/usr/local/share/gnucash/doc/examples/splitdemo.xac'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'swipe.qif' '/usr/local/share/gnucash/doc/examples/swipe.qif'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'taxreport.xac' '/usr/local/share/gnucash/doc/examples/taxreport.xac'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'test.xac' '/usr/local/share/gnucash/doc/examples/test.xac'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'test2.xac' '/usr/local/share/gnucash/doc/examples/test2.xac'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'test3.xac' '/usr/local/share/gnucash/doc/examples/test3.xac'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'test4.xac' '/usr/local/share/gnucash/doc/examples/test4.xac'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'trading.xac' '/usr/local/share/gnucash/doc/examples/trading.xac'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'trading2.xac' '/usr/local/share/gnucash/doc/examples/trading2.xac'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'web.qif' '/usr/local/share/gnucash/doc/examples/web.qif'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'xfer.xac' '/usr/local/share/gnucash/doc/examples/xfer.xac'
true_fopen == 0 for fopen64("/proc/mounts", "r")
make[4]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/doc/examples'
make[3]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/doc/examples'
make[3]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/doc'
make[4]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/doc'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/gnucash/doc" || mkdir -p -- "/usr/local/share/gnucash/doc"
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'README.francais' '/usr/local/share/gnucash/doc/README.francais'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'README.german' '/usr/local/share/gnucash/doc/README.german'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'guile-hackers.txt' '/usr/local/share/gnucash/doc/guile-hackers.txt'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'projects.html' '/usr/local/share/gnucash/doc/projects.html'
true_fopen == 0 for fopen64("/proc/mounts", "r")
test -z "/usr/local/share/man/man1" || mkdir -p -- "/usr/local/share/man/man1"
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 './gnc-prices.1' '/usr/local/share/man/man1/gnc-prices.1'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 './gnucash.1' '/usr/local/share/man/man1/gnucash.1'
true_fopen == 0 for fopen64("/proc/mounts", "r")
test -z "/usr/local/share/gnucash" || mkdir -p -- "/usr/local/share/gnucash"
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'tip_of_the_day.list' '/usr/local/share/gnucash/tip_of_the_day.list'
true_fopen == 0 for fopen64("/proc/mounts", "r")
make[4]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/doc'make[3]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/doc'make[2]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/doc'Making install in lib
make[2]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib'
Making install in libc
make[3]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/libc'
make[4]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/libc'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/libc'
make[3]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/libc'
Making install in glib26
make[3]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/glib26'
make[4]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/glib26'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/glib26'
make[3]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/glib26'
Making install in guile-www
make[3]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/guile-www'
make[4]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/guile-www'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/gnucash/guile-modules/www" || mkdir -p -- "/usr/local/share/gnucash/guile-modules/www"
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'cgi.scm' '/usr/local/share/gnucash/guile-modules/www/cgi.scm'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'http.scm' '/usr/local/share/gnucash/guile-modules/www/http.scm'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'main.scm' '/usr/local/share/gnucash/guile-modules/www/main.scm'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'url.scm' '/usr/local/share/gnucash/guile-modules/www/url.scm'
true_fopen == 0 for fopen64("/proc/mounts", "r")
make[4]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/guile-www'
make[3]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/guile-www'
Making install in srfi
make[3]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/srfi'
make[4]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/srfi'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/gnucash/guile-modules/srfi" || mkdir -p -- "/usr/local/share/gnucash/guile-modules/srfi"
true_fopen == 0 for fopen64("/proc/mounts", "r")
make[4]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/srfi'
make[3]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/srfi'
Making install in goffice-0.0.4
make[3]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4'
Making install in goffice
make[4]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice'
make  install-recursive
make[5]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice'
Making install in utils
make[6]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/utils'
make  install-am
make[7]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/utils'
make[8]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/utils'
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
true_fopen == 0 for fopen64("/proc/mounts", "r")
test -z "/usr/local/share/gnucash/goffice//patterns" || mkdir -p -- "/usr/local/share/gnucash/goffice//patterns"
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'svg-patterns.xml' '/usr/local/share/gnucash/goffice//patterns/svg-patterns.xml'
true_fopen == 0 for fopen64("/proc/mounts", "r")
make[8]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/utils'
make[7]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/utils'
make[6]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/utils'
Making install in data
make[6]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/data'
make[7]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/data'
make[7]: Nothing to be done for `install-exec-am'.
make[7]: Nothing to be done for `install-data-am'.
make[7]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/data'
make[6]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/data'
Making install in app
make[6]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/app'
make[7]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/app'
make[7]: Nothing to be done for `install-exec-am'.
make[7]: Nothing to be done for `install-data-am'.
make[7]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/app'
make[6]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/app'
Making install in graph
make[6]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/graph'
make[7]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/graph'
make[7]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/gnucash/goffice//glade" || mkdir -p -- "/usr/local/share/gnucash/goffice//glade"
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'gog-guru.glade' '/usr/local/share/gnucash/goffice//glade/gog-guru.glade'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'gog-guru-type-selector.glade' '/usr/local/share/gnucash/goffice//glade/gog-guru-type-selector.glade'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'gog-object-prefs.glade' '/usr/local/share/gnucash/goffice//glade/gog-object-prefs.glade'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'gog-chart-prefs.glade' '/usr/local/share/gnucash/goffice//glade/gog-chart-prefs.glade'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'gog-style-prefs.glade' '/usr/local/share/gnucash/goffice//glade/gog-style-prefs.glade'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'gog-axis-prefs.glade' '/usr/local/share/gnucash/goffice//glade/gog-axis-prefs.glade'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'gog-error-bar-prefs.glade' '/usr/local/share/gnucash/goffice//glade/gog-error-bar-prefs.glade'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'gog-reg-curve-prefs.glade' '/usr/local/share/gnucash/goffice//glade/gog-reg-curve-prefs.glade'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'gog-reg-eqn-prefs.glade' '/usr/local/share/gnucash/goffice//glade/gog-reg-eqn-prefs.glade'
true_fopen == 0 for fopen64("/proc/mounts", "r")
make[7]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/graph'
make[6]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/graph'
Making install in gtk
make[6]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/gtk'
make[7]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/gtk'
make[7]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/gnucash/goffice//glade" || mkdir -p -- "/usr/local/share/gnucash/goffice//glade"
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'go-rotation-sel.glade' '/usr/local/share/gnucash/goffice//glade/go-rotation-sel.glade'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'go-font-sel.glade' '/usr/local/share/gnucash/goffice//glade/go-font-sel.glade'
true_fopen == 0 for fopen64("/proc/mounts", "r")
 /usr/bin/install -c -m 644 'go-format-sel.glade' '/usr/local/share/gnucash/goffice//glade/go-format-sel.glade'
true_fopen == 0 for fopen64("/proc/mounts", "r")
make[7]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/gtk'
make[6]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/gtk'
Making install in drawing
make[6]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/drawing'
make[7]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/drawing'
make[7]: Nothing to be done for `install-exec-am'.
make[7]: Nothing to be done for `install-data-am'.
make[7]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/drawing'
make[6]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/drawing'
Making install in ms-compat
make[6]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/ms-compat'
make[7]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/ms-compat'
make[7]: Nothing to be done for `install-exec-am'.
make[7]: Nothing to be done for `install-data-am'.
make[7]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/ms-compat'
make[6]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/ms-compat'
Making install in cut-n-paste
make[6]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/cut-n-paste'
Making install in pcre
make[7]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/cut-n-paste/pcre'
make[8]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/cut-n-paste/pcre'
make[8]: Nothing to be done for `install-exec-am'.
make[8]: Nothing to be done for `install-data-am'.
make[8]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/cut-n-paste/pcre'
make[7]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/cut-n-paste/pcre'
Making install in foocanvas
make[7]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/cut-n-paste/foocanvas'
make  install-am
make[8]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/cut-n-paste/foocanvas'
make[9]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/cut-n-paste/foocanvas'
make[9]: Nothing to be done for `install-exec-am'.
make[9]: Nothing to be done for `install-data-am'.
make[9]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/cut-n-paste/foocanvas'
make[8]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/cut-n-paste/foocanvas'
make[7]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/cut-n-paste/foocanvas'
make[7]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/cut-n-paste'
make[8]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/cut-n-paste'
make[8]: Nothing to be done for `install-exec-am'.
make[8]: Nothing to be done for `install-data-am'.
make[8]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/cut-n-paste'
make[7]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/cut-n-paste'
make[6]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice/cut-n-paste'
make[6]: Entering directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice'
/bin/sh ../../../libtool --tag=CC --mode=link gcc  -g -O2 -Wall -Wunused -Wmissing-prototypes -Wmissing-declarations   -Wdeclaration-after-statement -Wno-pointer-sign -D_FORTIFY_SOURCE=2 -pthread -lgsf-gnome-1 -lgsf-1 -lgnomevfs-2 -lxml2 -lz -lbonobo-2 -lgconf-2 -lgobject-2.0 -lbonobo-activation -lORBit-2 -lm -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0    -o libgoffice-1.la -rpath /usr/local/lib/gnucash -version-info 0:4:0  goffice.lo  cut-n-paste/pcre/libpcre.la utils/libgoffice-utils.la app/libgoffice-app.la data/libgoffice-data.la gtk/libgoffice-gtk.la cut-n-paste/foocanvas/libfoocanvas.la graph/libgoffice-graph.la drawing/libgoffice-drawing.la ms-compat/libgoffice-ms-compat.la -Wl,--export-dynamic -pthread -lglade-2.0 -lgnomeprint-2-2 -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnome-keyring -lgnomecanvas-2 -lgnome-2 -lpopt -lart_lgpl_2 -lpangoft2-1.0 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgsf-gnome-1 -lgsf-1 -lgnomevfs-2 -lxml2 -lz -lbonobo-2 -lgconf-2 -lgobject-2.0 -lbonobo-activation -lORBit-2 -lm -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0    -lpopt -lm  -lm
grep: /usr/lib/libXrender.la: No such file or directory
/bin/sed: can't read /usr/lib/libXrender.la: No such file or directory
libtool: link: `/usr/lib/libXrender.la' is not a valid libtool archive
make[6]: *** [libgoffice-1.la] Error 1
make[6]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice'
make[5]: *** [install-recursive] Error 1
make[5]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice'
make[4]: *** [install] Error 2
make[4]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4/goffice'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib/goffice-0.0.4'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1/lib'make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/caleb/.installfiles/Gnucash/gnucash-2.0.1'
make: *** [install] Error 2

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK

Bye.

```

---

### Post by DoktorSeven on 2006-08-17
Well, this:

```
grep: /usr/lib/libXrender.la: No such file or directory
/bin/sed: can't read /usr/lib/libXrender.la: No such file or directory
libtool: link: `/usr/lib/libXrender.la' is not a valid libtool archive
```

is your problem, but I don't know how to fix since apparently libXrender.la is not provided in the libXrender packages.  I found a few references to libXrender.la problems in searches, and it's *possible* that you can solve it by making your own libXrender.la (.la are just descriptive text files) in /usr/lib. though I have no idea if it would work correctly or not.  Basically, if you want to try it, you do so at your own risk since I'm sure there's a "right" way to do it that I'm not aware of...

Someone posted a possible working libXrender.la [here](http://mail.kde.org/pipermail/digikam-users/2006-April/001300.html). Try it (make a new file /usr/lib/libXrender.la as root and paste the file contents given there into it) and see if gnucash successfully links and installs with it.  Just take care not to delete or overwrite anything in /usr/lib already.

---

### Post by Cable on 2006-09-09
I fixed the error I was receiving before by following the directions [here]("http://www.ubuntuforums.org/showthread.php?t=238449").  So it no longer gives that error.  However, during make, it seems to continuously loop.  It outputs long errors such as these over and over.  Meaning, it will say some things, output these errors, do some other stuff, then output these errors again.
```

libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libltdl.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgconf-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libORBit-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgtk-x11-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgdk-x11-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libatk-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgdk_pixbuf-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libpangocairo-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libpango-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libcairo.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgwrap-guile-runtime.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgwrap-core-runtime.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libffi.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libguile.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libguile-ltdl.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libqthreads.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgthread-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgobject-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgmodule-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libglib-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libpopt.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libltdl.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgconf-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libORBit-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgtk-x11-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgdk-x11-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libatk-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgdk_pixbuf-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libpangocairo-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libpango-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libcairo.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgwrap-guile-runtime.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgwrap-core-runtime.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libguile.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libguile-ltdl.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libqthreads.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libffi.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgthread-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgobject-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgmodule-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libglib-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libpopt.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libltdl.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgconf-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libORBit-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgtk-x11-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgdk-x11-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libatk-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgdk_pixbuf-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libpangocairo-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libpango-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libcairo.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgwrap-guile-runtime.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgwrap-core-runtime.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libguile.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libguile-ltdl.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libqthreads.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libffi.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgthread-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgobject-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgmodule-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libglib-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libpopt.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgconf-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libORBit-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgthread-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgtk-x11-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgdk-x11-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libatk-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgdk_pixbuf-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libpangocairo-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libpango-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libcairo.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgobject-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgmodule-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libglib-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libpopt.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgthread-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgobject-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libgmodule-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libglib-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.0.3/../../..//libpopt.la' seems to be moved

``` I have no idea what to do about these.  Anybody know?  Attached is a screenshot of more of the errors.

---

### Post by sirmrmatt on 2006-11-21
```

libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libglade-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgnomeui-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libbonoboui-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgnome-keyring.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgnomecanvas-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgnome-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libart_lgpl_2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libpangoft2-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgtk-x11-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgdk-x11-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libatk-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgdk_pixbuf-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libpangocairo-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libpango-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libcairo.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libbonobo-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgnomevfs-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libxml2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libbonobo-activation.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgconf-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgobject-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libORBit-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgmodule-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgthread-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libglib-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libpopt.la' seems to be moved


```

Why am I getting this, building GnuCash? It just repeats and then spits some gobbeldygook out and repeats. Over and over, never erroring out or stopping.

I am tired of this issue...I can't seem to figure it out on my own.

Anyone have any ideas for me? I don't understand this stuff.

- Matt

---

### Post by Cable on 2006-11-22
I ended up just letting it continue on even though it was spitting out those messages, and apparently they aren't relevant.  It finished compiling, installed, and worked perfectly fine.  So, just let it keep going and see if it finishes, it may take a little while.

---

### Post by sirmrmatt on 2006-11-22
Interesting.

I mean, I have been STRUGGLING, on principle alone, to get GnuCash working WITH ofx directconnect *enabled* (and I guess therefore HBCI enabled)! I don't want to just "give in" and buy QuickBooks or whatever to run through Wine. FORGET THAT! :-| I would prefer to be all-open source and be able to convert friends and family with confidence. 

**The thought of having to manually import QIF files or whatever, when it is quite possible to easily get real-time transaction data on-demand is just untenable.** Plus, I have to wait til the end of the month until I can "export" a QIF file. That means that info is more often than not totally outdated and not entirely helpful at any given day of the month other than the first or whatever. 

This function, I believe, is an essential function for wider Linux adoption. Certainly is for me, and I intend on fixing it on my computer. Hopefully it won't be such a wild goose chase for users in the future.

WHY is it such a problem to make some option to have ofx enabled in Ubuntu? Personal and small business accounting is a BIG DEAL to a LOT of people. 

I have been willing to put aside my small business need to organize my finances in hopes of trying to solve this issue of not having the OFX DirectConnect available in GnuCash. 

The process has led me through many installs and uninstalls, but it seems like the best I've been able to find is a process something like this:

1. Download and compile latest openssl and libssl-dev source or packages. (Supposedly the big "breaker" issue for OFX support on GnuCash in Debian/Ubuntu is that the ssl libraries have some sort of non-GPL license and that kills the whole deal for purists...well I am not one of them! lol...I use Automatix2 with zero qualms, etc...so I downloaded the latest version of openssl and compiled it, but then got the libssl-dev from synaptic I believe...I am not an expert, do not know if that was best route, but those two through their respective methods stopped the compile error messages I was getting with AqBanking telling me I needed them)

2. Download and compile latest AqBanking (2.2.3 as of this writing).

3. Download and compile the latest LibOFX (0.8.2 as of this writing)

4. Download and try to compile the latest GnuCash (2.0.2) and see what other dependancies come up, if any.

Now I am on this apparent "infinite loop" which, as I am told above, might end well if I let it go instead of stopping it after some hours each time. I will certainly let the make'ing roll. 

Will report back if the looping "libtool: link: warning:" does or does not stop! Either outcome will be instructive, I'm sure.

Thanks for the hint, my friend.

- Matt

---

### Post by michael.fries on 2006-11-22
Hi Matt,

I would like to get my ofx working as well.  And, what you have written down is pretty much the closest thing I have found to a set of instructions so far.  But I am confused by some parts.  Why download and compile openssl and libssl-dev instead of installing them from synaptic? Why download and compile aqbanking and libOFX instead of installing them from synaptic?  Would these recompiled applications have different properties than the ones that are downloaded?

Thanks,
Mike

---

### Post by sirmrmatt on 2006-11-22
I am no expert! lol...

However, I have gathered this:

1. You have to compile gnucash with the --enable-hbci and --enable-ofx "flags" (or whatever they call them) when you do the ./configure step, because the Debian repositories do not have those enabled because aqbanking or libofx uses some sort of ssl thing that is not licensed to their liking under the GPL. So, you gotta do it yourself.

2. First you must have latest libofx and aqbanking installed (search google for their homepages, then unzip, enter folder and run 

./configure --enable-hbci --enable-ofx
make
make install

as is standard (I guess)

I was getting those repetitious warnings about "must have been moved" or something like this (as above) but just let it run (and run and run) and it worked for me!

So anyhow, don't use synaptic or apt-get or aptitutde as u will get a non-ofx-enabled version.

At this point, though, I am now at my next challenge of trying to figure out all of this:

[http://wiki.gnucash.org/wiki/OFX_Direct_Connect_Bank_Settings](http://wiki.gnucash.org/wiki/OFX_Direct_Connect_Bank_Settings) 
[http://www.jongsma.org/gc/](http://www.jongsma.org/gc/)

Got the first script on the second link to download all that data, but now am just looking to figure out how to implement it.

Seems like I was able to search the Bank.xml file it downloaded for my bank, which then refers you to the appropriately-numbered xml file in the "fi" folder.

In any event, cross THAT bridge when you get to it.


- Matt

---

### Post by michael.fries on 2006-11-23
Hi,

Just wondering..

When attempting ./configure for aqbanking, I am informed of several missing applications (?), although a number of them seem optional.  The specific message is this:

configure: *** Libchipcard2-client is required for backend "AqGeldKarte". Specify --with-backends="aqhbci aqdtaus aqofxconnect" to build aqbanking without that backend.
configure: *** GTK2 is required for GTK2-frontend "g2banking". Specify --with-frontends="cbanking qbanking kbanking" to build aqbanking without that frontend.
configure: *** The library "libglade2" is required for GTK2-frontend "g2banking". Specify --with-frontends="cbanking qbanking kbanking" to build aqbanking without that frontend.
configure: *** QT3 is required for QT-frontend "qbanking". Specify --with-frontends="cbanking g2banking" to build aqbanking without that frontend.
configure: *** KDE3 is required for KDE-frontend "kbanking". Specify --with-frontends="cbanking g2banking qbanking" to build aqbanking without that frontend.
configure: error: *** Requirements not fulfilled. Fix your requirements or change the configuration.

I don't know if I need any of these front ends at all, although I am sure I don't need the backend.  When I look at the gnucash documentation, it says 

"AqBanking has its own setup wizard for the purpose of setting up account identification and user login ID for your online connections."

(from: [http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2](http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2))

Does this set up use any or all of the front ends above?  I am using ubuntu edgy eft i386 distribution - so I am guessing I don't need the KDE front end, and probably not the QT3 front end.  I tried to apt-get gtk2, but was told it wasn't found.  When I looked at synaptic - there were many many packages.  I tried sudo apt-get install gtk2*, but that created an incompatable set of packages.

Should I even be worrying about this (and just use the suggested options to not include these front ends)?

Thanks,
Mike

---

### Post by dpm on 2006-11-23
> **sirmrmatt said:**
> Interesting.

I mean, I have been STRUGGLING, on principle alone, to get GnuCash working WITH ofx directconnect *enabled* (and I guess therefore HBCI enabled)!

After asking this question at the gnucash-user mailing list and getting this response: [http://permalink.gmane.org/gmane.comp.gnome.apps.gnucash.user/19076](http://permalink.gmane.org/gmane.comp.gnome.apps.gnucash.user/19076),

> --enable-hbci is really two things at once.  It means '--enable-aqbanking' and '--enable-hbci'...  Although there isn't an '--enable-aqbanking' per se.  But you need AqBanking for DirectConnect, which is why you need to --enable-hbci.

I've decided to correct this post with the correct information

1.- In GnuCash, OFX needs HBCI to be enabled in order to work. HBCI is disabled by default in the GnuCash Ubuntu package for licensing reasons.

2.- In order to do that, you can follow this guide ([http://wiki.gnucash.org/wiki/Debian](http://wiki.gnucash.org/wiki/Debian)) instructing you how to enable HBCI support (and thus indirectly OFX) in Debian by modifying and rebuilding the gnucash package. The guide also applies to Ubuntu.

3.- In any case, to get OFX to work even after it being enabled, you will need to install libofx and the libaq* (aqbanking libraries) from the repositories. Note, though, that the version of libofx in the edgy repositories is 0.8.0, and as stated here ([http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2)](http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2)), OFXDirectConnect only works with 0.8.2. A solution for this might be to use the Debian testing package (libofx3), which already includes v0.8.2, or to compile libofx yourself (I do not recommend it).

4.- Once that's done, you can follow this guide to configure OFX access to your bank account: [http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2](http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2).

Note: I do not use OFX myself, but I've been using HBCI using a similar approach to the guide I linked to in point 2 since GnuCash 1.9 without troubles. And IIRC, there are some people who compiled GnuCash packages for Edgy with HBCI support enabled in the forums and made them available. Search around.

Cheers.

---

### Post by michael.fries on 2006-11-23
But - there is not choice for ofx banking under tools.  Unless I recompile with the options --enable-hbci --enable-ofx, I don't see any way to actually use ofx.

Funny thing, in gnucash tools, after compiling, I only see hbci.

Although the aqbanking wizard apparently wasn't installed....apparently I needed the qbanking front end. 

I will try again....

---

### Post by sirmrmatt on 2006-11-24
The last reply you got regarding enabling ofx through apt-get may or may not be correct, I cannot verify except to say that I have seen in multiple places unanimous agreement that, like you noticed, you do not get OFX enabled by default in GnuCash. If there is a way to turn it on while still using repositories, great, but I could not figure it out.

To directly answer your question, I had the same problem with those program errors, and my answer was simply to paste the suggested options into the ./configure command:

./configure --with-backends="aqhbci aqdtaus aqofxconnect" --with-frontends="cbanking g2banking"

The commands I selected were the "lowest common demoninator" of the complaints you got from the system (for example, one complaint complains about kbanking, yet another includes it. Therefore, I removed it.)

Again, this worked for me. Didn't remember this step before!

Oh and yes, all you are going to see is HBCI. You use that option to get to the OFX stuff:

[http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2](http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2)

It's all in there, per the instructions.

I am now trying to figure out how to take the raw xml info I got from the info download script:

[http://www.jongsma.org/gc/](http://www.jongsma.org/gc/)

and put it into AqBanking so that it actually connects and gets my data...if anyone has any guidance on that, that would be much appreciated.

- Matt

---

### Post by svachalek on 2006-11-28
Forgive my utter noobiness here, but I am getting this message when I try to run the above configure command:

checking for gconf-2.0 >= "2.0"... Package gconf-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gconf-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gconf-2.0' found
configure: error: Library requirements (gconf-2.0 >= "2.0") not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.


In the package manager I can see I have "gconf2" installed which sounds like the same thing...?  Do I need something else or do I have to do something to my PKG_CONFIG_PATH?  I'm at a loss.

TIA,
Scott

---

### Post by balloons on 2006-12-08
I managed to get this far, trying this, and some variations:

Any ideas?

./configure --enable-hbci --enable-ofx --with-backends="aqhbci aqdtaus aqofxconnect" --with-frontends="cbanking g2banking"
make
make install

like:


./configure --enable-hbci --enable-ofx
make
make install

I can get to the HCBI setup wizard, but I get the following error. I'm guessing I don't have aqbanking setup right, but it's installed. I don't see an HCBI or OFX plugin for debian/ubuntu though.

> The external program " Setup Wizard" returned a nonzero exit code which means it has not been finished successfully. The further HBCI setup can only be finished if the  Setup Wizard is run successfully. Please try to start and successfully finish the  Setup Wizard program again.

---

### Post by theProf on 2007-02-23
guitara,

Did you ever obtain resolution for this?

---

