---
title: "proftpd + gadmin and other server stuff"
date: 2010-04-21
forum: Desktop Environments
---

### Post by quimkaos on 2010-04-21
I'm installing a few server services on Ubuntu desktop 9.10. yes  probably I should be doing this on the server distro, but I like to have  an graphical interface in any server I use, even being a  security/resource issue. this is a test server and I'll probably move later to the server edition.

I've already installed and configured the webserver (php, mysql, etc), SSH server, mumble server, Team Speak server, but I hanged in the ftp server:

1 - installed proftp and it works out of the box, thou it uses linux login system, and after logged in with a valid Linux user I have access to all folders in the system, at least I'm able to list them.

2 - can't start/stop/restart ftp server from init.d - "/etc/init.d/proftpd stop" gives me the message ProFTPd is started from inetd/xinetd

3 - when i install gadmin-proftpd i simply can't start the server... after adding user and directorys, the status (on the top right) stays deactivated, after clicking in the activate bottom.

##other##

any software open-source/GPL for server webadministration like webmin? without an pro ediction? ([www.webmin.com](www.webmin.com))

any input, opinions, suggestions are **really** welcome!

---

