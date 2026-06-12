---
title: "apt-get install anything blocked by webserver?"
date: 2009-03-28
forum: General Help
---

### Post by mr.miles on 2009-03-28
This is a fairly long post, with attempts by others to help, about trying to 

apt-get install something

without seeing this:

httpd (no pid file) not running
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
  ...fail!
invoke-rc.d: initscript apache2, action "restart" failed.
dpkg: error processing textpattern (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 textpattern
E: Sub-process /usr/bin/dpkg returned an error code (1)


Forwarded conversation
Subject: [help request] apt-get blocked by apache?
------------------------

Hi,

I'm trying to get rid of the 'textpattern' package so that I can use
apt-get normally again on ubuntu 8.04LTS but I think I messed up
apache while installing textpattern and that is preventing it. I would
be thankful for any help.

While trying to install textpattern I also installed the packages
mysql-server (partly) and lighttpd.

here's what happens when I try to install something:

mrmiles@kms_d:/etc/init.d$ sudo apt-get install avrdude
[sudo] password for mrmiles:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
 avrdude-doc
The following packages will be REMOVED:
 textpattern
The following NEW packages will be installed:
 avrdude
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/163kB of archives.
After this operation, 733kB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 154283 files and directories currently installed.)
Removing textpattern ...
 * Restarting web server apache2
httpd (no pid file) not running
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
  ...fail!
invoke-rc.d: initscript apache2, action "restart" failed.
dpkg: error processing textpattern (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 textpattern
E: Sub-process /usr/bin/dpkg returned an error code (1)

----------

Is it possible that you have lighttpd running and using port 80 so apache can't bind to that port?

This thread my be of use to you too:

[http://www.linuxquestions.org/questions/linux-software-2/98address-already-in-use-makesock-could-not-bind-to-address-0.0.0.0443-110753/](http://www.linuxquestions.org/questions/linux-software-2/98address-already-in-use-makesock-could-not-bind-to-address-0.0.0.0443-110753/)

----------

Are you sure nothing else is already running and occupying port 80?
`sudo netstat -antp` may provide clues.

----------

Can you start (or restart) apache by itself? 

You may also want to check /var/log/messages to see if it is giving you anymore useful information.

----------


I am rather partial to lsof but it isn't always installed.

# sudo lsof -i :http


----------

Hi,
(snip)
 Maybe you set textparttern package uses apache2 package as httpd,
 not lighttpd. Does apache2 run and listen port 80?

----------

Thanks to everyone who responded.
I'm still not sure what's going on, but the error message from dpkg
has changed. It looks like textpattern is configured to use apache2
and lighttpd? Anyhow, I'd just like to make dpkg useable again.

I've got boa, apache2 and lighttpd installed, and I can start and stop
all of them. When I go to 'localhost' I can see an 'It works!' page.
When I stop all three  with eg.
/etc/init.d/lighttpd stop
 then (sometimes?) the page is no longer found.
Also fiddling with
/etc/init.d/<servername> stop
changed the output of netstat and lsof but  dpkg hasn't stopped showing errors.


(earlier)
mrmiles@kms_d:~$ sudo netstat -A inet -lnp
[sudo] password for mrmiles:
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address
State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*
LISTEN      5173/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*
LISTEN      5313/smbd
tcp        0      0 0.0.0.0:80              0.0.0.0:*
LISTEN      5255/boa
tcp        0      0 127.0.0.1:631           0.0.0.0:*
LISTEN      5095/cupsd
tcp        0      0 0.0.0.0:445             0.0.0.0:*
LISTEN      5313/smbd
udp        0      0 192.168.0.16:137        0.0.0.0:*
        5311/nmbd
udp        0      0 0.0.0.0:137             0.0.0.0:*
        5311/nmbd
udp        0      0 192.168.0.16:138        0.0.0.0:*
        5311/nmbd
udp        0      0 0.0.0.0:138             0.0.0.0:*
        5311/nmbd
udp        0      0 0.0.0.0:33328           0.0.0.0:*
        5052/avahi-daemon:
udp        0      0 0.0.0.0:68              0.0.0.0:*
        5695/dhclient
udp        0      0 0.0.0.0:5353            0.0.0.0:*
        5052/avahi-daemon:

mrmiles@kms_d:/etc/init.d$ sudo netstat -antp
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address
State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*
LISTEN      5173/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*
LISTEN      5313/smbd
tcp        0      0 0.0.0.0:80              0.0.0.0:*
LISTEN      5255/boa
tcp        0      0 127.0.0.1:631           0.0.0.0:*
LISTEN      5095/cupsd
tcp        0      0 0.0.0.0:445             0.0.0.0:*
LISTEN      5313/smbd
tcp        0      0 192.168.0.16:60167      66.249.89.18:80
ESTABLISHED 6170/firefox
tcp        0      0 192.168.0.16:60165      66.249.89.18:80
ESTABLISHED 6170/firefox

(later)

mrmiles@kms_d:/etc/init.d$ sudo /etc/init.d/lighttpd stop
 * Stopping web server lighttpd
  ...done.
mrmiles@kms_d:/etc/init.d$ sudo /etc/init.d/lighttpd start
 * Starting web server lighttpd
  ...done.
mrmiles@kms_d:/etc/init.d$ sudo /etc/init.d/lighttpd stop
 * Stopping web server lighttpd
  ...done.
mrmiles@kms_d:/etc/init.d$ sudo /etc/init.d/apache2 stop
 * Stopping web server apache2
  ...done.
mrmiles@kms_d:/etc/init.d$ sudo /etc/init.d/boa stop
Stopping HTTP server: boa.
mrmiles@kms_d:/etc/init.d$ apt-get install avrdude
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
  ...done.
 * Stopping web server lighttpd
  ...done.
 * Starting web server lighttpd
2009-03-27 23:39:33: (network.c.300) can't bind to port:  80 Address
already in use
  ...fail!
invoke-rc.d: initscript lighttpd, action "restart" failed.
mrmiles@kms_d:/etc/init.d$ sudo lsof -i :http
COMMAND  PID     USER   FD   TYPE DEVICE SIZE NODE NAME
firefox 6170  mrmiles   21u  IPv4 108111       TCP
kmsd.local:59747->jp-in-f18.google.com:www (ESTABLISHED)
firefox 6170  mrmiles   57u  IPv4 105604       TCP
kmsd.local:51119->jp-in-f83.google.com:www (ESTABLISHED)
apache2 7105     root    4u  IPv4 109772       TCP *:www (LISTEN)
apache2 7106 www-data    4u  IPv4 109772       TCP *:www (LISTEN)
apache2 7108 www-data    4u  IPv4 109772       TCP *:www (LISTEN)
apache2 7110 www-data    4u  IPv4 109772       TCP *:www (LISTEN)
apache2 7111 www-data    4u  IPv4 109772       TCP *:www (LISTEN)
apache2 7112 www-data    4u  IPv4 109772       TCP *:www (LISTEN)
mrmiles@kms_d:/etc/init.d$ sudo netstat -antp
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address
State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*
LISTEN      5173/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*
LISTEN      5313/smbd
tcp        0      0 0.0.0.0:80              0.0.0.0:*
LISTEN      7105/apache2
tcp        0      0 127.0.0.1:631           0.0.0.0:*
LISTEN      5095/cupsd
tcp        0      0 0.0.0.0:445             0.0.0.0:*
LISTEN      5313/smbd
tcp        0      0 192.168.0.16:59747      66.249.89.18:80
ESTABLISHED 6170/firefox
tcp        0      0 192.168.0.16:51119      66.249.89.83:80
ESTABLISHED 6170/firefox

----------

On Fri, 27 Mar 2009 23:50:13 +0900
 From Debian some packages' point of view, you would see "debian/{postrm,prerm}"
 script in that package. You can get it by using "apt-get source <packagename>".


--

I'm not really sure where to go from here.

---

### Post by dcstar on 2009-03-28
> **mr.miles said:**
> This is a fairly long post, with attempts by others to help, about trying to 

apt-get install something

without seeing this:

httpd (no pid file) not running
(98)**Address already in use: make_sock: could not bind to address 0.0.0.0:80**
no listening sockets available, shutting down
Unable to open logs
  ...fail!
invoke-rc.d: initscript apache2, action "restart" failed.
dpkg: error processing textpattern (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 textpattern
E: Sub-process /usr/bin/dpkg returned an error code (1)
........
Thanks to everyone who responded.
I'm still not sure what's going on, but the error message from dpkg
has changed. It looks like textpattern is configured to use apache2
and lighttpd? Anyhow, I'd just like to make dpkg useable again.

**I've got boa, apache2 and lighttpd installed**, and I can start and stop
all of them. When I go to 'localhost' I can see an 'It works!' page.
........
I'm not really sure where to go from here.

Well, uninstalling two of the **THREE** conflicting webservers might actually allow one of them to actually be the webserver for your system and work as it is intended to.

Apache cannot bind to an address because one of those other two webservers is already using it.

---

### Post by mr.miles on 2009-04-03
Well, removing one of the webservers did fix the problem. Thanks.
Apparently the GUI Synaptic Package Manager automatically recovers from this kind of situation better than naively using apt-get which refused to remove anything (including the servers) because the servers weren't starting.

---

