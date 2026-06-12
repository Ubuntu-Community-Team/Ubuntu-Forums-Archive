---
title: "cant install mythtv 0.20 using apt-get"
date: 2006-09-24
forum: Desktop Environments
---

### Post by kevinherring on 2006-09-24
I have added the following to my sources.list:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy multiverse

and run apt-get update

now when I try to do apt-get install mythtv-backend I get:
```

The following packages have unmet dependencies.
  mythtv-backend: Depends: libasound2 (> 1.0.11) but 1.0.10-2ubuntu4 is to be installed
                  Depends: libavc1394-0 (>= 0.5.3) but 0.5.1-1 is to be installed
                  Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20 is to be installed
                  Depends: libfreetype6 (>= 2.2) but 2.1.10-1ubuntu2.2 is to be installed
                  Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
                  Depends: libglib2.0-0 (>= 2.12.0) but 2.10.3-0ubuntu1 is to be installed
                  Depends: libiec61883-0 but it is not installable
                  Depends: libjack0.100.0-0 (>= 0.101.1) but it is not going to be installed
                  Depends: libmyth-0.20 but it is not going to be installed
                  Depends: libraw1394-8 but it is not installable
                  Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
E: Broken packages


```

how can it be that the version of mythtv specifically for ubuntu requires non-ubuntu packages?

Thanks
Kevin

---

### Post by austin on 2006-10-16
same problem here

how it can be is easy to answer - I think it's because of the beta status

Maybe we need the non-free repo?

---

### Post by superm1 on 2006-10-26
If you are on dapper attempting to install mythtv 0.20, don't use an edgy repository.  Those packages are compiled for edgy, and require edgy libraries.

Use my mirror for dapper packages

```
#my myth repo
deb http://home.eng.iastate.edu/~superm1 dapper main
deb-src http://home.eng.iastate.edu/~superm1 dapper main
```

---

### Post by austin on 2006-10-26
no no, I'm on edgy. It was beta when I hat those problems. Next session I'll upgrade to final and try again

---

### Post by superm1 on 2006-10-26
It almost appears as though you haven't ran sudo apt-get update in a while.

According to the apt policy for one of those packages that you couldn't install, this is the latest version:

mlimon@workingmario:~$  apt-cache policy libgcc1
libgcc1:
  Installed: 1:4.1.1-13ubuntu5
  Candidate: 1:4.1.1-13ubuntu5
  Version table:
 *** 1:4.1.1-13ubuntu5 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
        100 /var/lib/dpkg/status

---

### Post by superm1 on 2006-10-26
Also, you need both universe and multiverse.
```

mlimon@workingmario:~$ apt-cache policy libjack0.100.0-0
libjack0.100.0-0:
  Installed: (none)
  Candidate: 0.101.1-1
  Version table:
     0.101.1-1 0
        500 http://archive.ubuntu.com edgy/universe Packages
```

Some packages pull from universe.

---

