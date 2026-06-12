---
title: "Virus Protection for a File Server"
date: 2008-03-25
forum: Dell  Ubuntu Support
---

### Post by arvadawest on 2008-03-25
Hi and good day,
We have a Dell XPS410 running Fiesty 704.  We are going to use this machine as our File Server, so we are going to migrate our window folders/files onto the XPS410 system.  What virus protection would offer the best protection.

Please keep in mind we are "newbies" and just beginning on Linux.  Thank you for your help!  -aw

---

### Post by prshah on 2008-03-25
> **arvadawest said:**
> Hi and good day,
We have a Dell XPS410 running Fiesty 704.  We are going to use this machine as our File Server, so we are going to migrate our window folders/files onto the XPS410 system.  What virus protection would offer the best protection.

Please keep in mind we are "newbies" and just beginning on Linux.  Thank you for your help!  -aw

ClamAV

---

### Post by arvadawest on 2008-03-25
> **prshah said:**
> ClamAV

How do we set this up?

---

### Post by slackmaster on 2008-03-25
This site explains how to install Ubuntu Server, LAMP, WebAdmin, and configure it for your network.  

[http://onlyubuntu.blogspot.com/2007/10/ubuntu-710-gutsy-gibbon-lamp-server.html](http://onlyubuntu.blogspot.com/2007/10/ubuntu-710-gutsy-gibbon-lamp-server.html)

Its a good start.  You may encounter other issues, but see how this tutorial works for you.

To install clamAV, just go to applications--'add/remove' and search for clamAV.  Once found, select it, and apply.  It will install and from there I'm sure you know how to use AV.

Good luck.

Slack

---

### Post by arvadawest on 2008-03-25
Hi Slack, we are using 7.0.4 Fiesty desktop version.  Can we still do all this using the desktop ed. or do we have to go with the Server version?  I'm sorry.  We are newbies.  Thanks.

---

### Post by arvadawest on 2008-03-25
> **slackmaster said:**
> This site explains how to install Ubuntu Server, LAMP, WebAdmin, and configure it for your network.  

[http://onlyubuntu.blogspot.com/2007/10/ubuntu-710-gutsy-gibbon-lamp-server.html](http://onlyubuntu.blogspot.com/2007/10/ubuntu-710-gutsy-gibbon-lamp-server.html)

Its a good start.  You may encounter other issues, but see how this tutorial works for you.


Slack

Sorry, looks like my first reply didn't go through.  We are running Feisty 7.0.4 desktop ed.  Can we stay with this version and still use it as a file server?  Thanks.

---

### Post by prshah on 2008-03-25
> **arvadawest said:**
> How do we set this up?

By set this up, I assume you mean install.```
sudo apt-get install clamav
``` After installation, it will ask you for configuration, or you can run it from your Applications menu.

> **arvadawest said:**
> Hi Slack, we are using 7.0.4 Fiesty desktop version.  Can we still do all this using the desktop ed. or do we have to go with the Server version?  I'm sorry.  We are newbies.  Thanks.

Since you are using it as a FILE server, you don't need to setup LAMP (Linux, Apache, MySQL, PHP). In either case, yes you can use the desktop edition, but if you still want to use LAMP, you will have to set it up manually, whereas server install has an option to do this automatically for you.

---

### Post by arvadawest on 2008-03-26
> **prshah said:**
> By set this up, I assume you mean install.```
sudo apt-get install clamav
``` After installation, it will ask you for configuration, or you can run it from your Applications menu.



Since you are using it as a FILE server, you don't need to setup LAMP (Linux, Apache, MySQL, PHP). In either case, yes you can use the desktop edition, but if you still want to use LAMP, you will have to set it up manually, whereas server install has an option to do this automatically for you.

I installed and and when I ran the application it said:

Unable to view ClamAV's information file.
This will affect
how ClamTk views the number of viruses and version information.

Then it said:

ou do not appear to have virus definitions!
Running "freshclam -v" as root may fix the problem.

So when I ran freshclam -v as sudo it said (sorry if this is long):

Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host db.local.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host db.local.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-6397.cdiff from db.local.clamav.net
Retrieving [http://db.local.clamav.net/daily-6397.cdiff](http://db.local.clamav.net/daily-6397.cdiff)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host db.local.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host db.local.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
ERROR: getpatch: Can't download daily-6397.cdiff from db.local.clamav.net
Retrieving [http://db.local.clamav.net/daily-6397.cdiff](http://db.local.clamav.net/daily-6397.cdiff)
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host db.local.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
ERROR: getpatch: Can't download daily-6397.cdiff from db.local.clamav.net
Retrieving [http://db.local.clamav.net/daily-6397.cdiff](http://db.local.clamav.net/daily-6397.cdiff)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host db.local.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host db.local.clamav.net (IP: 129.64.99.170)
ERROR: getpatch: Can't download daily-6397.cdiff from db.local.clamav.net
Retrieving [http://db.local.clamav.net/daily-6397.cdiff](http://db.local.clamav.net/daily-6397.cdiff)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host db.local.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host db.local.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
ERROR: getpatch: Can't download daily-6397.cdiff from db.local.clamav.net
WARNING: Incremental update failed, trying to download daily.cvd
Retrieving [http://db.local.clamav.net/daily.cvd](http://db.local.clamav.net/daily.cvd)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host db.local.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host db.local.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
ERROR: Can't download daily.cvd from db.local.clamav.net
Restoring incremental directory daily.inc from backup
Giving up on db.local.clamav.net...
ClamAV update process started at Wed Mar 26 10:58:59 2008
Querying current.cvd.clamav.net
TTL: 277
Software version from DNS: 0.92.1
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.90.2 Recommended version: 0.92.1
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cvd version from DNS: 45
main.inc is up to date (version: 45, sigs: 169676, f-level: 21, builder: sven)
daily.cvd version from DNS: 6397
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
WARNING: Incremental update failed, trying to download daily.cvd
Retrieving [http://database.clamav.net/daily.cvd](http://database.clamav.net/daily.cvd)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
ERROR: Can't download daily.cvd from database.clamav.net
Restoring incremental directory daily.inc from backup
Trying again in 5 secs...
ClamAV update process started at Wed Mar 26 10:59:04 2008
Querying current.cvd.clamav.net
TTL: 271
Software version from DNS: 0.92.1
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.90.2 Recommended version: 0.92.1
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cvd version from DNS: 45
main.inc is up to date (version: 45, sigs: 169676, f-level: 21, builder: sven)
daily.cvd version from DNS: 6397
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
WARNING: Incremental update failed, trying to download daily.cvd
Retrieving [http://database.clamav.net/daily.cvd](http://database.clamav.net/daily.cvd)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
ERROR: Can't download daily.cvd from database.clamav.net
Restoring incremental directory daily.inc from backup
Trying again in 5 secs...
ClamAV update process started at Wed Mar 26 10:59:12 2008
Querying current.cvd.clamav.net
TTL: 263
Software version from DNS: 0.92.1
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.90.2 Recommended version: 0.92.1
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cvd version from DNS: 45
main.inc is up to date (version: 45, sigs: 169676, f-level: 21, builder: sven)
daily.cvd version from DNS: 6397
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
WARNING: Incremental update failed, trying to download daily.cvd
Retrieving [http://database.clamav.net/daily.cvd](http://database.clamav.net/daily.cvd)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
ERROR: Can't download daily.cvd from database.clamav.net
Restoring incremental directory daily.inc from backup
Trying again in 5 secs...
ClamAV update process started at Wed Mar 26 10:59:18 2008
Querying current.cvd.clamav.net
TTL: 258
Software version from DNS: 0.92.1
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.90.2 Recommended version: 0.92.1
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cvd version from DNS: 45
main.inc is up to date (version: 45, sigs: 169676, f-level: 21, builder: sven)
daily.cvd version from DNS: 6397
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
WARNING: Incremental update failed, trying to download daily.cvd
Retrieving [http://database.clamav.net/daily.cvd](http://database.clamav.net/daily.cvd)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
ERROR: Can't download daily.cvd from database.clamav.net
Restoring incremental directory daily.inc from backup
Trying again in 5 secs...
ClamAV update process started at Wed Mar 26 10:59:23 2008
Querying current.cvd.clamav.net
TTL: 252
Software version from DNS: 0.92.1
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.90.2 Recommended version: 0.92.1
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cvd version from DNS: 45
main.inc is up to date (version: 45, sigs: 169676, f-level: 21, builder: sven)
daily.cvd version from DNS: 6397
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
Retrieving [http://database.clamav.net/daily-6397.cdiff](http://database.clamav.net/daily-6397.cdiff)
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
ERROR: getpatch: Can't download daily-6397.cdiff from database.clamav.net
WARNING: Incremental update failed, trying to download daily.cvd
Retrieving [http://database.clamav.net/daily.cvd](http://database.clamav.net/daily.cvd)
Ignoring mirror 199.239.233.95 (due to previous errors)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.59.139.38 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (due to previous errors)
Ignoring mirror 72.21.63.182 (due to previous errors)
Trying host database.clamav.net (129.64.99.170)...
connect_error: getsockopt(SO_ERROR): fd=5 error=111: Connection refused
Can't connect to port 80 of host database.clamav.net (IP: 129.64.99.170)
ERROR: Can't download daily.cvd from database.clamav.net
Restoring incremental directory daily.inc from backup
Giving up on database.clamav.net...
Update failed. Your network may be down or none of the mirrors listed in freshclam.conf is working. Check [http://www.clamav.net/support/mirror-problem](http://www.clamav.net/support/mirror-problem) for possible reasons.

I am truly lost.  Remember, we are newbies.  thank you.  -aw

---

### Post by arvadawest on 2008-03-26
My apologies to All for pasting the long error message.  We uninstalled:

Virus Scanner
graphical front-end for ClamAV 
ClamTk is a GUI front-end for ClamAV using perl-Gtk2.
Homepage: [http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/)
Version: 2.31-0ubuntu1 (clamtk)

We are lost at  this point.  Thank you for your patience, but we are truly Newbies and need help  step  by step at this point.  Thank you.  -aw

---

### Post by slackmaster on 2008-04-03
Hello again,

sorry for the late reply.  I see someone else explained to you how to install Clamav from terminal.  But you can't update Clamav.  

The updater is probably working properly its just that all the sources for the virus definitions appear to be outdated.  You might have to update your repository list to find the latest definitions.  Those sources are outdated obviously.

The newest definitions are available [here]("http://www.clamav.org/download/packages/packages-linux/"):

I assume the Is the clamav-daemon must be activated (check in synaptic) and that you tried the following command right?


```
sudo apt-get install clamav-freshclam
```


I've noticed quite a few people have trouble updating Clamav.  Why not try [Avast ]("http://www.debianadmin.com/avast-antivirus-for-ubuntu-desktop.html")then if Clamav is too much of a hassle?  
Here is another Avast [link]("http://www.avast.com/eng/avast-for-linux-workstation.html").


 Well actually you **can **use LAMP as a file server, but here is a [tutorial ]("http://www.overclockingwiki.org/joomla/blogs/hot_new_products/how_to_make_a_ubuntu_file_server_and_more_part_1..html")on setting up an Ubuntu File Server.

Good luck, and be sure to look around the web for more solutions if you get hung up.  

S.

---

### Post by slackmaster on 2008-04-03
> **arvadawest said:**
> My apologies to All for pasting the long error message.  We uninstalled:

Virus Scanner
graphical front-end for ClamAV 
ClamTk is a GUI front-end for ClamAV using perl-Gtk2.
Homepage: [http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/)
Version: 2.31-0ubuntu1 (clamtk)

We are lost at  this point.  Thank you for your patience, but we are truly Newbies and need help  step  by step at this point.  Thank you.  -aw

Hi again,

I just tested Avast on my Ubuntu Desktop and it works fine.  No problem with the updater at all.

 This [tutorial ]("http://www.howtoforge.com/virus-protection-with-avast-on-ubuntu-gutsy-gibbon")walks you through the install step by step.  It is very easy to follow.    AND it explains how to create a link to Avast's graphical interface since you probably are more comfortable with the GUI right?  
I don't think there is any significant difference between installing Avast on 7.10 and 7.04.  Let me know if there is though.

]

As for the file server, well I gave you some [links ]("http://www.overclockingwiki.org/joomla/blogs/hot_new_products/how_to_make_a_ubuntu_file_server_and_more_part_1..html")for that.  Let me know if they help you at all.  



S.




h

---

