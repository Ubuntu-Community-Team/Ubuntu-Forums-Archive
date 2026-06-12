---
title: "hard lock up after upgrade"
date: 2009-05-29
forum: General Help
---

### Post by afderrick on 2009-05-29
So after I have upgraded to the most recent upgrade of Ubuntu every now and then my machine locks up hard.  I cannot restart X by doing the Ctrl Alt Backspace, I can't even use the alt sysreq reisub to restart it in that manner.  The only way I can restart it is be powering it down on the box itself.

I have looked through all my logs and cannot find anything indicative of it.  I also downgraded my nvidia driver to 173 from 180 since I thought that may fix it.  nothing has fixed it so far.  I cannot find anything on the Internet to help me.

Can anyone out there help me or should I just try and downgrade back to 8.1?  There is nothing common about the times it locks up, I can have any combination of apps open.

---

### Post by quixote on 2009-05-30
This seems to be a jaunty problem affecting some people, which, as far as I can tell, the ubuntu devs are ignoring. :-x

I have no solution because I have the same problem, and just had to go back to 8.10.

There are two threads about it on the forums (eg [http://ubuntuforums.org/showthread.php?p=7308336](http://ubuntuforums.org/showthread.php?p=7308336)) and a bug report that's not getting much attention: [https://bugs.launchpad.net/jaunty-backports/+bug/372526](https://bugs.launchpad.net/jaunty-backports/+bug/372526) .  If you think yours is the same problem, you might want to add your data to the bug report.  Maybe we could finally get someone moving on this!

---

### Post by afderrick on 2009-05-31
Appreciate it.  I'll have to go back and figure out how to downgrade back to 8.1 later this week.  I'll also go add my info to the bug report list as well.  Maybe if enough people show up with the problem someone can look into it.  If I had any ideas as to OS programming I'd look into it, but I'm certain it is well over my head.

---

### Post by quixote on 2009-05-31
I just got a message saying the bug has been marked a duplicate of this one: [https://bugs.launchpad.net/bugs/346691](https://bugs.launchpad.net/bugs/346691)

Nice to know they're starting to look at it!

I didn't know you could downgrade.  I did a clean install back to 8.10, and spent days getting my settings and programs back.  Never quite got it, either.  Very annoying!

---

### Post by quixote on 2009-06-01
Looks like [we may have a fix]("http://ubuntuforums.org/showpost.php?p=7382178&postcount=29").  It involves upgrading the kernel on the jaunty install, but that's surprisingly easy to do.  At least, it was surprising for me!

---

### Post by afderrick on 2009-06-01
Unfortunately the fix is for 64-bit.  I"m still running a 32 bit.

---

### Post by kemorc on 2009-06-01
I dono what the heck is wrong, but Jaunty should not have been released to the public.  I've had nothing but problems with it with lockups, lockups DURING reboots and games run ridiculously slow.  Making this post and downgrading to 8.10.

---

### Post by quixote on 2009-06-02
Yes, the fix is for 64-bit, but if you substitute the 32-bit package, then it works for 32-bit.  In other words (the linked comment says that, but maybe not clear enough): 

substitute _i386.deb at the end of the file name where it has _amd64.deb

---

### Post by afderrick on 2009-06-03
I did that, I guess over the next few days we will see if it worked or not.  One thing it did for me, was now I cannot use the proprietary nvidia drivers.  When I activate them if I restart it pops up that it didn't like it and makes me go to a basic settings.  Not so annoying except I'm also noticing my fonts look fuzzy too.

---

### Post by quixote on 2009-06-03
*now I cannot use the proprietary nvidia drivers*.  Sometimes it really is always something :-(

I'm sure the new improved drivers will surface one of these days . . . probably about the time the koalas come out.

---

### Post by afderrick on 2009-06-04
I guess we will see.  I only have one game I can't play and then I can't enable compiz but I leave that turned off all the time anyway.  I stayed up all night.  I appreciate the help.

---

