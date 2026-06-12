---
title: "Getting PHP files to parse"
date: 2008-12-09
forum: General Help
---

### Post by sum janus on 2008-12-09
Hi all,

I have a question on installing PHP.  I've installed PHP and Apache, but when I point Firefox towards a PHP file, it asks me if I'd like to open the file or save it - the same drill that happens when I download something.

Obviously this is not what I want... how do I go about getting PHP files to parse?

Thanks.

---

### Post by scott_g on 2008-12-09
Are you putting the PHP file in the web directory (/var/www)?  Do you have the apache-php module installed (libapache2-mod-php5 in my case....)?

Scott

---

### Post by LoneWolfJack on 2008-12-09
you can't just open php files, even through your browser.

you'll have to point firefox to your local server:
```
127.0.0.1/<your webroot path>/index.php
```

---

### Post by scott_g on 2008-12-09
So you'll have to open:
```
http://localhost/<filename.php>
```

in Firefox, assuming <filename.php> is located in your web-root directory (/var/www) by default.

---

### Post by sum janus on 2008-12-10
Right.  That's what I'm trying, and it asks me if I'd like to open / save.

I have pointed Firefox to:

```

http://localhost/

```

And gotten the "It works!" message.

...

But this brings up another interesting question - how can I get it so that if I have, say, a php file on my desktop I can view that, without putting into the /var/www directory?

---

### Post by scott_g on 2008-12-10
Can you double check that you have the following (or equivalent) packages installed:

libapache2-mod-php5
php5
apache2

If worst comes to worst, try installing phpmyadmin through the package manager (sudo apt-get install phpmyadmin), as it will install all the dependencies for a webserver.

To parse a php file thats on your desktop, you'll either need to point the root of your webdirectory to your desktop, or find a program that will debug your php file using the php libraries (phpdesigner2007 will do this in windows, not sure of the Ubuntu equivalent...)

Might want to make sure that your apache config file has the .php extension listed in it... not sure where the cong file is anymore though; I'd do a google search on it.  Should be a section of the config file that lists index.html, index.php, etc...

Scott

---

