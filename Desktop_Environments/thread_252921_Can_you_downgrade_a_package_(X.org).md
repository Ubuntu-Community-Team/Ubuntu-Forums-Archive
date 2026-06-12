---
title: "Can you downgrade a package (X.org)?"
date: 2006-09-07
forum: Desktop Environments
---

### Post by zooounds on 2006-09-07
How do I replace X.org 10.4 with 10.3 or maybe 10.2 (as the 10.3 seems to have some problem in it).

Where can I find the package?

Regards
Fredrik

---

### Post by croak77 on 2006-09-07
First, xorg is only up to 7.1 (7.0 on dapper). So I don't know where you are getting 10.4, 10.3 from.

---

### Post by zooounds on 2006-09-07
Sorry, the package i was refering to is xserver-xorg-core, which in mys system has a version ending with 10.4

---

### Post by croak77 on 2006-09-07
Are you talking about 1:1.0.2-0ubuntu10? That's the dapper version.

---

### Post by zooounds on 2006-09-07
My Dapper want to install 1:1.0.2-0ubuntu10.4

I have downgraded it now and locked the version of the package. And this fare my TV-out works fine... After some more testing I will know for sure.

---

### Post by cstudent on 2006-09-07
To see available versions by way of the terminal:
```

apt-cache policy xserver-xorg-core

```

This is what it reveals for me:
```

kirby@desktop:~$ apt-cache policy xserver-xorg-core
xserver-xorg-core:
  Installed: 1:1.0.2-0ubuntu10.4
  Candidate: 1:1.0.2-0ubuntu10.4
  Version table:
 *** 1:1.0.2-0ubuntu10.4 0
        500 http://archive.ubuntu.com dapper-updates/main Packages
        100 /var/lib/dpkg/status
     1:1.0.2-0ubuntu10 0
        500 http://archive.ubuntu.com dapper/main Packages

```

To downgrade my version 10.4 to 10:
```

sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

```

You can also do it via Synaptic by searching for the xserver-xorg-core package. Then under the package menu in the menu bar select force version and chose the version you want.

---

