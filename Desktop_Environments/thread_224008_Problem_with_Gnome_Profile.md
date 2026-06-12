---
title: "Problem with Gnome Profile"
date: 2006-07-27
forum: Desktop Environments
---

### Post by tommohawk on 2006-07-27
Have a strange one here that I can't seem to fix....

My user account seems to be broken - I can't log in to a gnome session (screen freezes) but I can log into a KDE session or a failsafe Gnome session.  Obviously something is loading that is causing the desktop to freeze but I don't know what!

Anyone got any ideas - I don't want to lose all my settings.

Also, I created a new user account for my daughter and that logs into Gnome without any problems.  It even gives hardware accelerated 3D whereas mine give me the Mesa drivers?!  Any new user accounts I create don't give me access to sound and stuff like that.

Suggestions??!!:confused:

---

### Post by apjone on 2006-07-27
when i had this i used

log in to a text terminal as root and

mv /home/user /home/oldhome
then
mkdir /home/user

now log in to gnome as that user and your profile will be re-created

next log out and as root

cp -r /home/oldhome /home/user 

and then logged in and it came back perfect

IT WORKED FOR ME, IT MAY NOT WORK FOR YOU - DONT BLAME ME IF IT DOSEN'T

---

### Post by tommohawk on 2006-07-27
OK I might give it a try later.  Don't want to lose my profile so might just live with KDE for now.  Only problem is I can't get my hot keys to work.

Do you know anything about this one then.......

When Gnome loads up, I have all my hot keys working and infra red, PCMCIA etc.  But when KDE loads up they don't work.  Gnome must be running some kind of script or loading some drivers to set these devices up but I can't track them down.

Any ideas?

---

