---
title: "Apt-Get repo for sama-3.0.20 or 20a?"
date: 2005-10-16
forum: Desktop Environments
---

### Post by SlowJet on 2005-10-16
Hi, :)

 I have not used apt-get or Debian format and I would like to get samba-3.0.20a
(because it works much better and has about 300 bug fixes over 14a. :)
I have used every version of 3.020 from b1,b2,b,rc1,rc2 and the final on rpm based systems so it's not like it is a spooky experiment.
I just need to know where to get it in the form that Ubuntu will install?
The samba site doesn't have Debian packaging yet.

Thank you,

SJ


What I tried according to posts I found. =============

root@Celcila-24:/home/darwinhwebb/Desktop# rpm -Uvh samba-common-3.0.20b-1.i386.rpm samba-3.0.20b-1.i386.rpm samba-client-3.0.20b-1.i386.rpm samba-swat-3.0.20b-1.i386.rpm
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
error: cannot open Packages database in /var/lib/rpm
root@Celcila-24:/home/darwinhwebb/Desktop# alien --help
-su: alien: command not found
root@Celcila-24:/home/darwinhwebb/Desktop# cd /
root@Celcila-24:/# alien
-su: alien: command not found
root@Celcila-24:/# sudo man fakerroot
No manual entry for fakerroot
root@Celcila-24:/# man checkinstall
No manual entry for checkinstall
root@Celcila-24:/# sudo apt-get install alien
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  debconf-utils debhelper gettext html2text intltool-debian po-debconf
Suggested packages:
  lsb-rpm lintian dh-make cvs gettext-doc
Recommended packages:
  curl libmail-sendmail-perl libcompress-zlib-perl
The following NEW packages will be installed:
  alien debconf-utils debhelper gettext html2text intltool-debian po-debconf
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2484kB of archives.
After unpacking 7610kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
Selecting previously deselected package html2text.
(Reading database ... 73944 files and directories currently installed.)
Unpacking html2text (from .../html2text_1.3.2a-2build1_i386.deb) ...
Selecting previously deselected package debconf-utils.
Unpacking debconf-utils (from .../debconf-utils_1.4.56ubuntu2_all.deb) ...
Selecting previously deselected package gettext.
Unpacking gettext (from .../gettext_0.14.5-2ubuntu2_i386.deb) ...
Selecting previously deselected package intltool-debian.
Unpacking intltool-debian (from .../intltool-debian_0.30+20040213_all.deb) ...
Selecting previously deselected package po-debconf.
Unpacking po-debconf (from .../po-debconf_0.8.23_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_4.9.5ubuntu1_all.deb) ...
Selecting previously deselected package alien.
Unpacking alien (from .../archives/alien_8.53_all.deb) ...
Setting up html2text (1.3.2a-2build1) ...

Setting up debconf-utils (1.4.56ubuntu2) ...

Setting up gettext (0.14.5-2ubuntu2) ...

Setting up intltool-debian (0.30+20040213) ...
Setting up po-debconf (0.8.23) ...
Setting up debhelper (4.9.5ubuntu1) ...
Setting up alien (8.53) ...
root@Celcila-24:/# cd /home/darwinhwebb/Desktop root@Celcila-24:/home/darwinhwebb/Desktop# dir
NVIDIA-Linux-x86-1.0-7676-pkg1.run  samba-common-3.0.20b-1.i386.rpm
samba-3.0.20b-1.i386.rpm            samba-swat-3.0.20b-1.i386.rpm
samba-client-3.0.20b-1.i386.rpm
root@Celcila-24:/home/darwinhwebb/Desktop# sudo alien samba-common-3.0.20b-1.i386.rpm samba-3.0.20b-1.i386.rpm samba-swat-3.0.20b-1.i386.rpm samba-client-3.0.20b-1.i386.rpm -d
samba-common_3.0.20b-2_i386.deb generated
samba_3.0.20b-2_i386.deb generated
samba-swat_3.0.20b-2_i386.deb generated
samba-client_3.0.20b-2_i386.deb generated
root@Celcila-24:/home/darwinhwebb/Desktop# sudo dpkg -i samba-common_3.0.20b-2_i386.deb samba_3.0.20b-2_i386.deb samba-swat_3.0.20b-2_i386.deb samba-client_3.0.20b-2_i386.deb
(Reading database ... 74467 files and directories currently installed.)
Preparing to replace samba-common 3.0.14a-6ubuntu1 (using samba-common_3.0.20b-2_i386.deb) ...
Unpacking replacement samba-common ...
dpkg: error processing samba-common_3.0.20b-2_i386.deb (--install):
 trying to overwrite `/usr/share/man/man1/smbcquotas.1.gz', which is also in package smbclient
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace samba 3.0.14a-6ubuntu1 (using samba_3.0.20b-2_i386.deb) ... * Stopping Samba daemons...                                             [ ok ]
Unpacking replacement samba ...
dpkg: error processing samba_3.0.20b-2_i386.deb (--install):
 trying to overwrite `/usr/share/man/man7/samba.7.gz', which is also in package samba-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package samba-swat.
Unpacking samba-swat (from samba-swat_3.0.20b-2_i386.deb) ...
Selecting previously deselected package samba-client.
Unpacking samba-client (from samba-client_3.0.20b-2_i386.deb) ...
dpkg: error processing samba-client_3.0.20b-2_i386.deb (--install):
 trying to overwrite `/usr/share/man/man1/nmblookup.1.gz', which is also in package samba-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Setting up samba-swat (3.0.20b-2) ...
Errors were encountered while processing:
 samba-common_3.0.20b-2_i386.deb
 samba_3.0.20b-2_i386.deb
 samba-client_3.0.20b-2_i386.deb

One at a time=========nope

root@Celcila-24:/home/darwinhwebb/Desktop# sudo dpkg -i samba-common_3.0.20b-2_i386.deb (Reading database ... 74935 files and directories currently installed.)
Preparing to replace samba-common 3.0.14a-6ubuntu1 (using samba-common_3.0.20b-2_i386.deb) ...
Unpacking replacement samba-common ...
dpkg: error processing samba-common_3.0.20b-2_i386.deb (--install):
 trying to overwrite `/usr/share/man/man1/smbcquotas.1.gz', which is also in package smbclient
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 samba-common_3.0.20b-2_i386.deb

Later --force-conflicts ====nope

?????????????????

---

### Post by SlowJet on 2005-10-19
An update======

  Did an svn on samba-3.0.21RC1
followed the samba guide for configure, make, make install

It all worked after installing a few packages.

But it would not start up.

The fine print on the samba binanarys site say that samba will not work on anything pass woody (which I assume is version 3.0.14a).

If this is true it must be fixed or Unbuntu is not very usable.

IMO, things like samba and the browser and the mail should be updated and ready a few days after production release. An experienced coderer-configurer would only need a few hours to get it going. There is no excuse, only wrong priorties.

SJ

---

### Post by thekurst on 2005-10-24
SlowJet, I fully agree with you, I need samba 3.0.20 to fix a bug with browsing with OS X Tiger and I can't believe that an updated Ubuntu package has not been released as I need t badly.

Seeing as you had little success with you installation I won't even try compiling from source (as I have very little experience with that).

Ubuntu developers please release a samba update to the latest stable version 3.0.20b

---

### Post by yjsoon on 2005-11-11
Any word on the availability of samba 3.0.20 to fix the Breezy/Tiger Samba unconnectability? I tried looking around the forums, but to no avail.

---

### Post by thekurst on 2005-11-11
yjsoon: I'm having the same issue, but although you can't browse using the finder to your samba share you can use command + K or "Connect to server" in the Go menu and manually connect using "smb://127.0.0.1/share" where 127.0.0.1 is the IP address of your Breezy box and "share" is the name of your samba share.

There has been a bug posted in bugzilla (Bug # 17509) about this but no one seems to really care, if we could somehow get this issue escalated that would be great.

---

### Post by yjsoon on 2005-11-11
Actually, I hadn't tried that. It works fine that way, thanks for the info!

---

