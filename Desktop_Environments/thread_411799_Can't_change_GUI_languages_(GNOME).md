---
title: "Can't change GUI languages (GNOME)"
date: 2007-04-17
forum: Desktop Environments
---

### Post by verucabong on 2007-04-17
Hi everyone-

I've looked through the forum a bit and can't seem to find an answer for this.  I've installed Ubuntu (Dapper) and absolutely love it.  What I'd like to do is change the GUI to German.  I've gone to System-Administration-Language Support and enabled the German tickbox and let the associated install perform.  I then rebooted (just to make sure) and I can't change to German.  On the Login screen where you select the language you want the only ones that are listed are the English variants and if I log in and go back to Language Support, I see German checked but not in the drop down box as an option for new users.

I'm running a fairly standard rig.  Really the biggest thing I've done to this has been the installation of VMWare Server (and it works perfectly)

Thanks!

vb

---

### Post by Theimon on 2007-04-21
Did you install the German languagepacks?

---

### Post by aneeshm on 2007-04-21
sudo apt-get install language-pack-de language-support-de



Should fix the problem.

---

