---
title: "Stopping automount of Raid1 disks at startup"
date: 2012-12-09
forum: Desktop Environments
---

### Post by RED666 on 2012-12-09
After a problem with my Sitecom254 Nas 2 x2Tb disk Raid1 (gpt,xfs) I've been doing some testing on similar future scenario's. I need to find out if it's worthwhile to maintain this Nas device in my home network .

My goal at this moment is to mount the ( possibly out of sync) second disk as a new array to my pc running UbuntuLiveUsb (probably desktop distr.) But I would like Ubuntu NOT to automatically try to mount the array, c.q. the disk as this creates  problems and interferes with testing.

My question:
[SIZE=3]Is there a way to start Ubuntu where the system does NOT  try to mount recognized arrays on startup?

[SIZE=2]I think I can answer my own question, I'm completely taking over this forum!!! Yeeeh for the the newbies! But seriously [SIZE=2]please correct me when I'm wrong.[/SIZE]

[SIZE=2]Answer:
[/SIZE][/SIZE][/SIZE]
Adding the "nodmraid" kernel parameter, now I only have to find how you do that.

---

