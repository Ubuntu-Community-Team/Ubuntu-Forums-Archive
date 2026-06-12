---
title: "remove broken package that wont configure"
date: 2009-03-02
forum: General Help
---

### Post by igknighted on 2009-03-02
So, I was wondering if they had fixed the new koffice packages in Kubuntu, but as I have found out they have not.  Now, apt is broken and wont finish the install, or install/update anything else.

I tried dpkg --configure -a, sudo apt-get -f install, apt-get clean, attempting to remove the offending packages, and anything else I could think of (but can't recall now).  Anyone know how to clear this mess up and get apt working again?

---

### Post by bodhi.zazen on 2009-03-02
Hey igknighted, good to see you ;)

Would you post the exact error message you are getting please ? I am hoping the error message will give us a clue.

---

### Post by igknighted on 2009-03-02
```
fitz@lappy:~$ sudo apt-get -f install
[sudo] password for fitz:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  mysql-server libpoppler-qt2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  koffice-data-kde4
Suggested packages:
  koffice-doc-html-kde4
The following NEW packages will be installed:
  koffice-data-kde4
0 upgraded, 1 newly installed, 0 to remove and 137 not upgraded.
9 not fully installed or removed.
Need to get 0B/1371kB of archives.
After this operation, 4776kB of additional disk space will be used.
Do you want to continue [Y/n]?
(Reading database ... 111132 files and directories currently installed.)
Unpacking koffice-data-kde4 (from .../koffice-data-kde4_1%3a1.9.98.5-0ubuntu1~intrepid1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/koffice-data-kde4_1%3a1.9.98.5-0ubuntu1~intrepid1_all.deb (--unpack):
 trying to overwrite `/usr/share/icons/oxygen/16x16/actions/object-order-back.png', which is also in package kde-icons-oxygen
Errors were encountered while processing:
 /var/cache/apt/archives/koffice-data-kde4_1%3a1.9.98.5-0ubuntu1~intrepid1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
fitz@lappy:~$

```

EDIT: Nice to see you again bodhi

---

### Post by bodhi.zazen on 2009-03-02
Try :

```
sudo dpkg --install --force-overwrite /var/cache/apt/archives/koffice-data-kde4_1%3a1.9.98.5-0ubuntu1~intrepid1_all.deb
```

Then if that works, consider updating your system ;)

---

### Post by igknighted on 2009-03-02
Aha!  Thanks so much

---

### Post by bodhi.zazen on 2009-03-02
You are most welcome ;)

---

