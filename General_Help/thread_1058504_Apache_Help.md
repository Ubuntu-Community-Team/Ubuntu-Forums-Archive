---
title: "Apache Help"
date: 2009-02-02
forum: General Help
---

### Post by KuroYoma on 2009-02-02
I am just starting with Apache and I want to start my own website.  Where would be the best place to start and where would the best place to begin my learning adventure.  I love linux and Apache is my weak point for now.  If you know of any other good website, HTML software for linux I would love any suggestions.

---

### Post by cmnorton on 2009-02-03
First, start by learning how /etc/apache2/apache2.conf works, not all at once, but things like DocumentRoot and how to share multiple applications from just port 80. 

You can also download Quanta Plus, which is free and open source.

Learning PHP and Javascript might also  be helpful. You are not going to do all this at once. You can display a web page with some very basic skills. I am listing out a direction you might consider taking.

---

### Post by chiefbutz on 2009-02-03
If you are new to making websites I suggest starting here:
[http://www.w3schools.com/html/DEFAULT.asp](http://www.w3schools.com/html/DEFAULT.asp)

Also, any webpages you make will need to be put into /var/www since I assume you haven't messed with Apache's configuration much.

Knowing a little bit of basic HTML is always a good thing even if you plan to use a WYSIWYG Editor all the time.

---

### Post by sedawk on 2009-02-03
There are two very different things:

a) Creating (good) web content

b) Running a web server

To create and view good content you do not need a web server running.
You store the web content to your local disk (e.g html files) and
open it by using the "Open File" dialog of your browser.
Then, when you think you have created a good web site you can bother
about publishing it.
(Okay, some advanced stuff needs a web server to work ...)
Keep in mind that setting up your own server, either in your basement
(bad upload speed!) or by renting a server is lots of work and
needs maintenance 24/7.
It might be easier to simple upload your content to an already running
web server where you rent some web space and someone else takes
care the system is running 24/7, has a backup, etc.

---

### Post by Coreigh on 2009-02-03
W3schools is a wealth of knowledge but I find it overwhelming. I found Webmonkey ([http://www.webmonkey.com/](http://www.webmonkey.com/)) to be a friendlier introduction, at all levels.

I also have to strongly agree with 'cmnorton' that it is very important to know how to use Apache. Your websites won't do what you want them to if you don't know how to operate your server. Apache, PHP, and MySQL are all very worth knowing and though they can get complicated are easy to get in to.

---

### Post by sloggerkhan on 2009-02-03
To start with apache, just install apache2 package from the repos. If you want to do mysql and php stuff, install appropriate packages to go with.

You can find tutorials all over the place. Most of running a webserver is just installing some packages once and setting up some permissions. Maybe you change 1 or 2 things in a config file. It's pretty anticlamactic.
However, making websites is a huge can of worms.

---

### Post by Iowan on 2009-02-03
[Here]("https://help.ubuntu.com/community/ApacheMySQLPHP") is a starting point.

---

### Post by KuroYoma on 2009-02-04
Thank You so much for all of you input.  I am going to start on the wesite first and then set up a server later.  I was wondering since I want to set up all my own server and stuff if I should use pure Apache or if I should try out LAMP because I here lots of good things about it.  Or am I mistaken?

---

### Post by sloggerkhan on 2009-02-05
I recomend learning something that goes beyond xhtml/css...
Without having some sort of database/formatting system, you can't really make interactive websites. 
Linux, Apache, mySQL, and something, be it PHP, Python, Ruby, Perl, or something else.
Lately I've been liking the look of Python/Django.

---

