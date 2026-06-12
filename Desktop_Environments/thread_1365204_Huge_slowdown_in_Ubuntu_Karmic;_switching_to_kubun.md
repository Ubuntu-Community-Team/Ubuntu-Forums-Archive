---
title: "Huge slowdown in Ubuntu Karmic; switching to kubuntu fixes it"
date: 2009-12-26
forum: Desktop Environments
---

### Post by chisser98 on 2009-12-26
Hey everyone,

Just wanted to add my issue here - I hear lots of people have had issues with the Karmic update, and I'm one of them.  My laptop has no problem with it, but my Dell desktop was getting killed by it.  I bought a new HD for my rig and installed Ubuntu 8.10, then almost immediately upgraded to 9.04 and then 9.10.  I don't recall any issues with 8.10, but once I had 9.10 all installed I started having issues.  It was weird, because sometimes it would work relatively 'okay' (I did notice the mouse 'stuttered' on the screen), but other times things would take FOREVER to load (took about 5 minutes to load Eclipse up, and only had Firefox with a few tabs open and the System Monitor running).  And the loading times were just part of it - the whole system was sluggish like mad.  I did some looking around and I guess there were issues with fan monitoring, so I disabled the 'OnDemand' option by following the 9.10 release notes, which seemed to help the issue after a reboot, but later on after I booted up another time the sluggishness was back.  I do recall sometimes it seemed to run better then other times; during the time I used Ubuntu 9.10 I installed updates usually when prompted to (and sometimes I searched for new updates), so perhaps the improvement and degradation of performance had something to do with corresponding updates for Ubuntu 9.10 I installed over the past while, I'm not sure.  Maybe with some more digging I could find a correlation for the sluggishness.  

In the system monitor, all of the processes running would make perhaps 7-8% CPU usage, but the cpu monitor would show 100% usage on one cpu and a large number on the other (I've got a P4 3.0GHz HT).  It was insanely slow.

Ultimately, this was unnacceptable.  So I thought I'd try Kubuntu, and installed it from the terminal with 'aptitude install kubuntu-desktop'.  Now when I login with the KDE session everything runs beautifully.  I haven't gone back to check the Gnome session, but I no longer have performance issues with my machine. 

I just thought some people might find this useful.

Regards,

Jarrett

---

