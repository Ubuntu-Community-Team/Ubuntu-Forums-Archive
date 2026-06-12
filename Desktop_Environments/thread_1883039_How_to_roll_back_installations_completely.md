---
title: "How to roll back installations completely?"
date: 2011-11-18
forum: Desktop Environments
---

### Post by VanillaMozilla on 2011-11-18
If you install a program or package, it will often install lots of other stuff.  If you then change your mind and uninstall the program, as far as I can tell neither Synaptic nor the Ubuntu Software Center will uninstall all the dependencies.  Is there a way either to do this or to roll everything back to a previous time?

Synaptic does allow you to view the history, and in theory one could tediously uninstall each of those packages manually, but I'm hoping for a more automated way to do it.

---

### Post by ajgreeny on 2011-11-18
```
sudo apt-get autoremove
``` will do that for you, or you can use synaptic if you prefer, with the Status button in the left hand pane, and look at the autoremovable list.

---

### Post by Rex Bouwense on 2011-11-18
There are programs that you can install to get rid of all that excess stuff; Computer Janitor (which is iffy), BleachBit, and Ubuntu Tweak.  I believe the first two are in the repositories.
I was always under the impression that if you marked a program for complete removal in Synaptic that the dependencies were also uninstalled if they were not needed by another program.

+1  Forgot about that one.

---

### Post by VanillaMozilla on 2011-11-21
Thanks for the replies.  The package I wanted to get rid of was the KDE desktop, and all the applications and packages that it installed (while sparing K3b, which I had previously installed).

I did run Synaptic, and sure enough, it did uninstall some stuff.  Unfortunately, I had previously removed most of the packages by hand, so I can't tell for sure, but it probably actually did the job.

From previous experience I was not under the impression that apt-get autoremove actually did the job, but again, I can't tell.

By the way, Computer Janitor is (or at least was) part of the default installation.  Unfortunately, people seem afraid to use it because no one seems to know just what it does.

P.S.  No, marking for complete removal does not remove the unneeded dependencies.  Complete removal just means that it removes the package plus data (i.e., configuration files).

---

### Post by snowpine on 2011-11-21
This tutorial will help you completely remove KDE desktop: 

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by VanillaMozilla on 2011-11-22
Oh, very nice, thanks.

---

### Post by VanillaMozilla on 2011-11-22
That's a great Web site.  A pointer to it should be made a sticky note.

---

