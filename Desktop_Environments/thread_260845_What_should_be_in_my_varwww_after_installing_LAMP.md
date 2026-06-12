---
title: "What should be in my /var/www/ after installing LAMP?"
date: 2006-09-19
forum: Desktop Environments
---

### Post by Physicist on 2006-09-19
I by mistake delete everything in /var/www/
```

sudo rm -r /var/www/

```

And I laready forget what I had immediately after I installed LAMP according to the [tutorial1]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Apache_HTTP_Server_for_HTTP_.28Web.29_Server_service") and [tutorial2]("https://help.ubuntu.com/community/ApacheMySQLPHP"). Could some saavy people tell me what I had initially? So, if not serious, I can skip the hassle of reinstalling everything to make sure I don't miss any important stuff.

By the way, I do remember initially I had one folder:
```

/var/www/phpmyadmin/

```

What was this thing?

---

### Post by Physicist on 2006-09-21
> **Physicist said:**
> I by mistake delete everything in /var/www/
```

sudo rm -r /var/www/

```

And I laready forget what I had immediately after I installed LAMP according to the [tutorial1]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Apache_HTTP_Server_for_HTTP_.28Web.29_Server_service") and [tutorial2]("https://help.ubuntu.com/community/ApacheMySQLPHP"). Could some saavy people tell me what I had initially? So, if not serious, I can skip the hassle of reinstalling everything to make sure I don't miss any important stuff.

By the way, I do remember initially I had one folder:
```

/var/www/phpmyadmin/

```

What was this thing?



Anybody give me a hand please?

---

### Post by Ramses de Norre on 2006-09-21
I had nothing there when I fresh installed apache. Everything I have in there is added by myself..

---

### Post by mmcclure79 on 2006-09-21
that myphpadmin you had was a link to you myphpadmin folder so that you can administer sql and php via a webinterface instead of the command line. easy enough to reinstall should you want to.

---

### Post by l.tambiah on 2006-09-21
You normally have a apche folder in there which is just a folderr  to say apache is running. Deleting that is not a problem. Your phpmyadmin would have been installed by yourself either using apt-get or downloading it from the website. Basically I create a folder in the /var/www called httpdocs and add my content there.

---

### Post by X.Cyclop on 2006-09-21
Apache and phpMyAdmin are there.

Just, reinstall them.

```
sudo apt-get install --reinstall apache2-common phpmyadmin
```

;)

---

### Post by jschwartz73 on 2006-09-21
I did a LAMP install from the X86 Server Install CD and the only thing that I have in my /var/www is apache2-default.  I am looking for phpmyadmin.  If i do a:

 sudo apt-get install --reinstall apache2-common phpmyadmin 

I get the following error:

E: Couldn't find package phpmyadmin

Any help would be greatly appreciated.

I did a 

 sudo apt-get update

Thanks in advance.

---

### Post by jschwartz73 on 2006-09-21
I solved my problem.

I just read the following which explained the sources.list
changes that were required to install phpmyadmin.

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

I hope this helps someone else.

---

