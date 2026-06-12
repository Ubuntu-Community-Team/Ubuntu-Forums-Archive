---
title: "wget and ssl"
date: 2006-02-22
forum: Desktop Environments
---

### Post by Minilek on 2006-02-22
I apt-get install openssl then wget, yet my wget doesn't have ssl support.  I can't wget from https url's, and some ssl-support-only command-line options don't work (e.g. --no-check-certificate).  Anyone encounter this?

---

### Post by Minilek on 2006-02-22
Got it working by downloading the source and ./configure'ng with --with-ssl.  Not sure why it didn't work when I used apt...

---

