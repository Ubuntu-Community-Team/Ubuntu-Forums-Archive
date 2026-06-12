---
title: "Ubuntu not saving settings"
date: 2009-04-10
forum: General Help
---

### Post by Roberto_Lapuente on 2009-04-10
Hi, just a few hours ago i was using my computer (wit ubuntu) and restart it because some downloads ask for it and when i log in again my desktop background, my window theme and my panel configuration was set to ubuntu 8.1 default, and also my firefox settings were set to default and every time i open it it displays the tabs of the plugins just as if it had just updated. this happens every time i restart my computer or open firefox again.

---

### Post by dcstar on 2009-04-10
> **Roberto_Lapuente said:**
> Hi, just a few hours ago i was using my computer (wit ubuntu) and restart it because some downloads ask for it and when i log in again my desktop background, my window theme and my panel configuration was set to ubuntu 8.1 default, and also my firefox settings were set to default and every time i open it it displays the tabs of the plugins just as if it had just updated. this happens every time i restart my computer or open firefox again.

Boot off a live CD and run a fsck on the "/" partition.

---

### Post by midtoad on 2009-06-13
@dcstar, running fsck is likely irrelevant. He's not having any file integrity problems.  Instead, his problem (and mine) is likely related to permissions on the file that stores the panel layout.

---

