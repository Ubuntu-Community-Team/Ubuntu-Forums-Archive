---
title: "MythTV won't start backend."
date: 2006-01-08
forum: General Help
---

### Post by fozzytbear on 2006-01-08
I have installed mythtv a few times before, but never on Ubuntu, using apt-get (always on gentoo).  Right now I'm trying to get the backend started with my PVR-150 card.  I am able to run myth-setup, and configure everything, but when I go to start the backend, I get this error:
```
Starting MythTV server: mythbackendSession management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
.
```
I am not sure whether or not I have missed something in setting up mySQL or mythtv.  the mythtv user exists, and here are the permissions:

```
user		host		Require PW		Priv.			Grant
mythtv  	%  			Yes  	 	USAGE   		No  	
mythtv 		192.168.1.%		Yes 		USAGE 			No 	
mythtv 		localhost		Yes 		USAGE 			No 	
```

mythtv user has all priveleges except GRANT on mythconverg.

I think my problem may lie in the fact that no mysql.txt file seems to be created in my .mythtv directory when I exit myth-setup.  The only mysql.txt file that exists is in /usr/share/.  I copied it by hand to the home directory the mythtv user and my other local user.
I feel like at some point when I set up mythtv in gentoo I was asked for a dbuser and pw.  Now it seems to be pre-made.

---

### Post by fozzytbear on 2006-01-08
nevermind....I figured it out.  Now for some reason the backend always crashes whenever I try to view Live TV.  It shows no image at all.

---

### Post by micjustmic on 2006-01-15
What did you do to fix the original error?

---

### Post by micjustmic on 2006-01-20
Okay, since fozzytbear either hasn't seen my request, or has chosen not to post, I'll answer myself for those that are still having this problem and haven't found the answer as of yet.

It's actually kind of simple, the file mysql.txt can show up in several directories.

/root/.mythtv/mysql.txt
/home/<user name here>/.mythtv/mysql.txt
/home/mythtv/.mythtv/mysql.txt

However, it shows up in one place I've only seen mentioned in one other post, and even though the suggestion given didn't actually suggest this file as the 'problem,' it's mention led me to the fix.

I've often seen mention of making sure the user name and password are correct in the files mentioned above, but it seems when loading mythbackend during boot, the file checked is /etc/mythtv/mysql.txt and changing the names/passwords in all the other copies/locations of this file will do no good to fix the boot problem.

When I looked in /etc/mythtv/mysql.txt the name was correct (mythtv) but the password was some off-the-wall combination of characters that I'd never typed in, nor seen anywhere on my system.

Changed this and joy, everything loads just fine.

This should not only fix the 'won't start on boot' problem, but also any problems you're having starting it manually.

I hope this helps someone out there, I searched these, and many other forums before I finally found what should be a simple to find answer.

Mic

---

