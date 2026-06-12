---
title: "Can't installl Firebird on Ubuntu 8.10"
date: 2009-02-04
forum: General Help
---

### Post by thesilverline on 2009-02-04
I'm trying to install firebird2.1 froom synaptics PM on ubuntu 8.10. But I get this error: 
```

The following extra packages will be installed:
  firebird2.1-common firebird2.1-server-common libfbclient2
Suggested packages:
  firebird2.1-doc
The following NEW packages will be installed:
  firebird2.1-common firebird2.1-server-common firebird2.1-super libfbclient2
0 upgraded, 4 newly installed, 0 to remove and 235 not upgraded.
Need to get 0B/5820kB of archives.
After this operation, 14.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package firebird2.1-common.
(Reading database ... 116356 files and directories currently installed.)
Unpacking firebird2.1-common (from .../firebird2.1-common_2.1.0.17798-0.ds2-1_i386.deb) ...
Selecting previously deselected package firebird2.1-server-common.
Unpacking firebird2.1-server-common (from .../firebird2.1-server-common_2.1.0.17798-0.ds2-1_i386.deb) ...
Selecting previously deselected package libfbclient2.
Unpacking libfbclient2 (from .../libfbclient2_2.1.0.17798-0.ds2-1_i386.deb) ...
Selecting previously deselected package firebird2.1-super.
Unpacking firebird2.1-super (from .../firebird2.1-super_2.1.0.17798-0.ds2-1_i386.deb) ...
Processing triggers for man-db ...
Setting up firebird2.1-common (2.1.0.17798-0.ds2-1) ...
Setting up firebird2.1-server-common (2.1.0.17798-0.ds2-1) ...
dpkg: error processing firebird2.1-server-common (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libfbclient2 (2.1.0.17798-0.ds2-1) ...

dpkg: dependency problems prevent configuration of firebird2.1-super:
 firebird2.1-super depends on firebird2.1-server-common (= 2.1.0.17798-0.ds2-1); however:
  Package firebird2.1-server-common is not configured yet.
dpkg: error processing firebird2.1-super (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          ldconfig deferred processing now taking place
Errors were encountered while processing:
 firebird2.1-server-common
 firebird2.1-super
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Any suggestion is welcome .

---

### Post by Partyboi2 on 2009-02-05
Open a terminal (Applications>Accessories>Terminal) and try
```
sudo apt-get -f install
sudo dpkg --configure -a
```

---

### Post by thesilverline on 2009-02-05
WEll it's fine now. I ran 
dpkg-reconfigure --all 
which resolved all dependecies messes and then i reinstalled.
Thanks to all though.

---

