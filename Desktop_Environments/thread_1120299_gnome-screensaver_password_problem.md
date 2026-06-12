---
title: "gnome-screensaver password problem"
date: 2009-04-08
forum: Desktop Environments
---

### Post by LepeKaname on 2009-04-08
Hi, I have Ubuntu Intrepid (updated) 32bit version.

I noticed that when I lock the screen using gnome-screensaver (System -> Lock Screen) and enter my password it fails even I have checked it several times (no capslock, etc..) 
I had to switch to console login and kill the process. 
Looking at the auth.log it displays:

Apr  9 09:42:13 hostname unix_chkpwd[9168]: check pass; user unknown
Apr  9 09:42:13 hostname unix_chkpwd[9168]: password check failed for user (myusername)
Apr  9 09:42:13 hostname gnome-screensaver-dialog: pam_unix(gnome-screensaver:auth): authentication failure; logname= uid=1000 euid=1000 tty=:0.0 ruser= rhost=  user=myusername

Any idea why is this happening? anyone else with this problem?

Thanks.

---

