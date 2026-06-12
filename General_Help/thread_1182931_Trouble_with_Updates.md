---
title: "Trouble with Updates"
date: 2009-06-09
forum: General Help
---

### Post by Belgatom on 2009-06-09
I've recently switched to 9.04 from 8.04. Fresh install no upgrade. When I was on 8.04 I had updates on regularly (almost every other day) but since I've been on 9.04, updates have been much less frequent. 

Is this with everyone or is there something wrong with my system?

I did add some repositories to install some other programs. 

Also twice, I've had errors. The latest today when I get this as feedback. 

```
W: Failed to fetch http://be.archive.ubuntu.com/ubuntu/pool/main/f/foomatic-db-engine/foomatic-db-engine_4.0.0-0ubuntu6.1_i386.deb
  404 Not Found [IP: 195.238.1.6 80]


W: Failed to fetch http://be.archive.ubuntu.com/ubuntu/pool/main/s/sqlite3/libsqlite3-0_3.6.10-1ubuntu0.2_i386.deb
  404 Not Found [IP: 195.238.1.6 80]


W: Failed to fetch http://be.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.26.1-0ubuntu2_i386.deb
  404 Not Found [IP: 195.238.1.6 80]


W: Failed to fetch http://be.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.26.1-0ubuntu2_all.deb
  404 Not Found [IP: 195.238.1.6 80]


W: Failed to fetch http://be.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-plugins_2.26.1-0ubuntu2_i386.deb
  404 Not Found [IP: 195.238.1.6 80]


W: Failed to fetch http://be.archive.ubuntu.com/ubuntu/pool/main/m/metacity/metacity-common_2.25.144-0ubuntu2.1_all.deb
  404 Not Found [IP: 195.238.1.6 80]


W: Failed to fetch http://be.archive.ubuntu.com/ubuntu/pool/main/m/metacity/libmetacity0_2.25.144-0ubuntu2.1_i386.deb
  404 Not Found [IP: 195.238.1.6 80]


W: Failed to fetch http://be.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.1.30really5.0.75-0ubuntu10.2_all.deb
  404 Not Found [IP: 195.238.1.6 80]


W: Failed to fetch http://be.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.1.30really5.0.75-0ubuntu10.2_i386.deb
  404 Not Found [IP: 195.238.1.6 80]


W: Failed to fetch http://be.archive.ubuntu.com/ubuntu/pool/main/t/tracker/libtrackerclient0_0.6.93-0ubuntu3_i386.deb
  404 Not Found [IP: 195.238.1.6 80]


W: Failed to fetch http://be.archive.ubuntu.com/ubuntu/pool/main/m/metacity/metacity_2.25.144-0ubuntu2.1_i386.deb
  404 Not Found [IP: 195.238.1.6 80]


W: Failed to fetch http://be.archive.ubuntu.com/ubuntu/pool/main/s/sqlite3/sqlite3_3.6.10-1ubuntu0.2_i386.deb
  404 Not Found [IP: 195.238.1.6 80]


W: Failed to fetch http://be.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-documentation-en_2.26.1-0ubuntu2_all.deb
  404 Not Found [IP: 195.238.1.6 80]



```

I notice a "be" in the url. I live in Belgium, I guess the be stands for Belgium. Could it be something is wrong with the belgium servers?

---

### Post by Soul-Sing on 2009-06-09
You could try another server. Be stands for belgium.
404 are server errors. On the off. dutch/belgium ubuntu forum there are often be server errors reported....

---

### Post by michy99 on 2009-06-09
As to update frequency, 9.04 uses a different update philosophy. You are notified pf security updates whenever they are released, but you are only notified of other updates once a week. You can check for updates manually at any time with the Update Manager.

---

### Post by Belgatom on 2009-06-13
> **leoquant said:**
> You could try another server. Be stands for belgium.
404 are server errors. On the off. dutch/belgium ubuntu forum there are often be server errors reported....

Ok, how do I change the server in question? I suppose I adjust my repositories?

---

### Post by Soul-Sing on 2009-06-13
Software sources.: downloading from server: choose: server nl.

succes!

---

### Post by Belgatom on 2009-06-13
Succes it is! Thank you. Also for informing me about the different update philosophy.

---

