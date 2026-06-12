---
title: "Upgrade to 18.04, now desktop doesn't work — trying to use Nautilus"
date: 2019-10-12
forum: Desktop Environments
---

### Post by Paddy Landau on 2019-10-12
I had Lubuntu 16.04, and today I upgraded to Lubuntu 18.04.

Unfortunately, the desktop no longer works. All I have is the default background, and none of my icons (Desktop files and folders).

The [solutions that I previously used]("https://ubuntuforums.org/showthread.php?t=2364066") to enable the desktop in 16.04 don't work at all.

Note that I use Nautilus, not the default PCManFM.

How can I enable the Nautilus desktop on Lubuntu 18.04, please?

**EDIT:** I found the answer.

In Default Applications for LXSession, I had to clear Core Applications > Desktop Manager, and check the box next to Files in Autostart.

The desktop icons are huge, though. I don't know how to reduce their size.

---

