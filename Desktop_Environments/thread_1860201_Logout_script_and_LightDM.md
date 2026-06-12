---
title: "Logout script and LightDM"
date: 2011-10-14
forum: Desktop Environments
---

### Post by kedaly2 on 2011-10-14
Previously in Karmic, we created a logout script that does some work in the background on backing up a users home directory, this script was put in the /etc/GDM/PostSession directory. 

I can't figure out where to put a script that I want to run during a logout in LightDM.

I've googled and have found many people who are looking for this answer so any help would be greatly appreciated.

---

### Post by kedaly2 on 2011-11-09
Although I never did find out how to do a logout script with LightDM, I did find a workaround using pam_script.. This is a pam module that will allow you to run a script on login or logout.

I figured it out with the MAN pages for pam script.

pam_script is in the repositories.

---

