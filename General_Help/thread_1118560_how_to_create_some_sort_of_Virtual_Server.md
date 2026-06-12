---
title: "how to create some sort of Virtual Server"
date: 2009-04-07
forum: General Help
---

### Post by happinesskills on 2009-04-07
I am a web developer & I need some sort of Virtual Server so I can test server-side coding languages like PHP.

For example, I could type file:///home/name/sites/index.php into firefox & be able to read & use the php file instead of a download window popping up.

PS: I would obviously need MySQL & PHP4 or 5

---

### Post by dgoosens on 2009-04-07
either you install everything like described here:
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

either you install Xampp
[http://www.apachefriends.org/en/xampp-linux.html#377]("http://www.apachefriends.org/en/xampp-linux.html#377")

rather easy actually...

---

### Post by lovinglinux on 2009-04-07
Xampp is pretty simple to install, configure and use for web development. It's not recommended for real server tho.

Take a look at [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

---

### Post by happinesskills on 2009-04-07
I don't need for a real server. I just need to be able to test my websites & read my PHP files.

I'll try all your options.

---

### Post by happinesskills on 2009-04-07
Ok. got Xampp installed & running, but I can't put anything into the /htdocs folder for testing. I can't even make a folder.

---

### Post by mb_webguy on 2009-04-07
In order for PHP files to be interpreted, you have to have a webserver running a PHP interpreter.  Just install LAMP with Synaptic and be done with it.  (In Synaptic, select Edit->Select packages by task, check LAMP Server, then OK and Apply.)  Your html and php files should go in the /var/www directory.

EDIT:  I didn't see your most recent post before I posted.  If Xampp is like Apache, the web root directory isn't writable by a normal user.  Either you need to edit and save files as root using something like "gksu gedit", or you need to change the permissions on the web root directory to allow your account write access.

---

