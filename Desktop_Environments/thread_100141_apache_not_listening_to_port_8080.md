---
title: "apache not listening to port 8080"
date: 2005-12-07
forum: Desktop Environments
---

### Post by aksum on 2005-12-07
Apache works on port 80 using either of 'localhost', 'my local ip', or my host name in the browser.  However, I've configured the httpd.conf to listen to port 8080 in addition to port 80.   In the browser I try to access my web page in the following fashion:  [http://localhost/index.html:8080](http://localhost/index.html:8080)

The result:
[B]
Not Found

The requested URL /index.html:8080 was not found on this server.
Apache/2.0.55 (Unix) mod_ssl/2.0.55 OpenSSL/0.9.8a PHP/5.0.5 DAV/2 mod_perl/2.0.1 Perl/v5.8.7 Server at localhost Port 80[/B]

Note, the error refers to port 80 in the end.
Seems as though apache is only listening to 80, but here is my entry in httpd.conf:
Listen 80
Listen 8080

My isp blocks port 80, so I want to set up a public website on a port that isn't blocked using the services of dyndns.org.  Again, my website works privately on port 80, but does not privately on port 8080.

My current installation of apache was made using the xampp suite of applications.  My next step would be removing the xampp, and installing apache from the synaptic.

Using 5.10
Apache 2.0.55
Any help is appreciated.
Thanks,

---

### Post by syncme on 2005-12-07
Try [http://localhost:8080/index.html](http://localhost:8080/index.html) instead :)

---

### Post by aksum on 2005-12-07
Great!, I was sorta hoping it was something simple(stupid) like that.
Thanks much,

---

### Post by syncme on 2005-12-07
not a problem ....

Sometimes even the simplest things can frustrate us all. 

Just glad I could help.

Syncme

---

