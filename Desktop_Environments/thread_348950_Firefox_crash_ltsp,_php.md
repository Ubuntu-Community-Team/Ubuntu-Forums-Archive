---
title: "Firefox crash: ltsp, php"
date: 2007-01-29
forum: Desktop Environments
---

### Post by Anivair on 2007-01-29
OK, I have a weird issue. 

Background: I am running a dapper server here at the office.  The employees log into it via thin clients that operate off of ltsp. We have about 30 people on the system.  They use gnome desktops with a pretty minimal setup.   I'm switching us over to a php timeclock that is run on our intranet (which is nothing more than a graduated ubuntu machine running stuff in /var/www, but what more do you need?),  

The phptimeclock project here here: [http://sourceforge.net/projects/timeclock/](http://sourceforge.net/projects/timeclock/)
Info on ltsp is here: [http://www.ltsp.org/](http://www.ltsp.org/)

Problem: This morning I saw a few people (5 or so) who could not log into the timeclock.  It's linked from our mainpage and when they navigate there firefox just crashes. 

Shortly after that, some people inhereted the problem.  That is they logged in in the morning, but could not get back in.  As far as I can tell, nobody is gaining the ability to get in, but I can't promise that.  

I tried firefox from the command line and when I hit that link, I got a segmentation fault. 

I tried an strace of firefox, but the program won't even start up (strace just runs for a long time noting unavailable recources). 

I tries strave firefox -safe-mode and then firefox finally opened (after a long delay) but ran so slowly that it wouldn't render anything, so that was useless. 

Anything? 

Also, I have got to use this: :guitar:

---

### Post by Anivair on 2007-01-30
Sorry, my brain was garbled.  Can someone (a mod?) please move this to general help?  I'll report later if not, but it'd be less list spamming by me that way.

---

