---
title: "Display issues after switching to Xubunto Oneiric"
date: 2012-02-22
forum: Desktop Environments
---

### Post by arvana on 2012-02-22
I recently upgraded to Oneiric and switched to XFCE -- I had been using Maverick until then to avoid Unity.  After doing a lot of configuring, things are mostly working and I'm generally very happy with this system. But there are some odd display freezes that keep happening.

Seemingly randomly, both Firefox and Thunderbird will just freeze up for about 10 seconds; I can't click or scroll anything in the window. But there is no extreme CPU or memory usage when that happens.

Similarly, whenever I play video -- either a Flash video in a browser, or a video file in VLC / mplayer -- it freezes for some time before it will play, after which it plays normally.

I've tried everything I can think of to solve this, but honestly I don't really know what I'm looking for, and I haven't been able to find anyone else who has had / solved this problem. I'd rather not start from scratch with a clean install unless I absolutely have to, because it takes a lot of work to configure my RAID card and other custom setups.

Any ideas or pointers to try to solve this problem would be very appreciated! Thanks. :)

---

### Post by cottfcfan on 2012-02-22
If you've upgraded & then added xfce desktop on top of unity, that may be your problem.
All I can suggest is download Xubuntu 11.10, run the live cd and see if you still get the issue.
If not, then maybe a fresh install is the way to go.
Upgrades are fraught with problems for some.

---

### Post by arvana on 2012-02-22
Are there any packages I can uninstall that might be interfering with XFCE and causing this behaviour?  A new install is my last resort, as I have a lot of customizations in my current install that I would have to redo. Thanks.

---

### Post by LewisTM on 2012-02-22
> **arvana said:**
> Are there any packages I can uninstall that might be interfering with XFCE and causing this behaviour?  As I said, a new install is my last resort. Thanks.
You can use Psychocat's master command to remove non Xubuntu packages.
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)
After that, if you find that you are missing something, you can always reinstall it.
Are you sure it's caused by Xfce? If you have another DE installed like Unity, you could log into that session and see if you have the same issues.

---

