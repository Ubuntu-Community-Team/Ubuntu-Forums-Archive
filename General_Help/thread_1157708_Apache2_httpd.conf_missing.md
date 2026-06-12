---
title: "Apache2: httpd.conf missing"
date: 2009-05-13
forum: General Help
---

### Post by sswittch on 2009-05-13
Hi,

I am missing my httpd.conf file.  I cannot find a backup of it on my server anywhere.  Is there any way I can rebuild this or have I killed yet another server ?

---

### Post by geraldvillorente on 2009-05-13
try to locate it...
```

locate httpd.conf

```
should be like this
> /etc/apache2/httpd.conf

---

### Post by sswittch on 2009-05-13
> **geraldvillorente said:**
> try to locate it...
```

locate httpd.conf

```


I have tried this and cannot find any on my server.

my httpd.conf located in /etc/apache2/ has nothing in it.  The locate only finds docs in the apache2 docs file. httpd-ssl.conf is the closest I can find but this would not contain all the info I need for apache2 to function correctly on the server.

---

### Post by BUSHYBOB on 2009-05-13
The default configuration file for apache2 is /etc/apache2/apache2.conf.

---

### Post by lamenramen on 2013-03-17
> **BUSHYBOB said:**
> The default configuration file for apache2 is /etc/apache2/apache2.conf.


This is endlessly confusing for newbies, like myself.

If you install from sudo-apt-get install, you get an entirely different set of files and directory structures than if you just download the binaries, unzip it.  If you download from the Apache site, you get an httpd.conf file.  Is there a synonym for an httpd.conf file?

---

### Post by Doug S on 2013-03-17
I think a moderator will close this thread, because it is so old.

Yes, it can be confusing, very confusing, at times.

Have a look here: [http://ubuntuforums.org/showthread.php?t=2118233&p=12520969#post12520969](http://ubuntuforums.org/showthread.php?t=2118233&p=12520969#post12520969)

---

### Post by Toz on 2013-03-17
And on that note.... closed.

---

