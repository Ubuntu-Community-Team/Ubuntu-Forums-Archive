---
title: "choosing KDM or gnome from vnc"
date: 2006-06-06
forum: Desktop Environments
---

### Post by rajko on 2006-06-06
I have ubuntu 6.0.6 (upgraded from 5).

KDM is default manager (I used 'sudo dpkg-reconfigure kdm' and selected kdm).
after I start kdm (sudo /etc/init.d/kdm start)
1. user mirko automaticaly log in and his desktop appears on vncviever hostX:0

2. I'm rajko and I start vncserver which creates hostX:1
I want my desktop to be KDM not gnome which is loaded

I'm accessing from remote so choosing default display on login screen is not an option. I need to edit some config file, but can not find it...

Thanks, Rajko.

---

### Post by rajko on 2006-06-07
I think I found it... :)

in $HOME create .xsession file with content:
exec startkde

this way any user can choose which display it wants to run...

---

