---
title: "Apache Help"
date: 2006-01-08
forum: General Help
---

### Post by jon_z on 2006-01-08
jon@ubuntu:~$ apache2
(13)Permission denied: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

i have port 80 correctly fowarded to my machine through my router (linksys router and i have been using it for 3 years, i know howto use it ;-) )

Any ideas on whats going on?

---

### Post by kairu0 on 2006-01-08
You don't have a problem with your router. The problem is that you cannot run apache as any user; you must be root.

And, it should already be running when you start you computer. Try this:

```
sudo /etc/init.d/apache2 restart
```

---

### Post by jon_z on 2006-01-08
This is pretty vague, but i installed the apache2 package via synaptic, set the homepage in /var/www  when people try to view my webpage they say the page doesnt load at all..

---

### Post by Thirsteh on 2006-01-08
[QUOTE=jon_z]This is pretty vague, but i installed the apache2 package via synaptic, set the homepage in /var/www  when people try to view my webpage they say the page doesnt load at all..[/QUOTE]

That would indeed seem to be a problem with your router, or of course that your apache service is still not running correctly.

---

### Post by jon_z on 2006-01-08
DMZ host is set to my machines ip 192.168.1.38..  & the port 80 has been fowarded just incase

---

### Post by jferrando on 2006-01-08
Open a browser in your machine, and type:

*[http://localhost](http://localhost)*

And see what you get. If you have NATTED your router, with TCP port 80 to your local machine, people should get the same page as you.

Apache2 configuration files are found in the /etc/apache2 directory. Take a littke time browsing through them. The web page contents are usually installed in /var/www, but it depends on what you specified in the */etc/apache2/sites-available/default* file. Gook luck!

---

