---
title: "gwibber gives 'HTTP error 400: bad request' for twitter accounts"
date: 2009-04-13
forum: General Help
---

### Post by Polygon on 2009-04-13
gwibber was working fine and dandy, until one day i could no longer get twitter updates through it, it just gives 'HTTP error 400: bad request" in the little error viewer.

My username and password are correct...and it is doing this to me in both jaunty and intrepid....any idea on how to fix it? =/

---

### Post by Polygon on 2009-04-13
bumpity

---

### Post by alienseer23 on 2009-04-13
Me too, and not just us...there's a bug in launchpad, 

[https://bugs.edge.launchpad.net/gwibber/+bug/358341](https://bugs.edge.launchpad.net/gwibber/+bug/358341)

there is a fix released, but it has not been uploaded for the stable version of gwibber for some reason. if you want the fix, use the daily release ppa.

[https://launchpad.net/~gwibber-daily/+archive/ppa](https://launchpad.net/~gwibber-daily/+archive/ppa)

or wait, and an update will appear soon.

Also, you will have to re-enter your password for twitter and identi.ca if you switch to daily, but it will work fine.

---

### Post by Polygon on 2009-04-13
this is what i was assuming, thank you for confirming it for me.

I shall just wait until it comes through the intrepid updates

EDIT: which was just today! thanks again.

---

### Post by ukblacknight on 2009-04-14
> **Polygon said:**
> this is what i was assuming, thank you for confirming it for me.

I shall just wait until it comes through the intrepid updates

EDIT: which was just today! thanks again.

I got the update today, but it still doesn't work!  I'll give the development one a go though.

---

### Post by jdeslip on 2009-04-14
I am running jaunty and have this problem.  I updated to the package in the daily-builds ppa and the problem still persists.

---

### Post by ukblacknight on 2009-04-14
> **jdeslip said:**
> I am running jaunty and have this problem.  I updated to the package in the daily-builds ppa and the problem still persists.

I've just tried the daily-builds version too, problem is still there!

I believe the problem is on Twitters end, as they've changed the API a bit.  The Gnome-do twitter plug-in isn't working for me either.

---

### Post by jdeslip on 2009-04-14
Actually, I noticed that I was now getting a 401 error (Unauthorized) instead of 400.  I deleted the account in gwibber and recreated it.  Now it seems to be working.  I wonder if it will keep working? ;)

---

### Post by ukblacknight on 2009-04-14
It's working for me now too. :)

---

### Post by Polygon on 2009-04-16
why is this still not working in jaunty? I have deleted the account and everything and it still gives me 400 bad request. this is just the one from the repos, and the one from the inrepid repos works fine....

---

### Post by ricemark20 on 2009-06-10
> **jdeslip said:**
> Actually, I noticed that I was now getting a 401 error (Unauthorized) instead of 400.  I deleted the account in gwibber and recreated it.  Now it seems to be working.  I wonder if it will keep working? ;)

Recreating the account seems to work in Jaunty.

---

### Post by EnderTheThird on 2009-06-16
Recreating the account didn't seem to work for me.  I even tried purging gwibber and reinstalling but no luck.  Still get an "HTTP Error 400: Bad Request."  I'm using the PPA and version "gwibber_1.2.0~bzr340-0ubuntu1~daily1~jaunty_all.deb"  Any ideas?

**Edit**

Turns out I might have had Gwibber updating too often.  Check this page out if you're still getting that 400 error: [http://sprayfly.com/2009/05/30/gwibber-error-400-no-twitter-updates/](http://sprayfly.com/2009/05/30/gwibber-error-400-no-twitter-updates/)

---

