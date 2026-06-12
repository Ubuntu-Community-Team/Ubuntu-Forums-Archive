---
title: "Installing PHP"
date: 2009-01-18
forum: General Help
---

### Post by kyalee on 2009-01-18
I want to be able to test the php scripts that I write on my computer without having to upload them to my webserver. Is this the correct code? 

```
sudo apt-get apache2 php5-mysql libapache2-mod-php5 mysql-server
```

Once I run that, will I be able to simply double click on PHP files and see them run in my browser?

Sorry for the stupid question, but I went through fits trying to get PHP installed once before and finally gave up in frustration. I want to get it right this time.

---

### Post by mcduck on 2009-01-18
No, that won't work.

PHP is always interpreted by a web server to create a HTML document your browser is able to display. If you want, you can install Apache & PHP to create a local server on your machine for easier testing, but you still can't open the PHP file itself with the browser.

The easiest way to install LAMP server is to use this command:
```
sudo tasksel install lamp-server
```
After that you'll need to put your PHP files in /var/www/ (which is the root directory of the server. You can then see them if you go to [http://localhost/](http://localhost/) with your browser.

---

### Post by kyalee on 2009-01-18
Okay, thank you. I ran 

```
sudo tasksel install lamp-server
```

It's hanging at 0%, though, and has been for several minutes. Does it usually take a really long time?

EDIT: Nevermind, it's doing something now. I guess it just needed a few minutes to get going. :)

---

### Post by kyalee on 2009-01-18
Okay, cool. I pointed my browser to [http://localhost/](http://localhost/) and got a message telling me that it works.

Now, how do I access the PHP scripts? I moved a test script to the /var/www/ folder, but I can't seem to access it. I tried running [http://localhost/script.php](http://localhost/script.php) but it did the same old thing where Firefox just wanted to save it.

---

### Post by mcduck on 2009-01-18
try this:
```

sudo a2enmod php5
sudo /etc/init.d/apache2 restart
```

The first command makes sure that PHP is enabled in Apache, the second one restarts the server.

You may also need to empty your browser's cache.

---

### Post by kyalee on 2009-01-18
Clearing the browser cache was what finally did it. My test script ran. Thanks for your help.

---

