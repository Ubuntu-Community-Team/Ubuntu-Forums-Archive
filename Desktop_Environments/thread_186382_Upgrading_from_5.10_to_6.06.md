---
title: "Upgrading from 5.10 to 6.06"
date: 2006-06-01
forum: Desktop Environments
---

### Post by Magiczero on 2006-06-01
Hello  

What do I need to enter into the terminal to upgrade from 5.10 to 6.06?  Will I lose my data if I upgrade hat way?
Thank You

---

### Post by TheHighChild on 2006-06-01
Personally, I had a poor experience with dist-upgrade and it would not locate any of my video, keyboard, or mouse drivers. Thus meaning x would not start and leaving me without a graphical desktop.

Hopefully it's working for other folks.

---

### Post by Magiczero on 2006-06-01
how do i run dist upgrade?

---

### Post by aysiu on 2006-06-01
[http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

---

### Post by Magiczero on 2006-06-02
This is not how you do it!  It doesnt work!  explain how I do it?

---

### Post by Irony on 2006-06-02
[https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)

The simplest method is to do it via update manager as explained in the above link.

---

### Post by Magiczero on 2006-06-02
I ran the upgrade through update maniger and I got this error:  Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found
What does this mean?  How can I fix it?
Thank You!

---

### Post by aysiu on 2006-06-02
It means your sources.list contains dead repositories like [http://koti.mbnet.fi/](http://koti.mbnet.fi/)

Get a fresh list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

