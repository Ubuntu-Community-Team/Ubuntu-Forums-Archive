---
title: "Repos for Edgy"
date: 2006-10-15
forum: Desktop Environments
---

### Post by someguyouknow on 2006-10-15
I am looking for repos for Edgy... I have some but i dont have the keys for them so there are some packages missing. 

Thanks in advance.

---

### Post by aysiu on 2006-10-15
Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by NeoLithium on 2006-10-15
These are the souces that I have enabled, so you may want to compare with yours.

```

# Edgy Final Release Repository
deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse 
# deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse 

# Edgy Security Updates
deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse 
# deb-src http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse 

# Edgy Bugfix Updates
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse 
# deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse 

# Edgy Backports (new software versions, provided by the Ubuntu Backports Project)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse 
# deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse 

#Ubuntu Commercial
deb http://archive.canonical.com/ubuntu edgy-commercial main 
# deb http://archive.canonical.com/ubuntu edgy-commercial main 

```

---

### Post by someguyouknow on 2006-10-15
This is what i use...
its from the kubuntu boards
```
deb http://archive.ubuntu.com/ubuntu edgy main
deb-src http://archive.ubuntu.com/ubuntu edgy main

deb http://archive.ubuntu.com/ubuntu edgy restricted
deb-src http://archive.ubuntu.com/ubuntu edgy restricted

deb http://archive.ubuntu.com/ubuntu edgy universe
deb-src http://archive.ubuntu.com/ubuntu edgy universe

deb http://archive.ubuntu.com/ubuntu edgy multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy multiverse

# Dapper Security Updates
deb http://archive.ubuntu.com/ubuntu edgy-security main
deb-src http://archive.ubuntu.com/ubuntu edgy-security main

deb http://archive.ubuntu.com/ubuntu edgy-security restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-security restricted

deb http://archive.ubuntu.com/ubuntu edgy-security universe
deb-src http://archive.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu edgy-security multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-security multiverse

# Dapper Bugfix Updates
deb http://archive.ubuntu.com/ubuntu edgy-updates main
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main

deb http://archive.ubuntu.com/ubuntu edgy-updates restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-updates restricted

deb http://archive.ubuntu.com/ubuntu edgy-updates universe
deb-src http://archive.ubuntu.com/ubuntu edgy-updates universe

deb http://archive.ubuntu.com/ubuntu edgy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb http://archive.ubuntu.com/ubuntu edgy-backports main
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main

deb http://archive.ubuntu.com/ubuntu edgy-backports restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-backports restricted

#deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

#deb http://archive.ubuntu.com/ubuntu edgy-backports universe
#deb-src http://archive.ubuntu.com/ubuntu edgy-backports universe

#deb http://archive.ubuntu.com/ubuntu edgy-backports multiverse
#deb-src http://archive.ubuntu.com/ubuntu edgy-backports multiverse

deb http://www.beerorkid.com/compiz edgy main-edgy
deb http://media.blutkind.org/xgl/ edgy main-edgy
deb http://ubuntu.compiz.net/ edgy main-edgy

deb http://givre.cabspace.com/ubuntu/ edgy main
deb-src http://givre.cabspace.com/ubuntu/ edgy main
deb http://people.ubuntu.com/~doko/ubuntu/ edgy/$(ARCH)/
deb http://people.ubuntu.com/~doko/ubuntu/ edgy/all/

deb http://www.debian-multimedia.org sid main

deb http://kubuntu.org/packages/koffice-latest edgy main
```

---

### Post by aysiu on 2006-10-15
> **someguyouknow said:**
> ```

deb http://www.beerorkid.com/compiz edgy main-edgy
deb http://media.blutkind.org/xgl/ edgy main-edgy
deb http://ubuntu.compiz.net/ edgy main-edgy

deb http://givre.cabspace.com/ubuntu/ edgy main
deb-src http://givre.cabspace.com/ubuntu/ edgy main
deb http://people.ubuntu.com/~doko/ubuntu/ edgy/$(ARCH)/
deb http://people.ubuntu.com/~doko/ubuntu/ edgy/all/

deb http://www.debian-multimedia.org sid main

deb http://kubuntu.org/packages/koffice-latest edgy main
``` It looks as if you have a lot of non-standard repositories in there. Are you sure they have Edgy repositories? They may not for another week or two.

---

### Post by NeoLithium on 2006-10-15
Whoah; that's a lot more than mine. I seem to have no problems with not having any packages found that I might need. I wonder if I'm missing anything by not having a few that you have up....?

EDIT Just wondering cause with this set up, I have definite edgy repos with 20,000+ packages...

---

### Post by someguyouknow on 2006-10-15
Thanks. i will use your list until i can either find the keys or get an official list.

---

