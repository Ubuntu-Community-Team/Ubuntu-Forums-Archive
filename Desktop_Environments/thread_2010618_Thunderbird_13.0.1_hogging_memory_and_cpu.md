---
title: "Thunderbird 13.0.1 hogging memory and cpu"
date: 2012-06-25
forum: Desktop Environments
---

### Post by klb1953 on 2012-06-25
Hi

As of a few days ago, Thunderbird was updated via update manager to Thunderbird 13.0.1.  I am using ubuntu lucid  10.04.  Thunderbird now very quickly consumes memory to over 40% and cpu varying but 30% or more making the whole system sluggish.  Seems to start when reviewing messages in the inbox.  Exiting Thunderbird restores performance.  Attached is display from top showing memory and cpu usage.  Is this a known issue?  Are there any workarounds for it?

TIA
Ken

---

### Post by ray field on 2012-07-08
Same problem here, looking for confirmation/resolution.

---

### Post by klb1953 on 2012-07-18
Thunderbird now upgraded to 14.0 but problem still exists.  Seems to happen when the preview pane is on.   Any thoughts appreciated.

TIA

---

### Post by pqwoerituytrueiwoq on 2012-07-18
what addons? no issues here, except the lightening addon is not in the repos yet

---

### Post by Frogs Hair on 2012-07-18
I'm at roughly 5.5% memory for Thunderbird 13.0.1 . The CPU under 10% with Opera and Thunderbird running on 12.04 . I have no large folders in Thunderbird though and use Lightning and Enigmail.

---

### Post by Warthaug on 2012-07-19
I have the same issue, with both verson 13 & 14.  Thunderbird sucks up anywhere from 300MB to 1GB of memory, and seemingly at random ramps up CPU usage.

I have lightening and google contacts sync plugins installed.

Any ideas/fixes are welcome.

Bryan

---

### Post by pqwoerituytrueiwoq on 2012-07-24
This is everything i am using and i am having no issues (Thunderbird 14.0 + Ubuntu 10.04 64bit)
[[IMG]http://i.imgur.com/jLLwJl.png[/IMG]]("http://i.imgur.com/jLLwJ.png")
using this ppa
[https://launchpad.net/~mozillateam/+archive/thunderbird-stable]("https://launchpad.net/%7Emozillateam/+archive/thunderbird-stable")
BTW I keep Thunderbird open all day

---

### Post by klb1953 on 2012-08-16
After much googling, I stumbled upon the fact that the inbox, despite only having less than 50 messages was about 900Mb in size.  Compacting did not help so I created a new folder and moved everything to it.  New folder size 1.5mb.  Compacted inbox still at 900Mb.  Restarted thunderbird and inbox folder size still 900Mb.  Moved all the messages back to the inbox and the problem seems to be solved.

Hope this helps others with similar issue.

Ken

---

### Post by verwaltungspraxis on 2012-09-23
Close TB, delete the file  global-messages-db.sqlite from your profile folder and start TB again. 

[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1039837](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1039837)

If it the problem comes back after a while, turn off global message indexing. They will hopefully fix this soon.

---

