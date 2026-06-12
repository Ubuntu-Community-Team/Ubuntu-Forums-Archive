---
title: "Nothing in my source list!  HELP!!!"
date: 2006-06-04
forum: Desktop Environments
---

### Post by Magiczero on 2006-06-04
I am running 5.10 and I have no idea how this happened but I was trying to upgrade to 6.06 and I was getting an error that said I had nothing in my source file.  So I ckecked it and I had nothing in there.  Can anyome tell me the main things I need in the source file so that I can get the new distrobution? 
Thanks

---

### Post by Anduu on 2006-06-04
Here is what my sources list looks like...It has been modified by me many times but should do the trick.

```
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
```

---

