---
title: "Freespire apt-get"
date: 2007-07-29
forum: Debian
---

### Post by Blade14228 on 2007-07-29
Hello...
I am using Freespire currently (I gave up on Ubuntu for a bit...) and I am using apt-get for sql. I want to download this but the problem is that I am getting the error:

Package mysql is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mysql has no installation candidate

From what I hear Ubuntu can get sql, so why can't freespire? Will php work? (You have to install mysql first)

( I am trying to register for the freespire forums, I can't get the activation email and can't sign-in, temp post here...)

Keith

---

### Post by Pobega on 2007-07-30
What is the package you are trying to install? According to my Debian install the package for MySQL is called *mysql-server* or *mysql-server-5.0*. Also, the easiest way to install everything you need is one command:

*apt-get install apache2 libapache2-mod-php5 phpmyadmin mysql-server*

That should set up everything you need, and all you have to do now is edit the configuration files in the /etc directory. But I'm not sure if this works the same for Freespire.

---

### Post by jaygreentree on 2007-09-27
> **Pobega said:**
> What is the package you are trying to install? According to my Debian install the package for MySQL is called *mysql-server* or *mysql-server-5.0*. Also, the easiest way to install everything you need is one command:

*apt-get install apache2 libapache2-mod-php5 phpmyadmin mysql-server*

That should set up everything you need, and all you have to do now is edit the configuration files in the /etc directory. But I'm not sure if this works the same for Freespire.

I am using freespire 2.0 and I can't get apache either. I get the same error as above. I am attempting from root on SSH.

---

