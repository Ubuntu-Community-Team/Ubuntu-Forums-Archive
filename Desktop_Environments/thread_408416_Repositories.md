---
title: "Repositories"
date: 2007-04-13
forum: Desktop Environments
---

### Post by Pengwyn44 on 2007-04-13
The sources.list supplied with the Dapper 6.06 CD appears to be out of date because I get "cannot connect to " errors. I have tried to match the syntax in the file with the actual URL's but to no avail. Can someone please supply me with the correct syntax?
Pengwyn44.(Or better still a copy of the correct sources.list file!)

---

### Post by taurus on 2007-04-13
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by az on 2007-04-13
> **Pengwyn44 said:**
> The sources.list supplied with the Dapper 6.06 CD appears to be out of date because I get "cannot connect to " errors. I have tried to match the syntax in the file with the actual URL's but to no avail. Can someone please supply me with the correct syntax?
Pengwyn44.(Or better still a copy of the correct sources.list file!)

I think the problem is that those repos are (were) temporarily down.  Those repos will not be out of date until support for Dapper is over (in another few years!)

---

### Post by Seisen on 2007-04-13
Or you can go to [http://www.ubuntuguide.org]("http://www.ubuntuguide.org") and use the repo list there.

---

### Post by Pengwyn44 on 2007-04-15
Thanks to everyone who responded to my Repositories query. With all that information
I shall be kept busy for a while!
Pengwyn44

---

### Post by ardchoille42 on 2007-04-15
I still use Dapper and here is my sources.list:

```

# This is the Ubuntu 6.06.1 LTS sources.list that is used by the package managers.

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse

deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

```

Those repos are up and working fine as of the time of this post.

---

