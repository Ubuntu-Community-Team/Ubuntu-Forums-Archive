---
title: "Execute php script with localhost"
date: 2009-04-15
forum: Desktop Environments
---

### Post by DFHIII on 2009-04-15
This is the latest attempt at running localhost php.

I did a clean installation of ubuntu and ran all of the updates.  I used the following apt-get to install LAMP:

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

That seemed to run successfully. 

I created two index files in www, index.html and index.php.  Their contents are as follows:

index.html:
<html><body><h1>It works!</h1></body></html>

index.php:
<html><body><h1>
<?php echo "It works with PHP as well"; ?>
</h1></body></html>

index.html opens in the browser with "It works!"

index.php gives me a message box:

You have chosen to open index.php which is a PHP file from /var/www
What should Firefox do with this file?

I did a lot of development on my old ubuntu 8.04 system using apache, php, and mysql.  What am I missing on this system?  Where can I start looking for hints?  This is also ubuntu 8.04.

Thanks,

Dan H.

---

### Post by PacSci on 2009-04-15
Check the output of 'ls /etc/apache2/mods-enabled'. If something named 'php' is not in there, check /etc/apache2/mods-available for something like 'php.load' (maybe 'php5.load')? Then, take the '.load' off the end and pass that to a2enmod (example: 'sudo a2enmod php' or 'sudo a2enmod php5').

BTW, this topic is better suited to the Server support discussions, since you're talking about a Web server.

---

### Post by DFHIII on 2009-04-15
I found php5.load with mods-available and ran a2enmod php5.  I got this reply:

run /etc/init.d/apache2 force-reload

I executed:
sudo /etc/init.d/apache2 force-reload

I got:
 *Reloading web server config apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

This topic may be better suited to the Server support discussions, but I am running using localhost on Ubuntu Desktop.

---

### Post by mcduck on 2009-04-16
How are you exactly opening these files? By clicking on the file itself, or by accessing it through the server (as in going to [http://localhost/index.php](http://localhost/index.php) with your browser)?

Even with LAMP server installed, PHP files are still server-side scripts, not documents that you can open directly. The script must be run by the server to generate a web page that is then sent to your browser..

---

### Post by DFHIII on 2009-04-16
That worked!  I was opening the document directly.  Thank you very much.

Below is my summary of the problem and solution.  I keep these notes for when I make the same mistake again.

When I tried to open index.php I got the following message:

You have chosen to open index.php which is a PHP file from /var/www
What should Firefox do with this file?

I checked to see if I had a php module enabled with:

ls /etc/apache2/mods-enabled

There was no php module enabled, so I checked to see if one was available with:

ls /etc/apache2/mods-available

I found I had php5.load available, so I enabled php5 with:

sudo a2enmod php5

I got the message: run /etc/init.d/apache2 force-reload

I executed: sudo /etc/init.d/apache2 force-reload

and got:
*Reloading web server config apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

The last problem was caused by opening the document itself instead of accessing it through the server.  When I opened it through the browser address field with [http://localhost/index.php](http://localhost/index.php) it worked as advertised.

---

