---
title: "libpango error"
date: 2006-07-28
forum: Desktop Environments
---

### Post by vangheem on 2006-07-28
Hi, this is my first post and I hate to be one of those who just asks a dumb question that anyone should know but I'm having a bit of an annoying problem here.

I'm just trying to install compiz right now.  I've done this a couple times on other machines but for some reason it doesn't seem to be working now...

> 
nate@blim:~$ sudo apt-get install xserver-xgl compiz-gnome cgwd gcompizthemer gcompizthemer-themes
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  cgwd: Depends: libpango1.0-0 (>= 1.12.3) but 1.12.2-0ubuntu3 is to be installed
  compiz-gnome: Depends: libpango1.0-0 (>= 1.12.3) but 1.12.2-0ubuntu3 is to be installed
  gcompizthemer: Depends: libpango1.0-0 (>= 1.12.3) but 1.12.2-0ubuntu3 is to be installed
E: Broken packages


I also find that I get that while trying to install other apps too.
Can I force the install, and if so, how?  Or is there a way to get the newest version of libpango?

Thanks for any help!

---

### Post by Irony on 2006-07-28
A quick google search and this pops up;

[http://packages.debian.org/unstable/libs/libpango1.0-0](http://packages.debian.org/unstable/libs/libpango1.0-0)

I presume you can install this later version over your current one.

---

### Post by vangheem on 2006-07-28
I've already tried that...  I run into a whole slew of dependency problems.  I try installing one dependency and it just creates another problem...  So I just gave up that route.

Maybe I'll just have to wait until Dapper updates libpango

---

### Post by vangheem on 2006-07-28
I just don't get why I am having dependency problems all the sudden.  I never had the issue before..  It's rather frustrating.  Some other apps fail to install also.

---

### Post by loell on 2006-07-28
i've had the same expirience back then..
when libpango is messed, i'm afraid you'll have reinstall IMHO
did you have forced install on some packages?

i think this only happens when some third party deb packages are installed in the system.

---

### Post by vangheem on 2006-07-28
Yes, I did actually.  Something got messed up when using easyUbuntu.  Yah, maybe I'll just do a reinstall....

---

