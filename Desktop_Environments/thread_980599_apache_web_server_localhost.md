---
title: "apache web server/ localhost"
date: 2008-11-13
forum: Desktop Environments
---

### Post by raunhar on 2008-11-13
I installed MySQL and checked [http://localhost](http://localhost) . It showed sucess.
But I cannot figure out, where the folder www is.

I also want to copy some sites from windows www folder (through easy php).

---

### Post by Rhubarb on 2008-11-13
> **raunhar said:**
> I installed MySQL and checked [http://localhost](http://localhost) . It showed sucess.
But I cannot figure out, where the folder www is.

I also want to copy some sites from windows www folder (through easy php).

The www folder is located at:  **/var/www/**
You may need to change ownership of the files in the /var/www/ directory, so it's owned by **www-data**

---

### Post by raunhar on 2008-11-14
Currently the owner is showing as root. How do i change the ownership

---

### Post by R.Bucky on 2008-11-14
sudo chmod 777 /var/www/ -R should allow read/write to all folders and files within the www directory

---

### Post by y@w on 2008-11-14
You don't want to chmod 777 that directory.. It'll allow read-write-execute to everyone. Just chown it so the web server owns it: 

```
chown -R www-data:www-data /var/www
```

---

### Post by R.Bucky on 2008-11-14
Doh! thanks for catching that one!

---

### Post by raunhar on 2008-11-14
Thanks.
Did that and I was able to access the folder. BUt when I try to open a web site by giving the command localhost/xyz, it says 403 Forbidden. I edited the folder permissions alos but still the same error

---

### Post by raunhar on 2008-11-14
did chown as directed in the terminal. Error: Permission not granted.

---

### Post by R.Bucky on 2008-11-14
you need to give the command "sudo" powers. e.g. **sudo chown -R www-data:www-data /var/www **

---

### Post by raunhar on 2008-11-14
Thanks for the reply.

Now when I try to open the site uisng [http://localhost/xyz](http://localhost/xyz) , it says :
Opening
You have chosen to open     which is a :PHTML file from [http://localhost](http://localhost)

What should Firefox do with this file?
Open
Save

The file is index.php

Please suggest

---

### Post by R.Bucky on 2008-11-14
Yup, this problem often pops up with a phpmyadmin install as well. I have had success with adding the below code to my httpd.conf file. 
[B]AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps[/B]

---

### Post by raunhar on 2008-11-14
Thanks for the reply.
I added those lines, but still it asks for the options to save or open

I added those two lines s it is. Before that the httpd.conf was empty

---

### Post by ShizzlePDX503 on 2009-10-17
not sure if this was resolved or not but after you add those two lines then you have to restart the webserver

for example
```
sudo /etc/init.d/apache2 restart
```

---

