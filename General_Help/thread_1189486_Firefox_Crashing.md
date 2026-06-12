---
title: "Firefox Crashing"
date: 2009-06-16
forum: General Help
---

### Post by dillzz on 2009-06-16
Specs:
Kubuntu 9.04 x86_64

Firefox started crashing when opening files, eg: pdf, torrent, etc.  will open file fine then crash firefox and spittings errors to .xsession-errors

Could not open library /usr/bin/firefox: Cannot load library /usr/lib/libkdeinit4_firefox.so: (/usr/lib/libkdeinit4_firefox.so: cannot open shared object file: No such file or directory)


ll /usr/lib/libkdeinit4_firefox.so
ls: cannot access /usr/lib/libkdeinit4_firefox.so: No such file or directory

Any ideas?  Please help!

---

### Post by dillzz on 2009-06-16
Also note that when firefox crashes after opening attachment it asks if I want to start new or restore session.  If I choose restore it complains a bout /tmp/randomfileattachment and not having permissions to change it.  However the permissions on /tmp are correct.  

ll -d /tmp
drwxrwxrwt 15 root root 4096 2009-06-16 21:44 /tmp

---

