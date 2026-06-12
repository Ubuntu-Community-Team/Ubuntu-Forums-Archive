---
title: "Ubuntu as a Server Environment for PHP/SQL deving?"
date: 2009-03-18
forum: General Help
---

### Post by jAuriya on 2009-03-18
Hello Everyone!

My name's Jonathan and I've been a windows user for as far as I've been on computers. And two years ago got a Macbook running OSX which I'm to date still in love with.

But for me, Windows nor OSX has been an awesome platform to develop PHP/SQL in as I always needed to get additional software to get things done. (Small example; mail() function is a pain in the *** to get working on XAMPP on Windows..)

So I'm gonna make a switch to Ubuntu, but ofcourse before I made the switch I wanted some advice from the pro's on this forum! :) 

I'm developing sites and scripts using HTML, PHP and MySQL (and sometimes additional Javascript and Ajax.)

If I install Ubuntu, will it be an easy environment to test Scripts on as if it was a real server environment?
How about Cron Jobs? Any way to get that working in Ubuntu as well?

To be honest as I always provide people with scripts when they ask me, I'm used to work in a Cpanel environment as well..Does Ubuntu also support installations of such to be used as if I'm in a server environment?

Also, I looked at Ubuntu Server, but am not sure if this is what I need.

I really hope that this switch will be awesome and smooth, cause after a few years I really want to settle on an OS to develop on, and the first two kinda failed me PHP/SQL wise.

(The other two for me, have been great for game developing though, my main profession.)

(Also, side note: My current machine I work on has a AMD Sempron 3000+ 1.8Ghz processor, 512MB-Ram and an ATI-Radeon 200M Xpress Graphics Card, just in case I thought I'd include this info.)

Hoping to hear good news,
Jonathan

---

### Post by zigx on 2009-03-18
Ubuntu desktop will work fine...

when you deploy to a Real server u might want to consider ubuntu sever for that, but if you want to work on your computer and do dev on it i think Ubuntu desktop is perfect.

Installing stuff like php, and mysql is super easy.
just a matter of sudo apt-get whatever-you-want 

you could use something like webmin or the ubuntu preferred ebox ([http://ebox-platform.com/product/screenshots/](http://ebox-platform.com/product/screenshots/)) to manage stuff graphically but ive found that the command line is so much faster.

if you run into probs you might want to jump into #ubuntu or #ubuntu-server on irc.freenode.net 

really great people in there

---

### Post by jAuriya on 2009-03-18
Hey!

Very nice, thanks for the swift reply! Now I have no doubts at all about switching my PHP/SQL environment over to Ubuntu. :)

Thank you very much and I'll be definately paying the IRC's a visit.

Thanks for the links as well! :D

---

### Post by mb_webguy on 2009-03-18
It's extremely easy to setup your Ubuntu system to use PHP and MySQL.

Open Synaptic.  Go to Edit->Mark Packages By Task. Check LAMP Server, and click OK.  Now click the Apply button.  This will install the Apache webserver, PHP, and MySQL.  The default web root (i.e. where you put your php and html files) is the /var/www directory.  You can change this by editing /etc/apache2/sites-available/default and changing every instance of "/var/www/" to the new directory path.

The default data directory for MySQL is /var/lib/mysql.  [Changing this]("http://ubuntuforums.org/showpost.php?p=5640983&postcount=1") is only slightly more difficult than changing the Apache web directory.

---

