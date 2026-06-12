---
title: "Turn down LAMP"
date: 2009-06-25
forum: General Help
---

### Post by carlosgs91 on 2009-06-25
.

---

### Post by Celauran on 2009-06-25
You can turn Apache off like so:

```
sudo /etc/init.d/apache2 stop
```

Sounds like your problem runs deeper than that, though.

---

### Post by carlosgs91 on 2009-06-26
.

---

### Post by wojox on 2009-06-26
Ok first off LAMP is an acronym.
Linux-Apache-MySQL-PHP
When you shut down Apache you also shut down PHP. It's loaded as a module.
Now you just need to shut down MySQL.
Bam everything's shut down.
Now look in your error logs for Apache and it should say something like unable to resolve ServerName 127.0.0.1.
You need to edit you configuration file and set the ServerName to whatever your ip address is. Go to the Apache site and read the manual if you need further instructions on doing this.

---

