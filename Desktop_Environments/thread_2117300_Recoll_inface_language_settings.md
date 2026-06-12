---
title: "Recoll inface language settings"
date: 2013-02-18
forum: Desktop Environments
---

### Post by be4truth on 2013-02-18
I installed Recoll 1.17.3 + Xapian 1.2.12 on a Spanish laptop with and English Ubuntu 12.10 but it uses Spanish as the interface language. I can't find the configuration file where to change this backto English?
I am using XFCE 4.1

Any help appreciated :)

---

### Post by medoc on 2013-02-18
There is no explicit interface to change the recoll interface language, it is determined from the NLS environment. I can think of two ways to revert the language to english:

 - Launch the command with a different environment, like in:
  LC_ALL=C recoll

 - Just rename the directory which holds the translation files: 
  sudo mv /usr/local/share/recoll/translations /usr/local/share/recoll/translations-

Cheers,

jf

---

### Post by medoc on 2013-02-18
OOps, for a standard Recoll installation there should be no "local" in the paths above.

---

### Post by be4truth on 2013-02-18
Thanks!!

I removed the file recoll_es.qm from /usr/share/recoll/translations and now it launches with an English interface.

:)

---

