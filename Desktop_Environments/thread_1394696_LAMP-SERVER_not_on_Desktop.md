---
title: "LAMP-SERVER not on Desktop?"
date: 2010-01-30
forum: Desktop Environments
---

### Post by Bartly on 2010-01-30
Just installed 9.10. Wanted to instal LAMP but sudo apt-get install lamp-server^ returned 
barry@barry-laptop:~$ sudo apt-get install lamp-server^
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
E: Couldn't find task lamp-server

Also use used this:
barry@barry-laptop:~$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package apache2

Is something wrong or does the desktop distro not come with these packages? I read a couple articles that this should work on desktop.

---

### Post by Bartly on 2010-01-30
Oops, sorry folks, thought this meant desktop edition vs. server, but apparently this forum means desktop enviros. I'll repost.

---

### Post by mcduck on 2010-01-31
try this:
```

sudo tasksel install lamp-server
```

---

### Post by Lars Noodén on 2010-01-31
> **Bartly said:**
> 
E: Couldn't find package apache2


It looks like your machine does not have any of the [Ubuntu repositories available](https://help.ubuntu.com/community/Repositories) for the package manager or that you are offline or something.

Once the repositories are available, you should be able to see that the package is spelled correctly using apt-cache:

```

sudo apt-get update
apt-cache search apache2

```

---

### Post by rlj1965 on 2010-01-31
Have you added the required repositories?

---

