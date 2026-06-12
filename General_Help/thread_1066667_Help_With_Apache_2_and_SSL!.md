---
title: "Help With Apache 2 and SSL!"
date: 2009-02-11
forum: General Help
---

### Post by Canuckelhead on 2009-02-11
I can use SSL once.  I can reinstall apache2 and go through the hoops to enable ssl but when I reboot I can't start apache at all... 
I get the error:  
> apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs


I've tried commenting out listen 80 on ports.conf 

Not working... any help???

---

### Post by Canuckelhead on 2009-02-11
bump

---

### Post by Jac3510 on 2009-02-11
Try opening /etc/apache2/httpd.conf file and add the following line:

ServerName nameofserver

I'm not familiar with SSL, but that's what I had to do when I got that error.

---

### Post by jonobr on 2009-02-11
Shut down apache and try attaching using port 80.
(Open a browser and put in the IP address) 
See if something responds.

It looks like something else is using that port number if I read your logs correctly???

---

### Post by Canuckelhead on 2009-02-11
Now I just get:

> (98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]


---

