---
title: "Time inconsistency between terminal and desktop"
date: 2005-07-23
forum: Desktop Environments
---

### Post by rosslaird on 2005-07-23
I'm having this weird problem with the time that is displayed on my desktop and on my terminal. This problem began yesterday, after the most recent hoary dist-upgrade (I dist-upgrade whenever there are new packages, so this recent one was only a few packages).

Here's the deal:

In gnome or xfce, the correct time is displayed (I use the xfce time plugin for the panel and it works perfectly). However, I also run the z shell in my terminal windows, and my shell prompt, which shows the current date and time, now displays a time that is 16 hours ahead. The time is accurate, but it's been shifted by a bunch of time zones.  This is not a z shell issue, as the prompt worked fine until yesterday.

When I check the time zone from the terminall window (tzconfig? I can't remember, I'm not at my machine), it shows the correct time zone -- Pacific time. But the z shell prompt seems to show another timezone, JHS or something like that.

Anybody know what's going on?

Ross

---

