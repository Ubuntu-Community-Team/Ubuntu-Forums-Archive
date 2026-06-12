---
title: "Help configuring proftpd for web administration."
date: 2006-08-15
forum: Desktop Environments
---

### Post by em3raldxiii on 2006-08-15
Alrighty, so first off, I am not exactly a newbie any more.  I'm not a pro, but I'm more of an "intermediate" who occasionally gets stumped by simple things.
 
So here's what I got.  I have a successful LAMP server:  
1. Apache 2.0 (haven't upgraded cuz I am afraid of breaking something)
2. PHP 5.? (not at my comp atm, so I can't say for sure)
3. mySQL (configured successfully and running phpbb2 happily)
4. proftpd (probably configured wrong)
 
The domain is fully functional and I could happily leave it as-is and be happy.  However, I would like to be able to administer it via FTP from work.  When I access my server with FTP, either I can't log in (timeouts), or it logs in after a super long time (we're talking over a minute) ... and even when successful, everything is slow.  Also, I haven't figured out how to nail down default directories and such.
 
What I want:
 
1. Anonymous FTP access to a VERY limited directory with a few files and therefore read access.
2. Webadministrator for read/write/browse access to /var/www/.
3. Serveradministrator for FULL access to root (if possible)
4. Subdomain_administrator with read/write access to /var/www/[subdomain]/ .... there may be several different subdomain administrators if I decide to host more than one project.
5. Power-user accounts (roughly 6 of these) for read access to /var/www/, write access to /var/www/[username], but NO access to /var/www/[subdomain] or other username accounts.
 
If anyone can help me out here, I would be very grateful.  I have tried muddling through various howtos, but they all seem to be written with the expectation that a user understands how it all works.  It's a little frustrating actually.  That's why I like these forums .... someone usually comes along and spells it out, then I can go and help other people too :D
 
Thanks a bunch.
 
Incedentally, I am using this to administer my wife's band site ([www.anxietyofinfluence.ca]("http://www.anxietyofinfluence.ca")).  I know, shameless plug, but if you like bands like Evanescence and Lacuna Coil, you'll probably like her band.  They sound quite pro :D and you can DL/stream some songs from the site.

---

