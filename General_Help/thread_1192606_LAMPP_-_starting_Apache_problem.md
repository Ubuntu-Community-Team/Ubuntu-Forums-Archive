---
title: "LAMPP - starting Apache problem"
date: 2009-06-20
forum: General Help
---

### Post by Laki on 2009-06-20
Hi. I've installed Lampp 2 ways. First with regular downloading, extracting and starting everything with > sudo /opt/lampp/lampp start command. The result was XAMPP: Another web server daemon is already running.

Then I installed with > sudo tasksel install lamp-server command. I restarted the machine, and tried with [http://localhost](http://localhost) in browser, but nothing showed up.

In console I typed > sudo /etc/init.d/apache2 restart, and got
>  * Restarting web server apache2                                                (98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]

I also have installed and running VMware Server, which is accessible at 127.0.0.1:8333, and I think this is the problem for me, not being able to start up the Apache.

I need help determining what is the problem, and how to solve it.

---

### Post by credobyte on 2009-06-20
80 port is already in use and you need to "release" it.

```
sudo /opt/lampp/lampp stop
sudo /etc/init.d/apache2 restart
```

---

### Post by Laki on 2009-06-20
credobyte, thank you for helping. Indeed port 80 is already in use, but not by Apache. I tried your commands before, and did so again now, and the result is the same. I think VMware server or something else is using port 80, but I don't know how to find out what is using it, and then how to reconfigure Apache or the other application (which is using port 80), to work on some other port.

---

### Post by credobyte on 2009-06-20
httpd.conf ( Windows ) or apache2.conf ( Ubuntu ). Look for "Listen" and change 80 to whatever you wan't ( 666 :D ).

---

### Post by Kareeser on 2009-06-20
You have too many web servers running, and they can not all listen on the same port. Either do as **credybyte** says, and change the port, or shutdown/uninstall the other unused web servers.

Contrary to popular opinion, you cannot simply install more programs to make a problem go away.

---

### Post by el.otro on 2009-06-20
I think you could change in the file
 ```
/etc/apache2/ports.conf
```the Listen directive to 8000:
```
Listen 8000
```or whatever port you want, also check the 
```
NameVirtualHost *:
```statement, it has to match
```
 ./sites-enabled/000-default
```...it is most likely the XAMPP using port 80, I haven't used it before, so I wouldn't know what to do there; I know its apache-based, so it probably uses a similar config.

also, instead of restarting apache use:
```
sudo /etc/init.d/apache2 reload
``` to load the new configuration, and then 
```
sudo /etc/init.d/apache2 restart
```That's what I can see, I hope it was helpful...

---

### Post by Laki on 2009-06-20
Thank you all for helping. I did as el.otro suggested, and now it all works fine. Just needed to change NameVirtualHost *: to 8000 both in /etc/apache2/ports.conf and /etc/apache2/sites-enabled/000-default, and needed to CHMOD /var/WWW. 

Thanks again.

---

