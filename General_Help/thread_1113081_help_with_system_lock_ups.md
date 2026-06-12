---
title: "help with system lock ups"
date: 2009-04-01
forum: General Help
---

### Post by sydbat on 2009-04-01
Hardy 8.04

This morning my box locked up as I was about to post on these forums. It was very strange and I had to hard power off. One of my HHD's was very active just before the lockup.

When I rebooted, I went to check the HHD that was active and found a file that was not there yesterday. It is **.windows-serial**. Checking the 'Properties', it says "Modified Feb 24 2009" and "Accessed today (April 1)". I have found at least one other file like this that says it was accessed yesterday (March 31). They are in different folders on different HHD's.

Looking at the file itself, there is only a number (0).

Is this some type of Windows based malware? That it might be the cause of my computer locking is disturbing.

I have run rkhunter and chkrootkit, with both showing nothing. Any other things I should run to find what this file is? Could this be part of that Conficker worm affecting Windows boxes?

I will install clam and run it to find other instances of this file, if indeed it is malware.

Please let me know ASAP. Thank you.

EDIT - I have also noticed a .sudo_as_admin_successful files in the same folders as the .windows-serial files. Now I am wondering if my system has been compromised.

---

### Post by sydbat on 2009-04-01
I did some Goggling and think I figured out the two files...

.sudo_as_admin_successful seems to be the file that tells Ubuntu to not show a message about how to use sudo - [http://ubuntuforums.org/showthread.php?t=241011](http://ubuntuforums.org/showthread.php?t=241011)

.windows-serial seems to be associated with wine, but I do not know why it is not in the wine folder.

Still trying to figure out why my box locked up randomly though. It has never done this before (been using Ubuntu for over a year exclusively, and had XP for 2 years before with no lockups).

---

### Post by bodhi.zazen on 2009-04-01
I think you are jumping to conclusions. 

.sudo_as_admin_successful is normal, you get that when you use sudo.

.windows-serial has been present for a while, from the time stamp. I do not know what that is though.

Sounds like a hard ware problem. Could be a problem with your video or wireless drivers (I have seen this with nvidia and wireless drivers) so who knows.

As such, I am moving this thread to general help and changing the title.

---

### Post by sydbat on 2009-04-01
> **bodhi.zazen said:**
> I think you are jumping to conclusions. 

.sudo_as_admin_successful is normal, you get that when you use sudo.

.windows-serial has been present for a while, from the time stamp. I do not know what that is though.

Sounds like a hard ware problem. Could be a problem with your video or wireless drivers (I have seen this with nvidia and wireless drivers) so who knows.

As such, I am moving this thread to general help and changing the title.OK. Thanks.

---

