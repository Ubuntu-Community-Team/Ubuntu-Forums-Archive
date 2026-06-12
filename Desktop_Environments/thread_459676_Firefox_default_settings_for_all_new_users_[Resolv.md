---
title: "Firefox default settings for all new users [Resolved]"
date: 2007-05-30
forum: Desktop Environments
---

### Post by BevanFindlay on 2007-05-30
Hi all,
This is my first post on the Ubuntu forums, though I have used it and been aware of it for a little while.

We run a tertiary campus (and other things) that is currently a Windows-only shop, but we are working on setting up a bunch of boxes to sit in the student library for them to go online and type assignments on.  The machines have printers and Winbind logons working fine, but I need to be able to make a couple of customisations to Firefox to be applied to each new user profile when it is created.  I have searched the forums but cannot find how to do this.

I had thought of getting a script to automatically generate a user.js file, but as Firefox randomises its profile location, I can't see how to automate that (unless something like "cp /user.js /home/domain/%username%/.mozilla/profiles/*.profile/user.js" would work?  Comments welcome).

There are a few things I would like to do, but the main ones are (in approximate order of priority):
(1) Set to use our HTTP proxy server.
(2) Set to clear all personal information and the disk cache on exit (also because these are old boxes and diskspace would soon become an issue).
(3) Change the home page.
(4) Set "network.http.proxy.version" to "1.0" (long story).
(5) Set "network.negotiate-auth.allow-proxies" to "false" (equally long story).
(6) Add a couple of custom bookmarks.
(7) Possibly some other stuff (which I can't remember, so it can't be too important :)).

Might be a good one to document once we work out how to do it - I would expect that a number of educational/corporate places would want to be able to similarly customise the browser and desktop.

As this is the first main install I am doing of Linux here, I want to try and get it really polished.

There are a couple of other things I need to do as well, but I'll cover them separately as they are for different programs.

Thanks all!  After playing with Ubuntu again for a week, Windows feels really horrible...  :)  (I want to "sudo" all the time when fixing users' computers...)
Oh, and to anyone who worked on Beryl: I think you rock. :cool:

---

### Post by yabbadabbadont on 2007-05-30
```
/home/daffy $ ls -lR /etc/firefox/
/etc/firefox/:
total 12
-rw-r--r-- 1 root root  206 2007-04-03 09:52 firefoxrc
drwxr-xr-x 2 root root 4096 2007-05-25 18:49 pref
drwxr-xr-x 3 root root 4096 2007-05-25 18:49 profile

/etc/firefox/pref:
total 4
-rw-r--r-- 1 root root 708 2007-04-03 09:52 firefox.js

/etc/firefox/profile:
total 48
-rw-r--r-- 1 root root 27953 2007-04-03 09:52 bookmarks.html
drwxr-xr-x 2 root root  4096 2007-05-25 18:49 chrome
-rw-r--r-- 1 root root   153 2006-09-14 12:13 localstore.rdf
-rw-r--r-- 1 root root   287 2004-11-30 15:26 mimeTypes.rdf
-rw-r--r-- 1 root root   347 2004-07-28 16:20 prefs.js
-rw-r--r-- 1 root root  3287 2005-02-01 11:36 search.rdf

/etc/firefox/profile/chrome:
total 8
-rw-r--r-- 1 root root 1078 2004-11-30 15:26 userChrome-example.css
-rw-r--r-- 1 root root  663 2004-11-30 15:26 userContent-example.css

```
:D

---

### Post by BevanFindlay on 2007-05-30
I think next time I post I should use a stopwatch.  Very fast answer indeed.

Works perfectly - thank you!!! :D

I figured there was somewhere that FF was storing its default settings, but I am still too much of a *nix newbie to know where that is...

By the way, while we're on the topic, does "etc" actually stand for anything or is it literally just "etcetera"?

Thanks muchly :cool:  If I could give you something for that, I would.

---

### Post by yabbadabbadont on 2007-05-30
From wikipedia (take it with a grain of salt...):

> /etc/ 	Host-specific system-wide configuration files (the name comes from et cetera).

---

### Post by BevanFindlay on 2007-05-30
Cool. :cool:

Should help me to know where to go for similar things in future.  Cheers. :)

---

### Post by BevanFindlay on 2007-05-31
Ok, slightly tougher one: do you know if it is possible to get Firefox to use NTLM integrated authentication so that the users who are logging on to the Linux box using credentials from our Windows Active Directory server don't have to then re-enter their username and password whenever they open Firefox?

It's not a major as people can just get used to typing it again (hey, I have :)), but I do know that Firefox can do NTLM integrated authentication on a Windows box, so it could be possible...

---

