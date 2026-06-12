---
title: "Can't find fileserver"
date: 2006-06-16
forum: Desktop Environments
---

### Post by jewishj on 2006-06-16
I have two ubuntu machines.  One is a fileserver with apache/php/mysql (named "fileserver" with a local ip of 192.168.1.100) and one is my main machine.  If I type [http://fileserver](http://fileserver) into a windows machine that is on the computer (in firefox, opera, or ie) it loads fine.  From my main (second ubuntu) machine I type in [http://fileserver](http://fileserver) and it takes me to some domain registration site for fileserver.com ([http://192.168.1.100](http://192.168.1.100) still works though).  I was wondering if anyone knows why this would be happening?

Thanks

---

### Post by frup on 2006-06-16
try [http://192.168.1.100](http://192.168.1.100)

oops didnt read properly lol.
on firefox for me if i type anything that is not a proper website it tries to google search..

---

### Post by scxtt on 2006-06-16
what's your /etc/hosts file look like?

you'll possibly need to "tell" ubuntu that "fileserver" points to the 192.168.1.100 IP address ...```
/etc/hosts example:

127.0.0.1          localhost
192.168.1.100      fileserver
192.168.1.101      main_box
```

---

### Post by jewishj on 2006-06-16
That did it.. thanks! :D :D

---

