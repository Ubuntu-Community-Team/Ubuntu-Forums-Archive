---
title: "Updating GrADS: convert from RH or compile from source?"
date: 2009-04-28
forum: General Help
---

### Post by TideMan on 2009-04-28
I have an old version of GrADS (Grid Analysis and Display System) installed and working, but I'd like to upgrade to a new version from this site:
[http://www.iges.org/grads/downloads.html]("http://www.iges.org/grads/downloads.html")

They give several choices of Red Hat Linux and the source.
I understand I can transform RH into .deb and thence into Ubuntu.
Is this a good strategy?  If so which version of RH should I use: RH7.1, RH9 or RHE3?
Alternatively, I could download the source and compile.
Which is the preferred strategy?

Any advice appreciated.

---

### Post by Klipstraat on 2009-05-04
Hi - I am also trying to install GrADS on Kubuntu Jaunty - There is a package available from [ftp://iges.org/grads/2.0/grads-bin-2.0.a5-ubuntu-x86_64.tar.gz](ftp://iges.org/grads/2.0/grads-bin-2.0.a5-ubuntu-x86_64.tar.gz).

Unfortunately the documentation is rather sparse and the instuctions although straightforward do not give a workable GrADS - the files are there in /usr/local/bin but the execs do not work. 

I have tried various tricks to make the executables run but no luck yet..

(I have also tried to compile from the source code - ./config works fine but make does not work - still trying to figure out why.. )

Any one else have any insight on this?

---

### Post by TideMan on 2009-06-03
A new version of GrADS 2.0.a6 has just been issued and it contains a version that works on my Ubuntu Hardy:
[http://iges.org/grads/downloads.html](http://iges.org/grads/downloads.html)
Choose the i686 version and unzip, then extract the programs in /bin to /usr/local/sbin

Note: gradsdap has replaced gradsdods and there might be other changes as well.

---

