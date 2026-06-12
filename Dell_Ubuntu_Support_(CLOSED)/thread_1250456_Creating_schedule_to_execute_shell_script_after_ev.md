---
title: "Creating schedule to execute shell script after every 1 minute"
date: 2009-08-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Vinod_hire on 2009-08-26
Hi am vinod,
i want to create new file after every minute in linux, i am using anacron.
but not works , pls suggest me the right way.
how to create scheduled task which execute efter every 1 minute
Thanks in advance

---

### Post by jhair.tocancipa on 2009-08-26
> **Vinod_hire said:**
> Hi am vinod,
i want to create new file after every minute in linux, i am using anacron.
but not works , pls suggest me the right way.
how to create scheduled task which execute efter every 1 minute
Thanks in advance

sudo crontab -e

Then  type,

* * * * * yourscript

and save.

HTH

---

