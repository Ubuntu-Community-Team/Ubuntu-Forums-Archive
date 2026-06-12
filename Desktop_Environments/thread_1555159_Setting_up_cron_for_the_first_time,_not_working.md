---
title: "Setting up cron for the first time, not working"
date: 2010-08-17
forum: Desktop Environments
---

### Post by racertim on 2010-08-17
I've read a lot on how to setup a task in crontab. I think I understand how to edit the file, but when I try to save the changes, it says "no crontab for xxx." Then it says that it cannot create a new crontab. 

I have ubuntu desktop 9 running as a webserver. I've read the details in these posts and it isn't helping.

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
[http://ubuntuforums.org/showthread.php?t=1003553](http://ubuntuforums.org/showthread.php?t=1003553)

Is there something super basic that I am missing? Thanks!

---

### Post by jobix on 2010-08-18
What is the full and exact error message when you say: "no crontab for xxx"?

Regarding trouble saving the file, did you check to see if you have the requisite permissions?

---

### Post by racertim on 2010-08-18
Yes, I have full permissions. This is a dedicated server I manage. Full error message after trying to save changes to my crontab file:

no crontab for USER - using an empty one
crontab: installing new crontab
"/tmp/crontab.gSZmYE/crontab":1: bad command
errors in crontab file, can't install.
Do you want to retry the same edit?

I'm getting this error no matter what command I try to execute. From what I can tell, my edit is formatted properly. Here is what I am trying to make the file look like:

MAILTO=""
# m h dom mon dow command
00 * * * * * /path/to/shell

---

### Post by racertim on 2010-08-18
Oh man.... too many *'s. It accepted the edit when I fixed that.

---

