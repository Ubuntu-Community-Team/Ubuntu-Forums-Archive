---
title: "Jaunty: No updates with 'old' Intrepid behavior (auto_launch is false)"
date: 2009-06-18
forum: General Help
---

### Post by paperplate9 on 2009-06-18
Before everyone gets on me and says 'read the release notes', well I have...the day I upgraded from Intrepid to Jaunty.

While the download was going on, I already had it set in mind that I wanted the old behavior. So as soon as the upgrade to Jaunty was complete, the first thing I did was set the auto_launch value to false and  regular_auto_launch_interval to 0 (notify of updates as they come avail).

Well, no update notifications have been received in the tray at all since I made the upgrade to Jaunty almost 2 months ago. I have to manually run an update-manager 'check' or an `apt-get update`...which updates package info just fine.

With some googling, I came across the 
/var/lib/apt/periodic
directory and it seems the files in there do not get updated at all unless I do an `apt-get update` or update-manager 'check'.

So bottom line:

1. auto_launch is false
2. regular_auto_launch_interval is 0

...so why don't I get update notifications like I used to in Intrepid?

[IMG]http://img38.imageshack.us/img38/4138/41765599.gif[/IMG]

---

### Post by paperplate9 on 2009-06-19
Whoa!!! This thread is on the 18th page after just 1 day of posting this?

I wanted to post the icon/tooltip I see in the tray:

[IMG]http://img95.imageshack.us/img95/8372/outdated.gif[/IMG]

Following these instructions, lists are downloaded successfully.

---

### Post by paperplate9 on 2009-06-19
Anyone know what a checkbox with a 'dash' through it signifies? It seems in my Software Sources, "Source Code" is "dashed". I can un-dash it but when I click on it again, it turns to a check and I can't get it to come back dashed.

I think this may be the source of my problems. I've unchecked it, removed /var/lib/apt/periodic/* and /var/lib/apt/lists/* and will see if I get notification. Before I removed these files, an update-manager 'check' said that I had about 73 updates to be made, so I know that there are updates available.

---

### Post by paperplate9 on 2009-06-20
**Resolved:**

[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/356152](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/356152)

Like posted in the bug report above, my /etc/cron.daily/apt script for some reason had permissions of 644 and therefore not executable. So, the simple fix was just to chmod it to 755. But to verify that this was in fact the problem:

# /etc/init.d anacron stop
# vi /etc/anacrontab............change the startup delay (2nd column) to 0 for cron.daily
# rm -f /var/spool/anacron/cron.daily
# rm -f /var/lib/apt/periodic/update-*
# rm -rf /var/lib/apt/lists/*
# /etc/init.d anacron start

I also edited /etc/cron.daily/apt to touch a file as soon as it runs.

The touched file was created, lists popped up under /varlib/apt/lists and I got both update-stamp files in /var/lib/apt/periodic!

I then manually ran update-notifier and boo-yah....my little red arrow popped up informing me of my 73 updates!

So now I believe the problem is fixed...this is in fact a bug as I've never touched the permissions on /etc/cron.daily/apt (let alone knew that that's how auto-update-checking worked).

---

### Post by cariboo on 2009-06-20
If you want help with your problem, quit posting in the thread, as it looks like you are getting help, and some people will pass the thread by.

Why not set the updates to the default behaviour first to make sure it works, then you can change it to your liking.

---

### Post by paperplate9 on 2009-06-20
> **cariboo907 said:**
> If you want help with your problem, quit posting in the thread, as it looks like you are getting help, and some people will pass the thread by.

Why not set the updates to the default behaviour first to make sure it works, then you can change it to your liking.

I guess I can't help myself? ...no pun intended

If you say so though, since you are staff...I will just refrain from posting my own diagnosis / course of action; surprised that that's how things work around here.

---

