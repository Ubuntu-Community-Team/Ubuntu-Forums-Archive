---
title: "Newie help needed - very confused with php"
date: 2009-06-17
forum: General Help
---

### Post by albertramsbottom3 on 2009-06-17
Hi

I am a newbie with Ubuntu and im having a lot of greif and im very confused with the structure of php in Ubuntu.

Basically I am running Moodle and need the PHP_radius Extension installed so \i can use Radius as my authentication method.

I installed the LAMP package during the installation of Ubuntu but I now find that there is several php folders with several php.ini's etc.

I have also installed the Pear package manager and installed the auth_radius package (which I assume is the php_radius extension), that Moodle is asking for.

I can only assume that I need to enable the auth_radius extension in my php.ini file (somehow, not sure?), but I have several php.inis

Here is what I got:

/etc/php5 - 3 items - apache2, cli and conf.d folders with a php.ini in both Apache2 and the CLI folders.

/usr/lib - 3 items - 20060613, ext and Libexce - nothing except some extensions for mysql

usr/share/php - loads of files including Pear and Auth direcories.  The auth directory has a radius.php file in it.

/usr/share/php5 with more php.ini and php.ini-dist in it

Very confused.

Any ideas would be great

Many thanks
:(

---

### Post by Celauran on 2009-06-17
> **albertramsbottom3 said:**
> 
Here is what I got:

/etc/php5 - 3 items - apache2, cli and conf.d folders with a php.ini in both Apache2 and the CLI folders.

Apache2 is for the web server, cli is for running php from the command line. The one you're looking for is in /etc/php5/apache2

---

