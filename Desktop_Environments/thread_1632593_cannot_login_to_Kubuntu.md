---
title: "cannot login to Kubuntu"
date: 2010-11-28
forum: Desktop Environments
---

### Post by Vinger on 2010-11-28
Hello,

I have Kubuntu 10.10 installed in a dual boot configuration. (win vista)
I also have the Unity desktop installed.
I normally login to Kubuntu automaticly (KDE)

This all worked fine until now.
When i start Kubuntu, i get the login screen. I give my password but nothing happens; the login screen comes back to login...

I can start the unity desktop without problems with the same password...
Also windows is not a problem...

Does anyone knows what i can do?

Allready thanks.

---

### Post by johnnyhop on 2010-11-28
I just started having the same problem.  All was well until a few hours ago with Kubuntu 10.10.  The non administrative logins created for my roommate and a guest account are fine.  Tried moving the .kde folder to a temp directory but no change.  Also ran clamscan from console login.  Any suggestions short of a clean install?

---

### Post by Vinger on 2010-11-30
Ok,

I just reinstalled Kubuntu (not formatting my /home)
With this, i can login without problems...

I'm now busy with installing all my packages. Fortunately, i keep all my settings... :-)

grz

---

### Post by johnnyhop on 2010-12-01
I've considered doing that. I've been trying to create a new superuser account with adduser and useradd. So far found several approaches that don't work. Have spent time researching syntax for doing so and hope to have time tomorrow to experiment. Meanwhile created a regular user account with adduser and copied Thunderbird and Firefox settings to that account folder. It appears we're two specks of sand on the beach on this matter, noting this thread has gotten viewed but so far no suggestions for resolve.

---

### Post by Vinger on 2010-12-01
I've tried also to add a new admin account, and that worked. The problem i had was my automatic login which had some problems...

Hope you get a result that works for you!

grz

---

### Post by johnnyhop on 2010-12-10
Haven't spent time on the matter for a while.  Had no problem creating a restricted user account with adduser or useradd but have spent hours trying to create a superuser account with same without success.  My goal was to create another superuser account, then delete and reinstall my account.  At this point I'll try your approach and report my result.  Not at all sure if I did something to cause it or if there may be a hint as to why this is happening in a log file.

---

### Post by johnnyhop on 2010-12-14
My problem was in the home folder.  After formatting and reinstalling the file system partition there was no change.  Then did another clean install including a format of the home partition.[-o< I think I know what I did to cause the problem but don't care to try to recreate it.

---

