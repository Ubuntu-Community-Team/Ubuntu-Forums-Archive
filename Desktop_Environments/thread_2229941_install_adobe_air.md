---
title: "install adobe air"
date: 2014-06-16
forum: Desktop Environments
---

### Post by cmcanulty on 2014-06-16
I am having no luck installing adobe air on xubuntu 14.04 64 bit. The threads for installing it on ubuntu 12.04 don't work. I need it to read magazines from zinio.

---

### Post by Frogs Hair on 2014-06-16
According to the link a required package ( ia32-libs) was removed in 13.10 and  the author added an old repository for 64 bit installation. I find nothing current for 32 bit installations.

[http://www.leniwiec.org/en/2014/04/25/how-to-install-adobe-air-on-64bit-ubuntu-14-04lts/](http://www.leniwiec.org/en/2014/04/25/how-to-install-adobe-air-on-64bit-ubuntu-14-04lts/)

---

### Post by cmcanulty on 2014-06-16
thanks I get an error at the 2nd command

```
cmcanulty@ubuntu1:/etc/apt/sources.list.d$ sudo echo "deb http://archive.ubuntu.com/ubuntu/ raring main restricted universe multiverse" >ia32-libs-raring.list
bash: ia32-libs-raring.list: Permission denied
```

---

### Post by cmcanulty on 2014-06-16
OK I have it installed and also installed elance tracker don't even know what that is but followed instructions on this page
[http://www.tkalin.com/blog_posts/installing-adobe-air-and-elance-tracker-on-ubuntu-13-10-saucy-salamander-64-bit]("http://www.tkalin.com/blog_posts/installing-adobe-air-and-elance-tracker-on-ubuntu-13-10-saucy-salamander-64-bit")
 now if I open adobe air it goes to thunar. If I go to library and click read now air opens to a blank grey page. Very complicated!

---

