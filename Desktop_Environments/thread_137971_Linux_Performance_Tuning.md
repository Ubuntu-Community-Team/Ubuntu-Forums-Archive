---
title: "Linux Performance Tuning"
date: 2006-03-01
forum: Desktop Environments
---

### Post by mxc on 2006-03-01
Hi all,

We recently used breezy badger as the OS to try and improve the performance of a soon-to-be-retired application. Our application was experiencing poor performance on a dual xeon 1,8GHZ box with 2 gigs of ram. The box was originally running fedora core 4.0. The application was written in PHP and used the postgres 8.0 database.

We tested the app on  single processor, 3.8 GHZ Xeon processor with 4 gig of ram and it performed adequatly , although slowly. We re-installed the dual box with breezy and placed the application back on the box. We also increased ram to 4 gigs. We upgraded to postgres 8.1 as well. The client still reports poor performance.  The application has about 60 concurrent users and during a day the apache web server gets about 25 000 hits

It was suggested that the application performs poorly because postgres uses one process per query and therefore performs better on a single processor box. I know Postgress uses one process per connection but surely mutliple connections should connect to different CPUS?

Does Breexy Badger come with PAE enabled to address more thatn 3 gigs of ram?

Are there any other performance tips for setting up Breezy on a multi processor machine?

---

### Post by Jason_25 on 2006-03-01
What kernel version were you using?

---

### Post by mxc on 2006-03-01
2.6.12-9-386

---

### Post by Perfect Storm on 2006-03-01
You might wanna try i686-smp to support over 1 gb ram and for dual processor.

```
sudo apt-get install linux-686-smp
```

---

### Post by JayTee on 2006-09-14
"You might wanna try i686-smp to support over 1 gb ram and for dual processor."

"sudo apt-get install linux-686-smp"




Will this be a benefit to me running on a Pentium D 940 dual core?
:confused:

---

### Post by Perfect Storm on 2006-09-14
Aye.

---

### Post by JayTee on 2006-09-14
Cool! I'll give that a try tonight. Thanks for the quick response.

JayTee
"Carpe Argentum Et Fugio"
*Take the money and run*

---

