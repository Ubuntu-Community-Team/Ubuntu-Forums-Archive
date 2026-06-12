---
title: "Root login/session problem regarding cron/webmin"
date: 2005-11-16
forum: Desktop Environments
---

### Post by guy_uk on 2005-11-16
Hi Ubuntu-ees

background:
I've got ubuntu hoary running on a rackmount server acting as a domain controller and samba fileserver.

I have installed webmin on the machine to help other people take some of the day to day admin stuff off me.

Its version 1.240 downloaded from webmin.com as i got this working alot quicker and easier than the apt-sourced version.

My question/problem is - I want to use the lovely easy 'filesystem backup' feature in webmin to backup a couple of folders within /home.

It works! - but only if i am logged in to the machine (as user) or have recently been logged into the machine.

If i don't log in and the backup attempts to run, it doesn't! I get entries in syslog stating that a session was opened and closed for root at the same times, at the time the scheduled backup should have run.

I'm wondering:- i set the root user to have a password, but it still won't let me log into gnome as root.

Is it possible that, because i log in as the user, then sudo to root to run an app as root, that the session remains open for root for a while, and therefore the scheduled backup will run (as root), but if i don't log in, or the root session times out, the scheduled backup cannot then log in as root?

Is this part of the same setup that prevents root from logging into gnome, instead requiring sudo?

If so, how can i change it so that a completely unattended machine can run a scheduled (cron?) command, logging in as root?

Please help, i don;t know whether this is a blatant gap in my general linux knowledge, or a gap in my 'using root under ubuntu' knowledge

Thanks guys+gals

Guy

---

### Post by kzutter on 2005-11-16
I don't know if it will help with your webmin / backup problem, but...

System / Administration / Login Screen Setup has the switch that will let root login to gnome.

_Ken

---

### Post by guy_uk on 2005-11-16
Cheers Ken :) 

will give it a shot asap 

thanks, Guy

---

