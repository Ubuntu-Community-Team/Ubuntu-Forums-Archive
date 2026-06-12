---
title: "Where were Apache and MySQL installed?"
date: 2008-12-06
forum: General Help
---

### Post by clay7 on 2008-12-06
Hello everyone. I'm very excited to be using Linux and Ubuntu! I know tons of stuff in Windows, but almost nothing in Ubuntu. 

I used Synaptic to download and install Apache2, MySql5, and PHP. Synaptic said they were installed, and I see these names in folders like /usr, but:

1. Where are these programs?
2. How do I run them? 

In Windows I'd go to Start, Programs, MySql. None of these apps show up under the Applications Menu. This is important to me because I am a PHP developer and I want to start doing things in Ubuntu.

I'm running Ubuntu 8.10 on a box with 2 hard drives: one for XP and one for Ubuntu. 

Thanks in advance,
Clay

---

### Post by 3rdalbum on 2008-12-06
You have to start your database server manually in Windows? How uncivilised!

Apache, PHP and MySQL start automatically when the computer boots up. If you put some files into /var/www and go to [http://localhost](http://localhost), you'll see them there already.

I believe Ubuntu's packages for those programs actually automatically set them up to work with eachother too? In any case, just try putting a PHP script into /var/www and see what happens.

---

### Post by ngothean on 2008-12-06
If you want to know where they are, try this in a terminal (to open a terminal, click on Application/Accessories/Terminal, a terminal, or a shell is open just like cmd in Windows) 

which mysql 

to see where is mysql 
The same for php, apache ...
Typically, the result will be 

/usr/bin/mysql 

Basically, Linux is not Windows. It's cool, but it's different. For example, you don't expect to just clic to launch mysql and then clic again on Help to be guided through. You really need to spend some time going through a tutorial to start with mysql ... The same with PHP, Apache

Good luck

---

### Post by clay7 on 2008-12-06
All I had in the www folder was an index.html. It only said "It works!" 

I did a search for the folder "phpmyadmin" and all of these locations have a phpmyadmin folder:

/etc
/usr/share
/usr/share/doc
/var/lib

So, which one do I use? Also, I tried to edit a config file and I got a message saying that I did not have permission. I'm the only person on this computer and installed Ubuntu only a few hours ago. How do I not have permission?

Thanks!

---

### Post by sensez on 2008-12-06
> **clay7 said:**
> Hello everyone. I'm very excited to be using Linux and Ubuntu! I know tons of stuff in Windows, but almost nothing in Ubuntu. 

I used Synaptic to download and install Apache2, MySql5, and PHP. Synaptic said they were installed, and I see these names in folders like /usr, but:

1. Where are these programs?
2. How do I run them? 

In Windows I'd go to Start, Programs, MySql. None of these apps show up under the Applications Menu. This is important to me because I am a PHP developer and I want to start doing things in Ubuntu.

I'm running Ubuntu 8.10 on a box with 2 hard drives: one for XP and one for Ubuntu. 

Thanks in advance,
Clay
Q1: you can use dpkg to see what and where file in the package. Example:

[COLOR="Blue"]dpkg -S apache2[/COLOR]

Q2: You can find some script in /etc/init.d/ to start or stop this service. Some thing like:

[COLOR="Blue"]sudo /etc/init.d/apache2 start[/COLOR]
[COLOR="Blue"]sudo /etc/init.d/apache2 stop[/COLOR]

    In run level 2, looking the file in /etc/rc2.d/. Used "S" start is the services to autostart in this level. Change "S" to "K" can set this service do not autostart.

---

### Post by clay7 on 2008-12-06
ok - great! What you said works!

The only thing that I now have trouble with is phpMyAdmin, as noted above. Can anyone help me with this?

---

### Post by unutbu on 2008-12-06
To get phpmyadmin to work with apache2, try this:
[http://ubuntuforums.org/showpost.php?p=6046408&postcount=8](http://ubuntuforums.org/showpost.php?p=6046408&postcount=8)

---

### Post by clay7 on 2008-12-06
I'm showing my newness here...I went and added that line to apache.conf but when I tried to save it, I got this error message:

Could not save the file /etc/phpmyadmin/apache.conf.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again

How do I not have permission? I just installed 8.10 a few hours ago and I'm the only one on this box.

Thanks!

---

### Post by unutbu on 2008-12-06
You need root (admin) privileges to edit /etc/apache2/apache2.conf.
To do so, open a terminal (Applications>Accessories>Terminal), and
type
```

gksu gedit /etc/apache2/apache2.conf
```

For an explanation of Ubuntu's root and sudo system for administration and security, see

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

