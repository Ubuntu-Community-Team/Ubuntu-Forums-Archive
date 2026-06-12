---
title: "ntpd returns a permission denied error"
date: 2007-08-09
forum: Desktop Environments
---

### Post by cccc on 2007-08-09
hi

I have feisty installed and get the following error:```

# tail -f /var/log/syslog
Aug 10 00:31:11 localhost ntpd_initres[5514]: ntpd returns a permission denied error!

```

knows someone howto solve this problem ?

---

### Post by un_dave on 2007-09-22
I can confirm i get the same error.

---

### Post by graigsmith on 2007-09-25
me too. whats wrong with this?

---

### Post by gmc on 2007-10-06
Hi Folks,

I've been seeing the same problem on a feisty install. Further investigation showed that the ntpd is being run twice, once as user ntp and once as user root. Since there are two copies running, the copy being run as root fails because it can't access port 123.

If you issue "ps auxwww | grep ntpd", you'll see both copies, (as root) killing the copy running as user root and these error messages stop.

I'm at a loss as to why two copies are being started, but it's definately a bug in Feisty. I don't see this problem on my Gutsy systtem though.

Gord

---

### Post by skillllllz on 2007-12-28
> **gmc said:**
> Hi Folks,

I've been seeing the same problem on a feisty install. Further investigation showed that the ntpd is being run twice, once as user ntp and once as user root. Since there are two copies running, the copy being run as root fails because it can't access port 123.

If you issue "ps auxwww | grep ntpd", you'll see both copies, (as root) killing the copy running as user root and these error messages stop.

I'm at a loss as to why two copies are being started, but it's definately a bug in Feisty. I don't see this problem on my Gutsy systtem though.

Gord

Anyone have any ideas on how to work around this issue? Is there a way to disable one of the copies from running?

---

