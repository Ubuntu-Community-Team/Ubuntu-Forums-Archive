---
title: "Reinstalling /etc/init.d/mysql ?? Fixing mysql-server install (for MythTV)"
date: 2006-08-09
forum: Desktop Environments
---

### Post by amadeus_z on 2006-08-09
Hello,

As a BSD user I went ahead and deleted everything I could 'find' on the system to do with mysql when reinstalling the server as I messed up the Myth installation.

It seems the mysql-server package isn't the source of the /etc/init.d/mysql script (as it would be in BSD) and now I'm stuck!

I saw a thread about replacing lost init.d scripts but there doesn't seem to have been an answer.

Where do the /etc/init.d scripts come from?

I tried

sudo apt-get --reinstall install mysql-server
sudo apt-get --reinstall install initscripts

But to no avail.

I even looked on the install CD for the original init.d scripts (in particular mysql) but couldn't find them.

Any help would be most appreciated!

Thanks

Amadeus

---

### Post by amadeus_z on 2006-08-12
Hi,

I ended up asking on netBSD BBS ([http://sdf.lonestar.org](http://sdf.lonestar.org)) and I was told to try the --purge option in apt-get!

So:

sudo apt-get install mysql-server-5.0
sudo apt-get --purge remove mysql-server-5.0
sudo apt-get install mysql-server-5.0

Worked a treat!

Thanks SDF!! :D

---

### Post by kornface13 on 2007-08-23
You Are Amazing!!!!!!!!!

---

