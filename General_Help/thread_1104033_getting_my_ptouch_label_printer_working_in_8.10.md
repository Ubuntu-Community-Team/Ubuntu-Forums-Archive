---
title: "getting my ptouch label printer working in 8.10"
date: 2009-03-23
forum: General Help
---

### Post by bilmas on 2009-03-23
i went to this site to get the driver: [http://www.diku.dk/hjemmesider/ansatte/panic/P-touch/](http://www.diku.dk/hjemmesider/ansatte/panic/P-touch/) and i downloaded the tar.gz file

i am unsure of how to install the driver from the tar.gz but beyond that i'd be lost, too

has anybody had any success getting this to work on ubuntu 8.10?

---

### Post by cariboo on 2009-03-23
From the web page:
> To install the tar file distribution, run

 > tar zxf ptouch-driver-*.tar.gz
 > cd ptouch-driver-*
 > ./configure
 > make
 > make install


After you have installed the driver, go to System-->Administration-->Printing and add a new printer, just follow the prompts.

Jim

---

### Post by bilmas on 2009-03-25
i saw that site but i am not sure how to follow those instructions

---

