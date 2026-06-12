---
title: "Bibus upgrade loses most references!"
date: 2008-07-25
forum: Education &amp; Science
---

### Post by digisus on 2008-07-25
Hi!

I upgraded from Gutsy/Bibus 1.4.0rc2 (manual deb package installation, much manual tweaking) to Hardy/1.4.3-2 (installed via repos).

The problem is that if I copy my DB file into the .bibus folder and open bibus, it will only show 30 from a total of ~160 references.

Nautilus shows the old db file to be "SQLite3 database", whereas the new bibus version has produced an empty DB file as "SQLite2 database" during installation.

Why does Bibus 1.4.3 not understand the SQLite3 file when the older Bibus did?

What should I do to be able to use my full set of references in the new Bibus version?

Thank you very much!

---

### Post by machoo02 on 2008-07-25
Do you have python-pysqlite2 (the Python interface to SQLite3) installed?

---

