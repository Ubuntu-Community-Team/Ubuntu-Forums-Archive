---
title: "Koha. Ubuntu 8.04 LTS. How?"
date: 2009-01-31
forum: General Help
---

### Post by Roasted on 2009-01-31
Can anybody direct me to a guide that'll help me install Koha on Ubuntu Hardy? I found the installations, which it's a tar.gz package, so you'd think you'd do the normal make, ./configure, etc stuff... but it doesn't work on my system. Figured I'd ask in case there was a specific way that I was missing.

---

### Post by Roasted on 2009-01-31
I'm a little confused by the installation guide. It says prior to installing Koha, I need to set up a MySQL thing... something about setting up a locale. What is that referring to?

Default installation instructions:

1. perl Makefile.PL
  (you will be prompted to answer a number of questions and you will
  need to install some Perl dependencies)
  WARNING:
  1.1 A Perl library Koha depends on, MARC::File::XML may not work with Perl
    5.10, see: [http://bugs.koha.org/cgi-bin/bugzilla/show_bug.cgi?id=2309](http://bugs.koha.org/cgi-bin/bugzilla/show_bug.cgi?id=2309)),

  1.2 recent versions of CGI::Session have caused some issues for users;
  as of this release date, we suggest downloading the CGI::Session::serialize::yaml
  tarball direct from CPAN and install it directly rather than using the cpan command

2. make
3.(optional) make test 
4. sudo make install
5. sudo ln -s /etc/koha/koha-httpd.conf /etc/apache2/sites-available/koha
  (note that the path to koha-httpd.conf may be different depending on your
  installation choices)
6. sudo a2enmod rewrite
7. sudo a2ensite koha && /etc/init.d/apache2 reload
8. sudo zebrasrv -f /etc/koha/koha-conf.xml
  (note that you will want to run Zebra in daemon mode for a production
  system)
9. Browse to [http://servername:8080/](http://servername:8080/) and answer the questions


I have Perl 5.8 installed. It was installed already. I tried to just sudo make but it didn't take... said something about the command not being valid. Any thoughts to this?

---

### Post by Jac3510 on 2009-02-11
I can give you a partial answer. I'm in the process of installing it on my own system (have a few questions myself which I'll ask elsewhere). Anyway, Josh Ferraro has a pdf you can download here:

[http://www.kohadocs.org/Installing_Koha_on_Debian_sarge.html](http://www.kohadocs.org/Installing_Koha_on_Debian_sarge.html)

It's for an older versino (2.2) and is based on Debian, but I got through the entire thing with absolutely no problems. Be sure to use that and not the .pdf version of the install guide as the cvs commands get cut off. I didn't know that and had to google the things to get the right package names :p

You'll also need Apache and MySQL. Ferarro's guide has some of that, but I'd suggest going to the Community Ubuntu Doc here to set up your LAMP:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

And, for fun, if you want to set up phpmyadmin (which gives you a graphical interface for MySQL), go here after you get your LAMP going:

[https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)

One last thing. Be sure to install Zebra if you are trying to install Koha 3.0. That's what I'm working on now. The install instructions for Ubuntu can be found at the link below, although they're giving me some problems. Anyway, this should get you going. Good luck!

[http://www.indexdata.dk/zebra/doc/installation-debian.tkl](http://www.indexdata.dk/zebra/doc/installation-debian.tkl)

---

