---
title: "KDE 4.9.2 Dolphin force one instance multi-tabbed"
date: 2012-11-13
forum: Desktop Environments
---

### Post by manuleka on 2012-11-13
Platform:
Kubuntu 12.10

I'm wondering if anyone can help show me how to make Dolphin open in tabs instead of separate Windows?

One instance with multiple tabs...

thank you

---

### Post by ankspo71 on 2012-11-21
Hi,
I don't think it is possible to open new dophlin windows in tabs (aka single window mode), but we can use Kwin's built in tabbed windows instead.


To open Dolphin in Kwin's tabs:
Open dolphin, right click on the titlebar > More Actions > Special Application Settings;

Then click on the "Arrangement And Access" tab, then enable "autogroup with identical" and use the options "Force" and  "Yes"
Then click on the OK button.

Dolphin should now always open new windows in tabs.

You can access that rule later by going to SystemSettings > Window Behavior > Window Rules > 
"Application settings for dolphin"

Optional:
To open all windows in Kwin's tabs:
Go to System Settings > Window Behavior > Window Behavior (again) > Advanced; and then enable "Automatically Group Similar Windows" and "Switch To Automatically Grouped Windows Immediately", then click on the apply button.

---

