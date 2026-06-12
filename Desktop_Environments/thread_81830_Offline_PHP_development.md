---
title: "Offline PHP development"
date: 2005-10-25
forum: Desktop Environments
---

### Post by dizzy1234 on 2005-10-25
Hi folks,

I've got Ubuntu installed on my laptop and I want to be able to use it to develop PHP whether it's online or not.

When my machine online, I can write the code and upload files to a remote server I have access to and check the code works and does what it says. However, when I'm offline, I can write the code as usual but I can't (or possibly just don't know how to) check it when I can't upload it to the server.

Can anyone suggest a way to do this?

Cheers
Nick

---

### Post by mgor on 2005-10-25
install apache and php locally on your computer.
```
sudo apt-get install apache2
```
install the php module and php extensions
```
sudo apt-get install libapache2-mod-php5 php5 php5-cli php5-gd php5-ftp php5-mbstring
```
and if you want mysql
```
sudo apt-get install mysql-server php5-mysql
```
...and you should be set to run your scripts locally :)

---

### Post by MadMan2k on 2005-10-25
not yet - you will have to place them in /var/www or configure another directory first.

---

### Post by mgor on 2005-10-25
oh, easiest would be to uncomment the following lines in /etc/apache2/apache2.conf:
```
UserDir public_html
UserDir disabled root

<Directory /home/*/public_html>
        AllowOverride FileInfo AuthConfig Limit
        Options Indexes SymLinksIfOwnerMatch IncludesNoExec
</Directory>

```

restart apache
```
sudo /etc/init.d/apache2 restart
```

and create ~/public_html
```
mkdir ~/public_html
```

if you get any access denied when trying to access [http://localhost/~user/](http://localhost/~user/) run
```
sudo chmod 751 /home/user
```

then place the PHP-scripts in ~/public_html and you'll be able to access them through [http://localhost/~user/](http://localhost/~user/)

---

### Post by dizzy1234 on 2005-10-25
Sorry to be a pain, but my computer is having trouble finding two of the packages you suggested installing, namely:

php5-ftp
php5-mbstring

Do I definitely need these two? I have a load of other PHP modules that I can install, according to synaptic package manager, but not those two. Which library are they supposed to be in?

Nick

---

### Post by mgor on 2005-10-25
ah, they might be included in the main php5 package. check phpinfo() to see what's supported. mbstring is for handeling multibyte strings, phpmyadmin requires it to work properly. ftp is support for the ftp-functions.

---

### Post by dizzy1234 on 2005-10-25
Slightly offtopic, but speaking of PHPMyAdmin, there's a package in synaptic called Eskuel which claims to be like PHPMyAdmin, but better. Any idea what this package is like?

---

### Post by dizzy1234 on 2005-10-25
Just to let you know, you rock. Got it working now thanks!!!

---

### Post by mgor on 2005-10-25
[QUOTE=dizzy1234]Slightly offtopic, but speaking of PHPMyAdmin, there's a package in synaptic called Eskuel which claims to be like PHPMyAdmin, but better. Any idea what this package is like?[/QUOTE]

haven't heard of eskuel. i've been using phpmyadmin for ever :-) it does everything i need it to do.

glad' i could help

---

