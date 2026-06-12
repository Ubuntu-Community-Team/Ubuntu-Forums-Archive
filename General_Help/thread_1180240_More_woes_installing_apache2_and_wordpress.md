---
title: "More woes installing apache2 and wordpress"
date: 2009-06-06
forum: General Help
---

### Post by litlfrog on 2009-06-06
I've never tried to configure web server software and I'm very frustrated here. I followed instructions [here]("http://www.jonathanmoeller.com/screed/?p=932") to install apache2, MySQL, and PHP5 on the latest version of Ubuntu. When I try to browse to either [http://localhost](http://localhost) or [http://localhost/wordpress](http://localhost/wordpress), I get

> Not Found

The requested URL / was not found on this server.
Apache/2.2.11 (Ubuntu) Server at localhost Port 80

I don't know how to troubleshoot something like this and I'm finding surprisingly little online (at least that I can understand). I have lots of info on how to install WordPress, but nothing explaining what to check and what steps to take if the browser doesn't show the default page. Could anyone provide some insight? It'd be much appreciated.

---

### Post by jeromedavies on 2009-06-06
"http://127.0.0.1. If you see the &#8220;it works!&#8221; web page, you have Apache up and running."

Did you get the "It  Works" Message as in the instructions?

If not then the problem is with the Apache install. If you did get it then we need to look at the name resolution.

--------
Re-reading your message, it looks like Apache is running, but is not able to find any documents.

in /etc/apache2/apache2.conf 

look for ServerRoot and make sure it is pointing to a folder with your index.html (or whatever) page. See if you can access this page with 

[http://127.0.0.1/index.html](http://127.0.0.1/index.html) (or whatever page)

---

### Post by Celauran on 2009-06-06
I'd start by removing Wordpress from the equation. Let's make sure Apache is working, then add in WP later.

---

### Post by litlfrog on 2009-06-06
OK, this is interesting. ServerRoot was listed as /etc/apache2; I haven't saved any files in there. I backed up the file and tried changing Server Root to /var/www. When I try to restart apache2, I get
> apache2: Syntax error on line 285 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/sites-enabled/wordpress/index.php: /etc/apache2/sites-enabled/wordpress/index.php:1: <?php> was not closed.

I think I will uninstall wordpress and see what happens.

---

### Post by litlfrog on 2009-06-06
Except that I remembered--I haven't even gotten to the WordPress install page yet. All I've done is unzip the files into /var/www/wordpress. I'm seriously ready to throw this damned computer through the wall. Why is it so hard to just view a localhost page in apache?!

---

### Post by jeromedavies on 2009-06-06
> apache2: Syntax error on line 285 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/sites-enabled/wordpress/index.php: /etc/apache2/sites-enabled/wordpress/index.php:1: <?php> was not closed.

You will need to clean up your apache2.conf file by the look of it. 

You may find it easier to use the Wordpress install instructions rather than the ones you linked to. 

[http://codex.wordpress.org/Installing_WordPress](http://codex.wordpress.org/Installing_WordPress)

--------------------

> Why is it so hard to just view a localhost page in apache?!

Installing Apache, PHP, MySQL and Wordpress is a rather involved process. Try creating a basic HTML page called index.html and put it into the ServerRoot folder, yu can try to access this as it only depends on Apache. If you know any PHP or can find a basic script somewhere you can also put this in the Serverroot folder and try to access it. Once you have Apache and PHP running, you can check MySQL is running. Once all three of those are running OK you can install Wordpress.

---

### Post by Celauran on 2009-06-06
> **litlfrog said:**
> OK, this is interesting. ServerRoot was listed as /etc/apache2; I haven't saved any files in there. I backed up the file and tried changing Server Root to /var/www.

/var/www is the DocumentRoot, not ServerRoot. ServerRoot should be /etc/apache2.

Did you also remember to install PHP and MySQL? You'll need both for WP.

---

### Post by litlfrog on 2009-06-06
I removed, then reinstalled apache2. I noticed that my apache2.conf file remained the same after this--why would removing the program not get rid of the configuration file?--so I went in and got rid of the few changes I had made to the default apache2.conf file. I restarted apache2 without errors. When I try to navigate to [http://127.0.0.1/index.html](http://127.0.0.1/index.html), I get the message that I have chosen to open index.html which is a PHTML file, and Firefox asks what I would like to do. First time I've seen that before. Any thoughts?

---

### Post by Celauran on 2009-06-06
> **litlfrog said:**
> why would removing the program not get rid of the configuration file?
Use purge instead of remove to get rid of config files.

```
sudo aptitude purge apache2
```

As for this PHTML business, what are the contents of the file? Is it just HTML or does it also contain PHP? Do you have PHP installed?

---

### Post by litlfrog on 2009-06-06
I removed PHP earlier today, but the contents of that file are not php--it's a simple html page with nothing more than a background color and an h1 saying "It works!". I'm trying to purge to get rid of config files. I didn't know that command existed at all.

---

### Post by Celauran on 2009-06-06
purge gets rid of the config files and uninstalls. Have you tried something as simple as clearing your browser cache?

---

### Post by jeromedavies on 2009-06-06
> /var/www is the DocumentRoot, not ServerRoot.

Aaaargh. Sorry, I shouldn't post when I'm tired. (Hangs head in shame).

A couple of thoughts:

1. Do you really want to run your own version of Wordpress or do you simply want to set up a blog.

2. Normally I would install all this using the Ubuntu server install with the LAMP stack option selected, which takes a lot of the leg work out of this. Apache, MySQL and PHP are all installed as part of the base system, you just have to install Wordpress.

---

### Post by litlfrog on 2009-06-06
OK, here's what happened. I can load [http://127.0.0.1/index.html](http://127.0.0.1/index.html) just fine now after that purge. But if I try to just load 127.0.0.1 or localhost, I still get the error

> Not Found

The requested URL / was not found on this server.
Apache/2.2.11 (Ubuntu) Server at localhost Port 80

So, does that mean that apache2 is finally working since it loads that file? Or that something is borked somewhere because it doesn't load a page when I just try going to localhost in the browser?

---

### Post by Celauran on 2009-06-06
Sounds like Apache is working fine since you can access [http://localhost/index.html](http://localhost/index.html).

I suspect the remaining issue will be resolved by simply dumping your browser cache.

---

### Post by litlfrog on 2009-06-07
Okay, works so far. I then ran 
> sudo apt-get install php5 libapache2-mod-php5
and restarted apache2. Per instructions for LAMP installation [here]("http://www.supriyadisw.net/2006/12/lamp-installation-on-ubuntu"), I created a test file called testphp. It contains only the following code: 
> <?php phpinfo(); ?>
and I saved it in /var/www. When I try to navigate to [http://localhost/testphp.php](http://localhost/testphp.php), Firefox asks what it should do with the file. 

Someone asked whether I really wanted to install WordPress or only want to create a blog. I'd like to install WordPress on the machine so that I can use the content management system to quickly throw together a website. I have a good knowledge of HTML and CSS and an okay understanding of JavaScript, but have never studied server-side scripting--that's why I'm fumbling around here.

---

### Post by litlfrog on 2009-06-07
OK, after some futzing around that problem is solved. I had to run
> sudo a2enmod php5
to enable php5 apparently.

---

### Post by litlfrog on 2009-06-07
I installed php5 and mysql-server-5.0 with no apparent problems. When I try to restart apache2, I get the following error.
> 
 * Restarting web server apache2                                                Syntax error on line 7 of /etc/apache2/conf.d/phpmyadmin.conf:
Invalid command 'DirectoryIndex', perhaps misspelled or defined by a module not included in the server configuration
                                                                         [fail]
I commented out that line and apache2 restarted successfully. It still seems odd to me that just trying to load "localhost" doesn't work, but "localhost/index.html" works fine, even after flushing the browser cache, trying a different browser, and restarting the computer, but I'll see whether that makes a difference in the long run.

---

### Post by litlfrog on 2009-06-07
Again, I'm able to navigate directly to a page. I couldn't load localhost/wordpress, but COULD get to the install.php page in the browser. I got the message that wordpress had installed successfully, so I thought that I was home free!

No dice. If I try to navigate to localhost/wordpress, I still get a 404 error. Is this something as simple as needing to change the sites-enabled somehow?

---

### Post by solitaire on 2009-06-07
If you are having problems getting a LAMP server set up their is a good "Self-Contained" LAMP server called XAMPP.

[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

It's self contained and it's a matter of un-tar'ing the file to the /opt/ directory and starting it.

Everything is running so you just stick the wordpress folder into the /opt/lampp/htdocs/ directory and go you [http://localhost/wordpress/wp-admin/install](http://localhost/wordpress/wp-admin/install) (I think that's the file to start the wordpress install).

---

### Post by utnubuuser on 2009-06-07
When I install LAMP, I usually change the  000-default page in sites-enabled to ALL, (in <Directory /var/www> as in AllowOveride ALL instead of none), then restart the server.

Lullabot has an exellent Lamp>Drupal install video, and I'd guess Drupal could easily be replaced by WordPress in the tutorial.> [http://www.lullabot.com/node/289]("http://www.lullabot.com/node/289")

---

### Post by litlfrog on 2009-06-07
> **solitaire said:**
> If you are having problems getting a LAMP server set up their is a good "Self-Contained" LAMP server called XAMPP.

[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

It's self contained and it's a matter of un-tar'ing the file to the /opt/ directory and starting it.

Everything is running so you just stick the wordpress folder into the /opt/lampp/htdocs/ directory and go you [http://localhost/wordpress/wp-admin/install](http://localhost/wordpress/wp-admin/install) (I think that's the file to start the wordpress install).

That sounded really promising, but even after doing a purge of mysql-server-5.0, php5, and apache2 and restarting the computer, when I try to start XAMPP I get a message saying 
> Starting XAMPP for Linux 1.7.1...
XAMPP: Another web server daemon is already running.
XAMPP: XAMPP-MySQL is already running.
XAMPP: XAMPP-ProFTPD is already running.
XAMPP for Linux started.

apache2 is listed as not installed in Synaptic, yet after clearing the cache I still see

> Not Found

The requested URL / was not found on this server.
Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch Server at localhost Port 80

Why is apache2 reaching out from beyond the grave?

---

### Post by solitaire on 2009-06-07
Check your "systems monitor" and see if their is an apache daemon running? and double check that that no apache config files remain.

---

