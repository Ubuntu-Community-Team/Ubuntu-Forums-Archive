---
title: "Problem with apache/PHP5"
date: 2009-03-23
forum: General Help
---

### Post by Letterbomb05 on 2009-03-23
Hi,
I'm new to Linux, and have just installed the PHP, apache etc with the following command: ```
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server
```

The localhost works fine, however when I try and view a PHP file, the browser does not parse it, simply tries to download the file instead. Not sure why this is happening, thanks in advance for any help.

Letterbomb05.

---

### Post by James_Lochhead on 2009-03-23
[Best source for apache info on Ubuntu]("https://help.ubuntu.com/community/ApacheMySQLPHP")

The easiest way to install that stuff is:

```
sudo tasksel install lamp-server
```

Read the link above for configuration details.

Your problem is occuring because your browser cannot execute PHP like it can HTML; since the browser cannot execute the PHP is decided you want to download it.

PHP (when used in this manner) is a server side scripting, it must be executed by the server before a user attempts to download the file. 

When set up properly there will be a folder on your machine for Apache. Mine is /home/james/WebServer/. When I put PHP files in it I cannot run them by clicking the files. I have to open my browser and type localhost (this will access the directory or index file if you have one). You can browser files in Apache by adding stuff on localhost. For example, if I had a PHP file /home/james/WebServer/hello/hello.php I could execute it by typing localhost/hello/hello.php.

The guide I mentioned above will help you get everything set up nicely. It is not hard and takes maybe 20 minutes of reading.

To summarise:

Install PHP, Apache and MySQL:

```
sudo tasksel install lamp-server
```

Set up virtual hosts (i.e. configure Apache so it works):

[https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts")

---

### Post by Letterbomb05 on 2009-03-23
Thanks, however I have already read the guide AND tried LAMP SERVER and I had the same problem; this was what lead me to use this method for installing these packages. I am also running the files via localhost already and yet the problem persists. Is there anything else that may be causing the problem?

---

### Post by howlingmadhowie on 2009-03-23
does the file have the ending .php?

are you sure you're calling it over the webserver and not opening the file with firefox?

---

### Post by Letterbomb05 on 2009-03-23
Yes it is a PHP file with .PHP extension. I am going to localhost in firefox and clicking on the file; this is when the problem occurs.

---

### Post by howlingmadhowie on 2009-03-23
> **Letterbomb05 said:**
> Yes it is a PHP file with .PHP extension. I am going to localhost in firefox and clicking on the file; this is when the problem occurs.

what do you mean by clicking on the file?

can you enter the address directly into firefox, something like:

[http://localhost/mytestfile.php](http://localhost/mytestfile.php)

---

### Post by Letterbomb05 on 2009-03-23
Clicking on the file as in clicking on the hyperlink to localhost/test.php.

---

### Post by ibuclaw on 2009-03-23
After install the LAMP Server, all files for your website go inside this directory:
```
/var/www
```

But since this directory is usually writeable only by root. It's best to get it setup first.

ie:
```
sudo chmod 775 /var/www
```
```
sudo chgrp admin /var/www
```
And to ensure that you are part of the admin group
```
groups | grep " admin " --color=always
```
It should show up in [COLOR="Red"]**red**[/COLOR].

Now logout/log back in again to have full write access to that directory.
To which you just copy/move your php scripts to that folder and type in your browser:
```
http://localhost/**myfile.php**
```

Regards
Iain

---

### Post by Letterbomb05 on 2009-03-23
Thanks alot! Got the problem solved.

---

