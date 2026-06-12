---
title: "DokuWiki install not working"
date: 2005-11-18
forum: Desktop Environments
---

### Post by Sendervictorius on 2005-11-18
Hi,

I'm having trouble getting DocuWiki to run. According to the instructions ([http://wiki.splitbrain.org/wiki:install#debian_gnu_linux_ubuntu_linux](http://wiki.splitbrain.org/wiki:install#debian_gnu_linux_ubuntu_linux) ) it should just work out of the box.

I installed DokuWiki direct from Synaptic, along with PHP and Apache all at the same time. I answered the debconf qusetions - without altering the defaults (The default document root is /dokuwiki)

I should now just be able to start from my browser [http://localhost/dokuwiki](http://localhost/dokuwiki) - but I get a 404. Apache is going ok.

Am I supposed to see /var/www/dokuwiki ?

Has anyone had success installing this package on breezy?

---

### Post by l.tambiah on 2005-11-18
Hello,

I have installed *Docuwiki* on my local machine and on a live host without any problems. In terms of your localhost, you should store it in " /var/www/ " as you said. I take it you have apache, mysql and php installed?

If you type "http://localhost" into your browser you should see your "/var/www/" directory. Do you see this?

Now test php:

Add a file called "test.php" to your "/var/www". The file should contain the following text:

```
[COLOR=DarkGreen]<?php phpinfo(); ?>[/COLOR]
``` 

Now open your browser and goto "http://localhost" and select the "test.php" file you should now see a screen with all your setups. Do you see this? If you dont something is wrong with your setup.

Let me know how you get on with the above and we will take it from there to get you up and running.

---

### Post by Sendervictorius on 2005-11-18
Thanks for you help.

I followed your instructions, and all seems OK. The php info page is displaying a comprehensive list of stuff.

I don't have mysql installed. I was under the impression that Dokuwiki only needed apache and php?

The install has put nothing in /var/www/ - should it?

- Andrew

---

### Post by l.tambiah on 2005-11-19
I installed DokuWiki manually not with apt-get. You dont require mysql for Dokuwiki, it uses text files to store information.

I downloaded the dokuwiki latest stable release from: 

[http://www.splitbrain.org/Programming/PHP/DokuWiki/index.php]("http://www.splitbrain.org/Programming/PHP/DokuWiki/index.php")

Open a terminal and do the following commands:
```

$ cd /var/www
$ tar -xzvf /path/to/your/download/dokuwiki-YYYY-MM-DD.tgz

``` You should now see your terminal extract the files from the compressed package.

Do a *list* command to confirm your new directory now exists:

```
$ ls
``` 
In the list you should see a directory named "*dokuwiki-YYYY-MM-DD*"

You can rename the directory, lets call it *wiki*:

**Rename** the directory:

```
$ mv dokuwiki-YYYY-MM-DD wiki
``` 
Finally we create a changes.log file which is required for Dokuwiki to function.

Using the "*touch*" command we willl create an empty file called "*changes.log*"

```
$ touch wiki/data/changes.log
``` 
Now go to you browser and go to your localhost at "http://localhost". Now Select the wiki folder from your browser and you should see a screen with an attempt to load dokuwiki. You may have some permission errors on the screen this can be corrected by giving permission to the files that require access. The errors on the screen shows you what files are affected.

To change the permissions, using the file manager goto the directory or file concerned and right click on the file (or directory) and select properties. Then Select the permission tab and tick all read, write and execute checkboxes. 

When you have gave permission for the required files your wiki should work.

Also this page will be of help you:

[http://wiki.splitbrain.org/wiki%3AInstall]("http://wiki.splitbrain.org/wiki%3AInstall")

Hope this helps....if you have any difficult please ask again..

---

### Post by Sendervictorius on 2005-11-20
It works like a charm. Thank you so much! :) 

I conclude from all this that the docuwiki apt-get install in breezy is broken. Maybe someone who knows what it is supposed to do will take a look and fix it. :(

---

### Post by nesman89 on 2006-02-08
alright i installed dokuwiki just as you have explained however when i go to the browser and type in [http://localhost/dokuwiki](http://localhost/dokuwiki) it states that i'm trying to open a phtml file.

i do not know what to do.  any help would be appreciated.


thanks.

---

### Post by l.tambiah on 2006-02-09
I have never came across this issue so I'm not totally sure. But we will get to the bottom of it somehow ;-). It could possibly be a problem with the Apache, and the PHP set up. 

My second post has a little test you could try. When you have tried this let me know that you get a screen with your setup information (i take it you have done this, but i need to be confirmed if you have). 

Apologies for being a bit late on the reply its been a bit hectic of late...

If you have any progress on your issue please let me know, but more importantly post your fix so you help others that may encounter the same issue.

Regards

L. Tambiah

---

### Post by Vaxis on 2006-02-12
Hi all,

I don't know if the Ubuntu package for DokuWiki may be called broken, since it is actually works.

I use Apache 2 and the only thing that you have to do in order to make DokuWiki work after you've installed it with Synaptic is making a symbolic link of the DokuWiki snippet in apache2/conf.d, i.e. type on a root console:
```
ln -s /etc/dokuwiki/apache.conf /etc/apache2/conf.d/dokuwiki.conf
```

That's it! Have fun DokuWiki'ing ;)

---

### Post by Sendervictorius on 2006-02-14
Well, shouldn't the package install the symbolic link too?

---

