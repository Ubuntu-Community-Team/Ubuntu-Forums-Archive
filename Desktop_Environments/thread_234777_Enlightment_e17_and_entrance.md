---
title: "Enlightment e17 and entrance"
date: 2006-08-12
forum: Desktop Environments
---

### Post by chacon on 2006-08-12
Running dapper..

So I added this to my apt sources:


deb [http://seerofsouls.com/](http://seerofsouls.com/) dapper contrib e17

and all worked well!  But once of the main things that I wanted was entrance. :( 

I found another repo..but for breezy:

[http://issaris.be/breezy/](http://issaris.be/breezy/)

I installed the entrance form that repo by hand and it installed.

Then I edited /etc/X11/default-display-manager from this:
> 
/etc/sbin/gdm

to this:
> 
/usr/bin/entrance

I killed gdm for good:
> 
sudo update-rc.d gdm remove

I rebooted just for kicks...and viola!  :D

---

