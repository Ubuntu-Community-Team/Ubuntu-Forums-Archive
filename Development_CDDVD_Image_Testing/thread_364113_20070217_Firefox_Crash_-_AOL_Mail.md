---
title: "20070217 Firefox Crash - AOL Mail"
date: 2007-02-17
forum: Development CD/DVD Image Testing
---

### Post by jerrylamos on 2007-02-17
Test: AOL mail with Firefox
Result: Fail

Rsync'd 20070217 and checked MD5sum's O.K.

Firefox ran Yahoo mail O.K., BBC news, ABC news, ...

On logging onto AOL Mail or Aim Mail (same thing) Firefox vanishes.  Try to restart and the message says: "Your last Firefox session closed unexpectedly....".  Repeats every time.

I've tried two pc's so far, same thing. I don't see anything useful in /var/log/syslog.

Any way to gather data on this?

Thanks, Jerry:confused:

---

### Post by El Viejo Lobo on 2007-02-20
Firefox vanished after downloading a video from this website: 
[http://www.kab.tv/](http://www.kab.tv/)
I found this massage too: Your last Firefox session closed unexpectedly
Started Firefox again and the same thing comes again after a download:lolflag: .

---

### Post by jerrylamos on 2007-02-20
I generated launchpad bug #86014 about this problem.  A reply suggested updating Totem (on a daily-live CD?).  Checking for updates indicated 82 packages were downlevel, including 4 mentioning totem.  I updated just the totem packages and then levels 20070218 and 20070219 could access AOL Mail.  Somehow the daily-live build was not current.

Level 20070220 works as expected for AOL mail.  I haven't checked to see if/how many packages are downlevel.

So this problem is fixed as of this afternoon.  

Cheers, Jerry

---

