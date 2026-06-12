---
title: "Brown Screen after Login"
date: 2006-09-17
forum: Desktop Environments
---

### Post by jrthorne on 2006-09-17
Hello

Dell Latitude C600 video ATI Mobility 3

Installed 6.06 from LTS CD with no problem.
After install run thru Software update (172 updates)
Now after login I get a blank "brown" screen with mouse pointer.
Will run in Gnome "Safe Mode".
Ran dpkg-reconfigure xserver.xorg and selected various 
options auto yes and no, vesa etc and still can not get past
blank screen.

help

jrt

---

### Post by absnewby on 2006-11-07
Did you find a solution for this?

---

### Post by simonalexander2005 on 2007-03-22
I've got exactly the same problem... and a little white square appears in the top left after a while - and the cursor changes to a text selection cursor (the I-Shaped one) when i hover over it...

---

### Post by patscott on 2007-03-22
Me too - the only thing I did differently to normal before shutting down last time was to set my bluetooth headset as the default audio device - seems pretty unlikely to be the problem.  I also can't even start Gnome in failsafe mode, even if I try renaming all my Gnome config directories.  Could this have been caused by some recent update??  How does one roll back the last batch of updates?

---

### Post by Waffle Zombie on 2007-03-28
I managed to fix this by uncommenting my loopback interface in /etc/network/interfaces (I think I was a bit over enthusiastic when trying to get network manager to work).

---

### Post by xdamini_me on 2007-05-02
Has anyone found a solution for this yet? I have scoured the forums/net for a solution to this but to no avail.

 I have tried reinstalling Ubuntu 6.10 on my HP nx9110 laptop (dual boot with XP). The installation completes successfully but after I log in, all I get is the brown screen and mouse cursor.

I have tried the suggestion from another post to log in in safe mode and create a new user and tried to log in again with the new user. Still the same problem.

I've tried the installation several times, ensuring each time I start with a fresh partition (i.e. delete previous partition). Again, install goes smoothly until after I login.

I have tried installing Fedora Core 6 which runs fine, however I would like to use Ubuntu!

Any help appreciated.

---

### Post by carloslosgrande on 2007-05-04
I've just has this same problem come up in Feisty. Tried the 'recovery mode' and got this error "failed to initialize HAL"
This is after a clean install and then setup restricted drivers for my ATI card.
Luckily I've still got Dapper running on the other disc.
So what now? reinstall?

---

### Post by Vousmanos on 2007-08-06
I was able to reproduce the error by blocking access to loopback. I suppose the best thing to do is make sure loopback interface is configured properly.

EDIT: Forgot to say that i got the brown (mmmm) background and the white box on the top left-corner. As soon as you enable access to loopback (i did it by iptables for testing) that white box becomes an error message by GNOME Settings Manager informing you that some connection has timed out and then you get into gnome as normal. It is an excellent demonstration of a Catch -22 !

---

