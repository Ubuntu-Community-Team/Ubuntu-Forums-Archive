---
title: "Help, Error when apt-get install libmime-perl"
date: 2007-10-29
forum: Desktop Environments
---

### Post by PTrack88 on 2007-10-29
I am trying to set up a HelpDesk software that I am moving to a linux box. (Running Ubuntu Server 7.10)
The helpdesk software is called perldesk and I previously had it configured on a windows machine.

I am currently having a problem trying to install libmime-perl package using
```
sudo apt-get install libmime-perl
```

I have run the apt-get update and upgrade as well but each time the package fails with the following output

```
patrick@gsnt-linux:~$ sudo apt-get install libmime-perl
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libmime-perl: Depends: libio-stringy-perl (>= 1.211) but it is not installable
E: Broken packages
patrick@gsnt-linux:~$

```

Any help would be appreciated. Sorry if this is a repost but I did not find an answer to this in the forum already.

Thanks,
-Patrick

---

### Post by haldean on 2007-10-30
can you post the output of 
```
apt-cache show libio-stringy-perl
```and
```
apt-cache show libmime-perl
```?

---

### Post by PTrack88 on 2007-10-31
patrick@gsnt-linux:~$ apt-cache show libio-stringy-perl
patrick@gsnt-linux:~$ apt-cache show libio-stringy-perl -v
patrick@gsnt-linux:~$ sudo apt-cache show libio-stringy-perl
[sudo] password for patrick:
patrick@gsnt-linux:~$ apt-cache show libmime-perl
Package: libmime-perl
Priority: optional
Section: universe/perl
Installed-Size: 684
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Original-Maintainer: Debian Perl Group <pkg-perl-maintainers@lists.alioth.debian.org>
Architecture: all
Source: mime-tools
Version: 5.420-1
Depends: perl (>= 5.8.4-2.3), libmailtools-perl (>= 1.11), libio-stringy-perl (>= 1.211), libconvert-binhex-perl
Filename: pool/universe/m/mime-tools/libmime-perl_5.420-1_all.deb
Size: 269326
MD5sum: 78b865c89d266fe11229b4d591ee58bf
SHA1: 7207a0bc1d2d68a1f1a0d86bd6e4a80369581dec
SHA256: c468c115964b70b1442ebf00d9ab3aecdf3d2e5920b851ef4f794c64395ba1e1
Description: Perl5 modules for MIME-compliant messages (MIME-tools)
 The libmime-perl package provide the MIME-tools modules. MIME-tools is a
 collection of Perl5 MIME:: modules for parsing, decoding, and generating
 single- or multipart (even nested multipart) MIME messages.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by haldean on 2007-10-31
what version of ubuntu are you using?
does anything show up when you run
```
apt-cache search libio stringy
```?

---

### Post by PTrack88 on 2007-11-02
As stated in the first post, I am currently running Ubuntu Server 7.10 (Gutsy Gibbons)

There is no displayed result for ```
> apt-cache search libio stringy
```

---

### Post by haldean on 2007-11-02
Hmmm... try downloading [this](http://http.us.debian.org/debian/pool/main/i/io-stringy/libio-stringy-perl_2.110-2_all.deb), install it, and then try apt-getting libmime-perl.

---

