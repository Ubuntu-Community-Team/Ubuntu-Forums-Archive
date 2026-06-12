---
title: "(Broken Pipe) error code (1)  Help"
date: 2005-12-13
forum: Desktop Environments
---

### Post by interse on 2005-12-13
I am trying to reinstall Gnucash which was 'broken' after I download a number of upgrades.  Here is the output of "apt-get -f install gnucash":

Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gnucash-common libofx2
Suggested packages:
  gnucash-sql gnucash-docs
The following NEW packages will be installed:
  gnucash gnucash-common libofx2
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4649kB of archives.
After unpacking 20.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 80117 files and directories currently installed.)
Unpacking libofx2 (from .../libofx2_1%3a0.8.0-3ubuntu8_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb (--unpack):
 trying to overwrite `/usr/share/libofx/dtd/opensp.dcl', which is also in package libofx0c102
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package gnucash-common.
Unpacking gnucash-common (from .../gnucash-common_1.8.10-18_all.deb) ...
Selecting previously deselected package gnucash.
Unpacking gnucash (from .../gnucash_1.8.10-18_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


WHAT ARE MY NEXT STEPS, IF ANY?  I am new to terminal commands, BUT would like to learn to meaningfully read the above output AND know how to proceed.

Thank you in advance

---

### Post by interse on 2005-12-13
Information on how to deal with the above situation would be appreciated.  It happened to me in Hoary 5.04, but I was able to deal with the situation by using 'Smart Install' (?) which I cannot seem to find in Breezy.  Is it missing from Breezy or am I looking in the wrong place?  

As it stands currently, GnuCash cannot be installed.

---

