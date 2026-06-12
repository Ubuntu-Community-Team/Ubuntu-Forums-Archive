---
title: "Dell Inspiron 1200 screen dims"
date: 2008-06-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by SVWander on 2008-06-30
I have posted this problem in Absolute Beginner but no one knew how to correct the problem. I didn't know there was a Dell forum. Anyway, the problem is in Ubuntu only. It doesn't happen in XP (when I put in the XP hard drive). I believe it might be a problem with the ac jack. Or not . . . some times when the computer is moved slightly a popping or snapping sound is heard and at the same time the screen dims so that I have to readust the screen brightness. This doesn't happen in XP.

It there a system log that would record the problem? I looked at Xorg in the system log but couldn't make heads or tails of it. It might be a power management problem. The jack might be somewhat loose and it loses ac power then the power management believes it is on battery. But I don't understand the popping or snapping sound. 

I have completely reinstalled Ubuntu 8.04 but that has not solved the problem. I have gkrellm running with Dell l8k Plugin to control the fans. Again this isn't a problem in XP. It only happens in Ubuntu. In XP the machine runs much hotter.

Anyway, has anyone had this problem with a Dell laptop?

Tim

---

### Post by sdennie on 2008-07-01
The popping noise means that the you've lost AC power.  You can disable it by going to System->Preferences->Power Management->General and uncheck, Use sounds in case of error (I think this check box is mislabel and should be more like "Use sounds on events").  You can probably also disable the screen dimming from that dialog.

---

### Post by SVWander on 2008-07-03
> **vor said:**
> The popping noise means that the you've lost AC power.  You can disable it by going to System->Preferences->Power Management->General and uncheck, Use sounds in case of error (I think this check box is mislabel and should be more like "Use sounds on events").  You can probably also disable the screen dimming from that dialog.

Thank you! The power adapter must be going out. Your suggestion helped. Now I just need to find a new power adapter. Tim

---

