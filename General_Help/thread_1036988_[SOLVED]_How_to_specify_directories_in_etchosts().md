---
title: "[SOLVED] How to specify directories in /etc/hosts(?)"
date: 2009-01-11
forum: General Help
---

### Post by supergrover1981 on 2009-01-11
Hi gang,

I'm trying to locally test a site that uses $_SERVER["SERVER_NAME"] to interpret which information to send. I didn't write the site, but I need to make some simple tweaks to the CSS.

I've been told to use Linux's /etc/hosts file redirect [www.websitename](www.websitename) to localhost. The problem is, I can't afford to store the site at [http://localhost/](http://localhost/) or [http://127.0.0.1/](http://127.0.0.1/) - there are a bunch of other sites I need quick access to. When I try to add

[http://127.0.0.1/websitename](http://127.0.0.1/websitename) [www.websitename.com](www.websitename.com)

to my etc/hosts file, it seems to ignore the line.

Any suggestions? Is there a way to specify directories in /etc/hosts, or any other way to solve this problem?

Ubuntu 8.10, Apache 2.2

Any suggestions most appreciated.

Cheers,
       - SuperGrover

---

### Post by capscrew on 2009-01-11
The /etc/hosts file is for mapping hostname to IP address only.

---

### Post by cariboo on 2009-01-11
If you don't have the sapce to store the web site in /var/www, for testing purposes place the site in a directory and use a symlink to link it to /var/www eg:

```
sudo ln -s /home/<user>/website /var/www/website
```

You can then access the site by entering:

```
http://localhost/website
```

in Firefox's address bar.

Jim

---

### Post by KeyserSoze93 on 2009-01-11
The best solution would be the set up Apache to serve this second site from a different IP...

To give you computer a second IP, run:
```
sudo ifconfig eth0:1 0.0.0.0
```, where 0.0.0.0 is the new IP you want (maybe one above your current?)

Then configure apache with a virtual host (so your current site is served from your normal IP, and your second site is served from the new IP). See: [http://httpd.apache.org/docs/1.3/vhosts/ip-based.html](http://httpd.apache.org/docs/1.3/vhosts/ip-based.html)

Finally, set up /etc/hosts to redirect to your other virtual host, IE
```
0.0.0.0 websitename.com
```, where 0.0.0.0 is the second IP you set up.

Virtual hosts in apache sound complicated but it's very easy once you get the idea. Just remember you will need to run the ifconfig command every time you reboot (or add it to /etc/rc.local), if you want your second IP.

---

### Post by supergrover1981 on 2009-01-12
Cheers Keyser, much appreciated.

(The greatest trick you ever pulled was...teaching me how to set up a VirtualHost)

- SuperGrover

---

