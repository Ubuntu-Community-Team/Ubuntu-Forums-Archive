---
title: "Stuck at TTY1"
date: 2009-06-22
forum: General Help
---

### Post by ActivEcks on 2009-06-22
ok, when my ubuntu server comes up, it gives me:

Ubuntu 7.10 servername tty1
servername login:

I can type anything i want, when i hit enter, it just sends me back to that login prompt. No asking for password. No error message... nothing.

I've booted into recovery mode, and created a new user (adduser) and set it with a home directory and password. rebooted into normal tty1 and still, same thing.

I can log in remotely via SSH to get access to things, but i wont have that access indefinately, so i need to get this local access setup.

also, what may be noteworthy... is when the server starts up, it doesnt automatically display the login after services are finished.. the last thing it shows is:

*Running local boot scripts (/etc/rc.local)    [OK]

and just sits there. I have to hit enter before it shows the login request. Not sure if that is by design or not, as this is the only server I have been having to work on like this.

thanks in advance for any help. I would update the build, but im afraid I would lose my SSH access in lue of updating.

---

### Post by Scunizi on 2009-06-22
You really need to upgrade. Version 7.10 is not LTS and is at end of life as of April of this year with no further support.  Hopefully you have a seperate /home as that will make upgrading simpler.

Two links might be of interest to you..

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
and 
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

When upgrading you might consider moving only to version 8.04 as that has support for 5 years on the server.

---

### Post by ActivEcks on 2009-06-22
Thanks for the links and info, I'll plan on doing an upgrade immediantly. However, I was reading the instructions for the -server upgrade and i'll need tty access.

Think someone would be able to help me atleast get that far with what I have? This is a webserver and I can't just quite do a new install. I wouldn't know where to begin. (Apache2, SQL databases, and webmin configs and god knows what else). The server was built by someone else.

I've used linux here and there, but when it comes to things like this, i sit in front of a manual or google search bar.

---

