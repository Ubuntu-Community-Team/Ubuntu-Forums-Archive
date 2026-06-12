---
title: "System stalling for several minutes"
date: 2009-05-10
forum: General Help
---

### Post by pronik on 2009-05-10
I'm having a rather annoying problem for about a week now and I'm not sure whether it's hardware or software. Essentially, my computer stalls for several minutes every now and then, sometimes four or fives times in the course of 8 hours.

This stalling is not a complete one. Most of the times I can still switch workspaces, start terminals and start rather simple things like 'top'. What I can't do however is kill them -- quitting top seems to wait for something, exiting a terminal too, trying to kill an application hangs too. Firefox hangs in a loop, music still plays with Rhythmbox, sometimes with track changing, sometimes it hangs after one track.

So my system is essentially useless, but obviously still working. Most annoying symptom is console beeping -- if I induce a beep (e.g. with bash completion) the beep doesn't stop until system becomes "normal" again in several minutes. Everything I "ordered" get executed then, so no command was lost, it just waited for something.

'top' doesn't show any significant activity, 'iotop' neither, there is nothing of matter in either 'dmesg' or '/var/log/messages' or '/var/log/syslog', 'vmstat 1' doesn't show any difference to "normal" situation. CPU and mainboard temperature are normal (about 35C according to sensors), SMART doesn't tell me anything about about-to-be-dead hard drive.

I'm using Jaunty 9.04, 64-bit, awesome window manager. Please post even your wildest ideas, since I'm currently out of them. What can I check next?

---

### Post by Indian Summer on 2009-05-10
Could it be the "tracker" application? (It's some kind of file indexing application.) You can pause it by right-clicking on the magnifying glass icon on your panel and selecting "Pause all indexing". Does that make the stalling go away?

---

### Post by vahnx on 2009-05-10
Did this happen since day 1, does it happen on the Live portion of the disc? Also, if you have multiple OS's on that machine, do they also hang?

---

### Post by pronik on 2009-05-10
> **Indian Summer said:**
> Could it be the "tracker" application? (It's some kind of file indexing application.) You can pause it by right-clicking on the magnifying glass icon on your panel and selecting "Pause all indexing". Does that make the stalling go away?

I've also tried it without tracker, to no avail. Even if tracker had caused this, I'd see something sensible in 'top', which is not the case.

---

### Post by pronik on 2009-05-10
> **vahnx said:**
> Did this happen since day 1, does it happen on the Live portion of the disc? Also, if you have multiple OS's on that machine, do they also hang?

This is something I noticed this week. The system itself has been reinstalled half a year ago (upgrade to 64-bit) and since then upgraded to jaunty beta (daily updates since then). No other OSs, can't say anything about live system, since I haven't used that longer that a couple of minutes.

---

