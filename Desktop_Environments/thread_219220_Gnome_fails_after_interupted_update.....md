---
title: "Gnome fails after interupted update...."
date: 2006-07-19
forum: Desktop Environments
---

### Post by mallangong on 2006-07-19
Last night I shut down the computer accidently unaware that 
update was still in the process of installing. 

These were updates from a fresh install of Dapper (old laptop so it was the alternate version an not the live cd)

when restaring default gnome wont start - can get to the desktop
in recovery/safe mode but at a loss from where to go from there...

---

### Post by mattisking on 2006-07-19
the quickest answer would be to try 
sudo apt-get update
sudo apt-get dist-upgrade
then log out and see if it will let you log back in.

---

