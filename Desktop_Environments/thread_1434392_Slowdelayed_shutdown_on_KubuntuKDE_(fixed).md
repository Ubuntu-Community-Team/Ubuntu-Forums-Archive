---
title: "Slow/delayed shutdown on Kubuntu/KDE (fixed)"
date: 2010-03-20
forum: Desktop Environments
---

### Post by iRiUX on 2010-03-20
I have always experienced a slow shutdown on kubuntu since the first version I tried and never figured out how to fix it. Well I found out how to fix it. I don't know if this is a problem on everyone's PC, but it has been a problem on every computer I've tried Kubuntu on, so I'm sure many more people experience this.

So if you also experience a delay of (sometimes even) 30 seconds between the time you click shutdown, and it actually shutsdown. Do the following: Disable shutdown sound (the sound you hear when you click shutdown)

K Menu > Computer > System Settings >Notifications > Event Source: KDE System Notification, then disable the sounds for **Logout** and **Login**.

KDE now shuts down instantly when I click shutdown and startup is also much faster. I don't know if I should make a note of this on launchpad. Is this problem fixed in 10.4?

---

