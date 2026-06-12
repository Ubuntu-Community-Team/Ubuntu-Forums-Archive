---
title: "Virus alert with fresh install of ibex"
date: 2009-02-23
forum: General Help
---

### Post by kaarnijoki on 2009-02-23
Hello everybody.


Ran Clamtk and got two virus warnings. Did a fresh install and got the same hits: Virus found in all log files under /var/log/gdm/ as well as files under /var/lib/ucf/cache..

Does anyone have an idea what these files are for? Are they safe to delete or am i panicing for nothhing? 


Thank You


Use the Force



P

---

### Post by mb_webguy on 2009-02-23
Could you post the exact results of the ClamTk scan?

I think you're probably getting a couple of false positives, in which case you shouldn't delete anything -- especially outside of your home directory.  On the other hand, if they're not false positives, then you might as well delete the offending files if they're not necessary.  On the gripping hand, it's highly unlikely that they could do any harm anyway, so you might as well leave them alone.

But without knowing exactly what ClamTk is telling you, I can't say for sure.

---

### Post by kaarnijoki on 2009-02-23
Hi there. 

Clamtk really doesnt give much away. Log says:

Found 2 possible viruses (7841 files scanned).

/var/log/gdm/                                                         0.log.2
/var/lib/ucf/cache/       


First ones (../gdm/0.log and 0.log2) look like startup log files.

Others, look like clamtk config log files or something. Here list of files: :etc:clamav.clamd.conf
          :etc:clamav.freshclam.conf
          :etc:foomatic:filter.conf
          :etc:samba:smb.conf
          :etc:sensors.conf


What do you thik?



Thanks again


P

---

### Post by WatchingThePain on 2009-02-23
It is possible to get a virus on a fresh install. Some viruses keep logs.
Use a strong password, don't set a root password..what can they do?.
I think just go ahead with the install then get some good av tools. Use your firewall to see if anything dodgy is going on.
So where is the virus from?, bad installation media, it's somehow linked to your ip address or does the hard disc have an existing virus?. p.s. clam only scans the home folder by default.

---

### Post by kaarnijoki on 2009-02-23
Thanks for tips


Yes. Firewall is up and not giving any unusual alerts.

Going to download new copy of Ibex direct from Canonical and re install. Should do the job i hope?

Please feel free to post more tips if think of any. 

Enjoy the spring.



P

---

### Post by lykwydchykyn on 2009-02-23
Based on long experience with clamav, I'd almost certainly say you have a couple false positives there. If clamtk isn't giving you much info, pop open a console and run "clamscan filename" on the files mentioned, then post the output here.

---

### Post by WatchingThePain on 2009-02-23
It all looks like false positives.

---

### Post by kaarnijoki on 2009-02-24
Thank you everybody. 

Ran the clamscan from console and got clear result. Funny how you get different result when running same program from terminal.

Many thanks to all of you.


Use the force


P


Ps.  How do you mark the thread solved? Cannot find the button anymore..

---

### Post by john183 on 2009-02-24
It's under the thread tool menu at the top of the page.

(My mistake, it's not there. I guess they moved it recently. I found it there last time i closed out one of my threads.)

---

### Post by sisco311 on 2009-02-24
> **kaarnijoki said:**
> ...


Ps.  How do you mark the thread solved? Cannot find the button anymore..

The Thanks and Mark as Solved features are temporarily disabled while database issues are resolved.

---

