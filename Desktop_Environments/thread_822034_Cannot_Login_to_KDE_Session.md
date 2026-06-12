---
title: "Cannot Login to KDE Session"
date: 2008-06-07
forum: Desktop Environments
---

### Post by 4WoofGrrrr on 2008-06-07
Gutsy on AMD-64 PC

I just rebooted my system after weeks of up time.  Now, when I try to login, the after the screen going dark for a few seconds, the login screen is re-displayed.  Just to make sure it's not something in my setup (which I have not changed,) I went to console and created a new login and tried to login using that.  I still cannot.

Obviously, this makes my system useless to me.

I have been keeping my system up to date as update notifications have arrived.  I have not installed any new software in months, nor have I tweaked any settings.  I suspect that one of said updates might have "fixed" things for me.

I looked at various log files in /var/logs (kdm.log, Xorg.0.log, syslog, etc) and the only thing I can see is that in auth.log, the kde session pam_unix(kdm:session) is closed as soon as it is opened.

I even re-installed the latest proprietary NVidia driver, allowing the installer to re-create xorg.conf for me.

I'm not a Linux guru and I don't want to \be.  I just want to get work done.

Can someone please help me???

---

### Post by viikinki on 2008-06-08
Just to let you know I am facing the same problem with kubuntu 8.04/kde 4.0.80 installed. 

I am not sure what is causing it but surely it is affecting many kubuntu users :(

---

### Post by 4WoofGrrrr on 2008-06-08
I just ran 'apt-get update', 'apt-get upgrade', and 'apt-get dist-upgrade'.  Nothing.  I still cannot login.  Maybe I should upgrade from gutsy to hardy...

---

### Post by msidhard on 2008-06-08
hey me too got this problem and i just going on searching for it. u can try sudo dpkg-reconfigure -phigh Xserver-xorg. I STILL GOT ANY REMEDY FOR IT. I THINK IT MAY HELP U. THEN TRY sudo mv /home/username /home/newname . username refers to ur default uname

---

### Post by 4WoofGrrrr on 2008-06-08
I've since started my upgrade from Gutsy to Hardy.  I needed to do it anyway.  I hope that fixes the problem...

---

### Post by 4WoofGrrrr on 2008-06-08
I don't know if the others would consider this "solved" or not, but after Gutsy upgrade completed, I'm back in business

---

