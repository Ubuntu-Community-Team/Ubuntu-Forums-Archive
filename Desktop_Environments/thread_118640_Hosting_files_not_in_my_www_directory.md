---
title: "Hosting files not in my www directory"
date: 2006-01-17
forum: Desktop Environments
---

### Post by stiankarlsen on 2006-01-17
I have just set up an HTTP server, which can be reached here: [http://84.234.177.118/]("http://84.234.177.118/")

I was just wondering, can I host files that are placed in my account home dir, or do i have to place them in /var/www for that to work?


edit:

before i forget, is there a way i can see ip's that are connected to my server?

---

### Post by lamego on 2006-01-17
[QUOTE=stiankarlsen]I have just set up an HTTP server, which can be reached here: [http://84.234.177.118/]("http://84.234.177.118/")

I was just wondering, can I host files that are placed in my account home dir, or do i have to place them in /var/www for that to work?


edit:

before i forget, is there a way i can see ip's that are connected to my server?[/QUOTE]
You can place the files anywhere on your system as long you setup the web root path with:
sudo gedit /etc/apache2/sites-available/default
I believe you will need to restart apache:
sudo /etc/init.d/apache2 restart

You also need to make sure that you have the correct ownership/permissions set on the dir, usually 755 is fine.

---

### Post by shakin on 2006-01-17
you can also symlink any file or folder.

For example, if you want the web directory [http://84.234.177.118/personal](http://84.234.177.118/personal) to contain files from your ~/personal directory, do this:

ln -s ~/personal /var/www/personal

---

### Post by stiankarlsen on 2006-01-18
Thanks guys

will try this as soon as i get home from school.

---

### Post by stiankarlsen on 2006-01-18
by the way, why wont .htaccess documents work?


and how do i set a password for my mysql server?

---

### Post by Chris Tucker on 2006-01-18
.htaccess and .htpasswd docs work so long as your apache conf is set right.
also, about stuff from school... time to learn about ssh :) you can load PuTTY right off the net.. no install :) or install webmin on your server and use the built in web-ssh client in that.

---

### Post by stiankarlsen on 2006-01-18
how do i launch putty from school?

---

### Post by Chris Tucker on 2006-01-19
google putty, either download the putty standalone EXE or zip. then just run it.

---

