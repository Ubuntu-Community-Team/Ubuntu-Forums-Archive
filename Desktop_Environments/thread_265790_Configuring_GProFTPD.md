---
title: "Configuring GProFTPD"
date: 2006-09-26
forum: Desktop Environments
---

### Post by brettsut on 2006-09-26
I believe this to be my first post, and I am new to the whole linux thing. I have gproftpd running fine. My problem is, I would like to add a user and change another user. When I log in, the changes will not update. I assume this is because I have not logged in as root. So:

1. I am unable to login as root. I tried the unsuggested add root to the login screen approach, but root was not available.

2. I tried running sudo gproftpd, but the program window comes up and never populates beyond the window.

3. I ran gedit as root and changed the .conf file, but when I do that I am no longer able to login until I change it back to the way it was. They only change I have made in this attempt is to change <Anonymous /home/ftp> to <Anonymous />

Also, when I first run GProFTPD I get an information window that says "Cant open the security log here: /var/log/secure"

So, I assume that I have some rights issue that I have messed up. I have tried to rtfm, but my two brain cells no longer spark a thought when rubbed together.

My main goal is to make a login to update my web page that is another subdirectoy in /var. It would be nice to just be able to FTP it directly.

Thanks to all. Brett in Salt Lake

---

### Post by smoka on 2007-02-18
Can't say I know anything about your other questions, as I'm just starting to figure this stuff out, but I've just been getting a problem with that message information windows when it loads:

"Cant open the security log here: /var/log/secure"

I figured out that what I did was somehow manage to set that log file with the wrong permissions.

cd /var/log
ls -l

Scrolling down I found this line:
-rw-r----- 1 root **root**   26433 2007-02-19 00:44 syslog.log

Whereas the other logs I could see were set to:
-rw-r----- 1 root **adm**    1454 2007-02-19 00:37 syslog

So, I decided to change the ownership of the syslog.log file:
sudo chown root:adm syslog.log

now, doing a ls -l gives the following:
-rw-r----- 1 root **adm**   26433 2007-02-19 00:44 syslog.log

That seemed to get rid of the message from appearing each time I start GProFTPD.

hth

---

