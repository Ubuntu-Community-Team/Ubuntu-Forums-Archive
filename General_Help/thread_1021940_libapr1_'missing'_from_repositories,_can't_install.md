---
title: "libapr1 'missing' from repositories, can't install apache"
date: 2008-12-26
forum: General Help
---

### Post by stefangr1 on 2008-12-26
I want to install apache2 server and g++ on an old laptop (i386), but it fails with an error that says it can't find libapr1 version 8.1. That version is indeed missing from (all) servers, even tough version 8.2 appears to be there (but it won't use that).

Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/pool/main/a/apr/libapr1_1.2.7-8.1_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/a/apr/libapr1_1.2.7-8.1_i386.deb)  404 Not Found

Any tips on how to procees are higly regarded!

Stefan

---

### Post by dcstar on 2008-12-26
> **stefangr1 said:**
> I want to install apache2 server and g++ on an old laptop (i386), but it fails with an error that says it can't find libapr1 version 8.1. That version is indeed missing from (all) servers, even tough version 8.2 appears to be there (but it won't use that).
........

Exactly how are you trying to install this?

---

### Post by stefangr1 on 2008-12-26
I tried with both the synaptic package manager and from the command line with apt-get install.

I have managed to get it working in the mean time, by changing everything to the gutsy repositories in my sources.list, I'm not sure however if that's a good practice.

---

