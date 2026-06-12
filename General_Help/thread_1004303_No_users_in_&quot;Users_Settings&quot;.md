---
title: "No users in &quot;Users Settings&quot;"
date: 2008-12-07
forum: General Help
---

### Post by Mario1776 on 2008-12-07
I have installed xubuntu-8.10-alternate-i386.iso on several different Dell Optiplex GX110's. 70% of the time there seems to be a problem with the xubuntu install. When looking at "Users Settings" there are no users listed. In working installs I have seen the user and administrator listed in "User Settings", so no users being displayed is the first sign of trouble. But it seems that this only hints to more severe unseen errors.

I have tried and apparently suceeded at creating a new user, but after restarting I get the error message "The gdm user does not exist. please correct gdm configuration and restart." The forum page [http://ubuntuforums.org/showthread.php?t=623647](http://ubuntuforums.org/showthread.php?t=623647) suggests the error is caused by faulty package configuration and to run "sudo dpkg-reconfigure -a" which I have done. On one occasion "sudo dpkg-reconfigure -a" worked, the users that were supposed to be there indeed appeared, but numerous attempts on other faulty installs have failed. It seems that the GDM error does not occur until I try to create a new user on a faulty install (an install not displaying any user in "Users Settings"). The install is usable as long as I don't try to create a new user, but it is disconserting to know that there are mystery errors lurking in the OS.

If anyone can advise about how to resolve my problem, it would be greatly appreciated. If anyone could even tell me what exactly the problem is it would be appreciated. Using "sudo dpkg-reconfigure -a" to reconfigure every package in the OS seems a little like overkill.

P.S.
If you request particular data/information/output for you to interpurt and to use to help me, please tell me how to procure it (I have had a great many experiences with linux, unfortunately most of them have been bad).

---

