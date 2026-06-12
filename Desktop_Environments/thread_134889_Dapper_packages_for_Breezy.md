---
title: "Dapper packages for Breezy?"
date: 2006-02-22
forum: Desktop Environments
---

### Post by jchau on 2006-02-22
I'm trying to get naim to work (so I can run aim through ssh without firing up X).  However, the Breezy repositories have an old version of naim (0.11.7.3.1-1) & naim refuses to connect since it detects that a newer version is available.  After checking a bit, I found that Dapper has the newest naim available (0.11.8-1).  (Source of my info is [http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=naim](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=naim))

Is there a way of adding the Dapper repositories to my sources/list of repositories?  Is it safe to install Dapper packages on a Breezy system or will it mess up my system?  

I know I can just download the naim package from the website named above, but I want to do it through apt-get or (preferably) Synaptic so it can get all the dependencies.  

I would also like to know if it is safe to add the Dapper package repositories to my source list & get the latest packages.  If it is safe, what do I accomplish this?  What repositories do I add?

I'm not ready to try Dapper yet, but I like my packages to remain up-to-date.  Is there a special repository for this?

Thanks!

---

### Post by RAOF on 2006-02-22
It's not safe to add Dapper repositories.  You'll end up getting a strange Breezy-Dapper hybrid which may or may not work (and will likely work *less* than just Dapper).

The "backports" repository is just what you're looking for (check out the Backports Forum).  If they haven't backported it, you can request it and they might :)

---

### Post by jchau on 2006-02-22
Well, I have this line is my /etc/apt/sources.list:```
deb http://archive.ubuntu.com/ubuntu breezy-backports main universe multiverse restricted
``` I think this is for the backports.  However, I still can't find the updated naim.  Is this line correct?  If it is, how do I request a backport for naim?

Edit: I found how to request a backport. 

-Jimmy
BTW, thanks for your reply!

---

### Post by jchau on 2006-02-22
Well, I'll just sit back and wait.  My request is in [http://www.ubuntuforums.org/showthread.php?t=134926](http://www.ubuntuforums.org/showthread.php?t=134926) .

---

