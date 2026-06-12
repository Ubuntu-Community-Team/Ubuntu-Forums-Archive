---
title: "Apache2 Memory Usage"
date: 2006-01-14
forum: General Help
---

### Post by Evil Dax on 2006-01-14
Hi,
I am using Ubuntu now for a few monts, and I really like it.
The problem which I have right now:
I'm using a very small webserver with Apache2 (only HTML, no PHP or SQL)
but Apache seems to eat up most of my memory:
System monitor shows 4 instances of Apache2:
6.9MB, 7.1MB, 223.4MB and 223.5 MB.

This totals to about 470MB... seems an aweful lot for a tiny webserver.
Killing either one of these instances results in a restart of the application..

Any ideas on how to get the memory usage down?

---

### Post by aPello on 2006-01-15
I dont see a cause for your problem. It seems that you installed apache wrong. I am running apache/php/mysql servers + gaim + firefox n a few terminals and am only using a total of 138mb ram. Try uninstalling apache and then reinstalling it.

---

### Post by Evil Dax on 2006-01-18
Hmm, I've re-downloaded and re-installed apache2, but it is still eating all those Megabytes... anybody more ideas ??

---

### Post by Yogarine on 2006-01-19
Easy solution:

sudo apt-get install apache2-mpm-prefork

This will replace a part of apache2 and make it use some other default settings that use a lot less memory.



Complicated solution:
Edit to your /etc/apache2/apache2.conf and modify the part:

<IfModule worker.c>
StartServers 2
MaxClients 150
MinSpareThreads 25
MaxSpareThreads 75
ThreadsPerChild 25
MaxRequestsPerChild 0
</IfModule>

To use some lower values. Just experiment untill your get a good memory usage/performance.

---

### Post by Evil Dax on 2006-01-20
I've tried to edit this 'complicated solution' before, but it didn't do much difference.

However, the 'easy solution'  did the trick !
Memory usage down to 4x 7.1MB instead of 450+

:smile: 

Thanks a lot !

---

