---
title: "Mysql (does not start) + Mambo"
date: 2005-01-07
forum: General Help
---

### Post by kmf on 2005-01-07
I have a issue installing Mambo on Ubuntu.
I downloaded mysql-* via Synaptic.
I placed my Files are in my Document Root.
Now.
When I try and install Mambo. It says MYSQL is not availible.
After a nmap of my PC it´s true MySQL is not Running .
Yes, The service has been started ...
Any Ideas ?

Karl

---

### Post by az on 2005-01-07
I know that you need to set a password for the root mysql userafter installation:


mysqladmin -u root password "mypassword"

---

### Post by kmf on 2005-01-07
I know I have done this :)

Karl

---

### Post by az on 2005-01-07
I recently tried mambo as well as drupal (another cms)  I installed the mysql-server mysql-client and mysql-common debs and had no problem.  Did you do anything else?

Mambo worked for me right out of the box (after reading the docs...)

---

### Post by machiner on 2005-01-08
Have you worked this out? Lemme know if you have not -- we'll get it working.  I'm no expert but many of my sites are built with mambo - and I have seen many errors with different distros and have managed to get mysql rockin' for Mambo each time.

Lemme know.  oh, and have you tried to admin mysql with webmin? Works a charm, just don't leave webmin running.

---

### Post by kmf on 2005-01-08
hmm after checking the PHP Code I saw that ....
it's looking for a mysql_connect feature which it can't find .....
after a quick google it's seems it's a php feature.

Hmm any idea in what php/ubuntu package this is  ?

Thanks
Karl

---

### Post by az on 2005-01-08
libapache2-mod-php4
php4-mysql

---

### Post by kmf on 2005-01-08
yep it was installed !

Karl

---

### Post by az on 2005-01-09
"it's looking for a mysql_connect feature which it can't find ....."

In Drupal, you get that error if the base_url is incorrectly set.  With drupal, if it is set to localhost and I access from another machine on my lan, it looks for mysql on the querying machine.  

For the time that I tried Mambo, I found that it worked almost identically to drupal, so I hope this helps...

---

### Post by machiner on 2005-01-09
Couple things to get out of the way:

1: in your php.ini file (etc/php4/apache/php4/php.ini  or similar) make sure you uncomment mysql.so

2: CHeck your permissions  (user/owner - mysql) on your database files in your /var/lib/mysql folder

I know - I know, you have probably already done this -- maybe?

In mambo - configuration.php - make sure you don't have the trailing slash (/) following your folder and homepage locations:

/var/www/folder
[http://127.0.0.1/folder](http://127.0.0.1/folder)

You cannot load your homepage, right - have you checked your file permissions? Have you made sure that mysql server is running.. you said that it was...is mysql set to start at boot?

Do you have the correct information to connect to mysql in your configuration.php file? 

These things sure seem trivial, but I usually find that fundamentals solve 99% of problems.  I am sure that you have all this in order - in my mind I start at the bottom.

Maybe you really should install webmin and go through the mysql module.  At least you can have an easy visual on some errors that are relatively easy to solve with webmin.

---

### Post by kmf on 2005-01-10
Sorry,
For responding so Late.
I did get it Working ....
After uncommenting the mysql.so line :)
I feel like a total ass.

Thanks 
    Karl

---

### Post by machiner on 2005-01-11
Naah! -- You shouldn't. When I was a builder (houses, not systems) I sometimes got another set of eyes to check my work. Every once in a while it was a good thing because I missed some little thing.

Glad it's working for you.

Happy computing

---

