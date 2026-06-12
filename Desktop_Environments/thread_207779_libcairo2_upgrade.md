---
title: "libcairo2 upgrade?"
date: 2006-07-02
forum: Desktop Environments
---

### Post by Sean-Michael on 2006-07-02
Man I keep getting this messge when I run my Update Manager...

```
Cannot install all available updates

Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.

The following updates will be skipped:
libcairo2

```

So when I run sudo apt-get dist-upgrade I get this...

```
sean-michael@nitro:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  libcairo2
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

When I run Synaptic Package Manager to try to update I get more problems, meaning I dont understand what to do....  

Thankyou in advance for any help!

---

### Post by art on 2006-07-02
All I can say is that this package is in xgl repos, and it depend on a higher version of libfreetype, which is not there, hence the upgrade is impossible. Hopefully they will put the dependencies there soon.

---

### Post by marwal on 2006-07-02
Depends on: libfreetype6 (>=2.2.1) but 2.1.10-1ubuntu2-turnerpatch0 will be installed.

My libfreetype6 is version 2.1.10
So the dependency from cairo2 which needs libfreetype version 2.2.1 will not install.

You could force it but I would wait.

---

### Post by Sean-Michael on 2006-07-02
Ok' then I guess I ignore this messge till things change, I was worried being new to linux that there was something simple I was missing, I just started getting the message after adding a new new drive to my tower, that it had something to do with that, after all grub had a cow over the new drive lol

Thankyou for your help art.

---

### Post by Sean-Michael on 2006-07-02
Yea, thankyou also marwal, I will wait, my experience is limited at best, if something went wrong I would be lost.  I will wait'

---

### Post by kpkeerthi on 2006-07-02
Same problem here after the recent compiz update. I have posted the issue in the compiz forums.
[http://www.compiz.net/viewtopic.php?id=389&p=13](http://www.compiz.net/viewtopic.php?id=389&p=13)

---

### Post by shoagun on 2006-08-16
It's been over a month and this problem hasn't been fixed.  libfreetype6 2.2.1 is still not available thus libcairo2 still cannot be upgraded.  Is there something I missed?

---

### Post by d.h. on 2006-08-16
> **shoagun said:**
> It's been over a month and this problem hasn't been fixed.  libfreetype6 2.2.1 is still not available thus libcairo2 still cannot be upgraded.  Is there something I missed?

I think this problem was fixed back then and kind of reappeared today. :cry:

---

### Post by stryderjzw on 2006-08-16
Yup, this problem is back for me today...

---

### Post by Anduu on 2006-08-16
[http://www.compiz.net/topic-3099-ubuntu-dapper-libcairo2-errors](http://www.compiz.net/topic-3099-ubuntu-dapper-libcairo2-errors)

---

### Post by d.h. on 2006-08-17
Well, it is already fixed. Pretty fast this time. :-)

---

