---
title: "help me to  configure PHP"
date: 2008-12-24
forum: General Help
---

### Post by brijith on 2008-12-24
Hello friends,

Can any one help me to configure PHP in my debian System I installed php5 but when I try to get a **phpmyadmin** a download window popup as in the attached snap shot. You can also have a look at what all things I have installed related to **PHP & phpmyadmin** from the second snap shot


**[COLOR="DarkOrange"]Thanks[/COLOR]**

---

### Post by Xiong Chiamiov on 2008-12-24
You need to tell apache to use PHP to parse .phtml files.  In your httpd.conf (don't know where it is? run "locate httpd.conf"), there should be a line something like
```

AddHandler php5-script php

```
Add phtml to the end of that line and save it.

---

### Post by Haiyadragon on 2008-12-24
I think you need php5 for apache2:

```
sudo apt-get install libapache2-mod-php5
```

---

### Post by Xiong Chiamiov on 2008-12-24
> **Haiyadragon said:**
> I think you need php5 for apache2:

```
sudo apt-get install libapache2-mod-php5
```
He has it installed already, as shown in the 2nd screenshot.

OP:
As a second thought, have you gotten apache to parse normal .php files?  You can just write a simple one and stick it in the htdocs root.
```

<?php
echo phpinfo();
?>

```
Then you know whether it is the extension, or PHP itself, that you are having problems with.

---

### Post by hyper_ch on 2008-12-24
```

sudo a2enmod php5

```

---

### Post by brijith on 2008-12-24
> **hyper_ch said:**
> ```

sudo a2enmod php5

```

I Got this 
```

debian117:/var/www# a2enmod php5
This module does not exist!
```

friends Problem persists,

When I checked for the httpd.conf I found it in 

```
/etc/apache2/httpd.conf
```

But the file is empty

I could find another file 

```
/etc/apache2/apache2.conf
```


In this file I added the line 

```
AddHandler php5-script php phtml 
```

And restarted apache 

but the problem persists

---

### Post by hyper_ch on 2008-12-24
libapache2-mod-php5 is NOT installed, you installed the apache 1.3 mod

---

### Post by brijith on 2008-12-24
> **hyper_ch said:**
> libapache2-mod-php5 is NOT installed, you installed the apache 1.3 mod


Now phpinfo() works But phpmyadmin doesn't. Please  see the screen shot attached.


Also When I tried 

```
debian117:/home/brijith# a2enmod php5
This module is already enabled!


```

it was successful

---

### Post by Haiyadragon on 2008-12-25
Try clearing your browser's cache.

---

### Post by brijith on 2008-12-25
> **Haiyadragon said:**
> Try clearing your browser's cache.


now I gets this message in browser

```
Wrong permissions on configuration file, should not be world writable!

```

---

### Post by hyper_ch on 2008-12-26
and what could that mean?

---

### Post by Haiyadragon on 2008-12-26
You need to reset permissions on the phpmyadmin config file. Find the file 'config.inc.php' and run chmod on it:


```
sudo chmod 644 config.inc.php
```


Where config.inc.php is the full path to that file.

---

