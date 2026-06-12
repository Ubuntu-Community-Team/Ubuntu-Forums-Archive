---
title: "can't recall my main UN/PW !! oops"
date: 2005-08-27
forum: Desktop Environments
---

### Post by soopastar on 2005-08-27
So when I was installing ubuntu, I was a bit careless and was inexperienced.  I was basically waiting for that default question of the root un/pw, so when it was asking for my users, i kind of non-chalantly entered stuff.  I don't remember what username I entered, but I am pretty sure on my password.  Stupid, I know.  Any way to get that back?  I know redhat and others have a way of loggin in as single user root to change and edit stuff.  I don't have the cds on me (long story...moving to a new house, packed stuff etc etc).

Paul

---

### Post by amohanty on 2005-08-27
From grub drop into the recovery console and then at the command line:

cd /etc
cat passwd

this will return you a ton of usernames followed by stuff one per line. 

HTH
AM

---

