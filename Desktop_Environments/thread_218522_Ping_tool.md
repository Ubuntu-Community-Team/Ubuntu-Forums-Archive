---
title: "Ping tool ?"
date: 2006-07-18
forum: Desktop Environments
---

### Post by petef on 2006-07-18
Hi guys, we currently run a variety of servers/routers, windows, Ubuntu, Solaris etc. I am after a tool to ping these servers (30 in total abou 50 routers) and display on an apache page or send me an email if something is down what can you recommend ??

Thanks in advance

Pete

---

### Post by Jagot on 2006-07-18
Will the ping command from Terminal not work?  Or the Ping tool in Networking in System -> Admin (I think)?

---

### Post by reclusivemonkey on 2006-07-18
> **petef said:**
> Hi guys, we currently run a variety of servers/routers, windows, Ubuntu, Solaris etc. I am after a tool to ping these servers (30 in total abou 50 routers) and display on an apache page or send me an email if something is down what can you recommend ??

Thanks in advance

Pete

Waaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaay overkill from your post, but I thought I would link you anyway, because once you see it, you might want it;

[http://www.nagios.org/](http://www.nagios.org/)

Some screenshots to give you an idea;

[http://www.nagios.org/about/screenshots.php](http://www.nagios.org/about/screenshots.php)

Caveat: I installed this on Slackware for a friend's company, not sure how it would go with Ubuntu...

Edit: It seems its in the repos, so you could see how it goes.

---

### Post by tturrisi on 2006-07-18
You could use a php script on one of your servers that does all that you want done and then emails the results to you or creates/saves a web page or populates a database with the results.  php is probably the easiest method of doing what you want.

---

### Post by tturrisi on 2006-07-18
here's a free php script that will do what you want:
[http://www.hotscripts.com/Detailed/54254.html](http://www.hotscripts.com/Detailed/54254.html)

---

