---
title: "Apache2 error.."
date: 2009-03-30
forum: General Help
---

### Post by mindblaster7 on 2009-03-30
Hey. I just got Xubuntu 8.10 installed, and I want to work with some website, so I downloaded php5, mysql and apache2, but when I go to var/www and try to edit the index.html just to test it, it refuses to save.
Heres what I get:
"Can't open file to write"
also I can't copy any files into the folder or make new files there.

---

### Post by stereomuffin on 2009-03-30
Probably a file permissions issue..
Open up a terminal and type: gksudo nautilus /var/www

---

### Post by mindblaster7 on 2009-03-30
Thanks for the fast reply, but it seem not to change anything.

---

### Post by stereomuffin on 2009-03-30
Whats the output of: ls -l /var/www 
?

---

### Post by mindblaster7 on 2009-03-30
Sorry for the late reply.

```
mindblaster7@mindblaster7-laptop:~$ ls -l /var/www/
total 12
-rw-r--r-- 1 root root 147 2009-03-30 19:14 andreas.html
-rw-r--r-- 1 root root  45 2009-03-30 15:02 index.html
-rw-r--r-- 1 root root 152 2009-03-30 19:16 tezt.php
mindblaster7@mindblaster7-laptop:~$ 

```
I moved 2 files with the CP thing, but also noticed that when I open a .php file with firefox, it tries to download it, instead of trying to display it.

---

### Post by stereomuffin on 2009-04-01
You can try the suggestions posted here: (have a look at the comments concerning your problem with downloading the php file)

[http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/)

---

