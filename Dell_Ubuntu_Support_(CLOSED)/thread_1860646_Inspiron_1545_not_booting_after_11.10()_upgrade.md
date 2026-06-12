---
title: "Inspiron 1545 not booting after 11.10(?) upgrade"
date: 2011-10-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hungrypanda on 2011-10-15
Hi:

I have been running Natty on my Dell Inspiron 1545 for a while now.  This morning, while the update manager popped up, I notice there was a new version for upgrade.  I *think* it was 11.10, but I didn't pay very close attention.  I just clicked on it.  I know, I know, I should have backed up, and I should have perhaps waited for a more stable release..  but that's all spilt milk now... sigh

Anyways, I let the update run in the background, and later I rebooted as it says it required.  I was expecting wireless to not work, but I was not expecting the machine to not boot fully into ubuntu.  What's happening is the following:

* The Dell Inspiron logo shows up on hitting the power button
* Then it switches to the text screen and looks like it's starting services (such as apache)
* Then it starts shutting services down and just freezes (I let it run about 10 mins?)

The last printout reads
* Stopping save kernel messages
* stopping anac(h)ronistic cron

The only other anomaly I noted is that the status of one the printouts is 

[fail] stopping automatic crash report generation.

The rest of the printouts all have okay status.

I searched but was not able to find any related solutions.  Can someone please help?  This is my work computer and I would love to have it back up before monday.

-thanks so much
Annie

---

### Post by hungrypanda on 2011-10-17
Okay, so this is what I ended up figuring out.

It seems that the anac(h)ronistic cron was the thing that was causing the GUI to not boot up.  I found it in this thread.

[http://ubuntuforums.org/showthread.php?t=948064](http://ubuntuforums.org/showthread.php?t=948064)

So i ended up booting into recovery mode (I had pick a version that was a couple back for the boot to work for some reason).   Then from command line, I was able to do a sudo apt-get remove anacron.  Although I had to do a dpkg --configure -a before that for apt-get to work also.

I think though anacron is used during shut down or something, because now the machine does not shut down properly.  But at least now it is mostly working.

---

