---
title: "So I want to put gnucash on my Mini 9. How do I do that?"
date: 2008-11-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gavinfoxx on 2008-11-19
I am in an accounting class, and I wanted to show my accounting teacher GnuCash, but I get this error in synaptic package manager:

gnucash:
 Depends: guile-1.6-slib  but it is not installable
 Depends: libcrypt-ssleay-perl  but it is not installable
 Depends: libdate-manip-perl  but it is not installable
 Depends: libfinance-quote-perl  but it is not installable
 Depends: libgoffice-0-4 (>=0.4.2) but it is not installable
 Depends: libgtkhtml3.8-15 (>=1:3.13.5) but it is not installable
 Depends: libktoblzcheck1c2a but it is not going to be installed
 Depends: libofx4  but it is not installable
 Depends: libosp5 (>=1.5.2-1) but it is not installable
 Depends: psfontmgr  but it is not installable
 Depends: slib (>=3a2-5) but it is not installable


I presume this is because i am on lpia.  How do I manage to install these libraries to get gnucash working? Thanks!

---

### Post by yakker.yak on 2008-11-19
GNUCash and its dependencies are in the standard repositories so it should install like everything else via Synaptic.

Did you by any chance break your package manager (and system) trying to upgrade Gdebi?

If yes, please see the fix [here]("http://ubuntuforums.org/showthread.php?t=982260").

---

### Post by notwen on 2008-11-19
I'm willing to bet it's due to the i386 and lpia architecture compatibility issues since the Mini 9s shipped w/ the lpia kernel in Dell's custom Ubuntu install for the Mini 9s.  Not sure this is the cause though.  Seems like I recall a post explaining how to convert i386 packages over to lpia in one of the numerous Mini 9 threads. =|

---

### Post by gavinfoxx on 2008-11-19
Yea, I did break the package manager... uhm, I cant seem to do the list, cause gdebi does not come up when I search for it.  I asked for some help in another thread, but no one replied...

---

