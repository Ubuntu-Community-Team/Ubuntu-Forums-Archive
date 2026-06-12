---
title: "HOW TO: Fix xScreensaver Password Dialog Hidden Issue"
date: 2012-06-25
forum: Desktop Environments
---

### Post by dwitkin on 2012-06-25
GL Screensaver Issue

When I upgraded to 12.04, the xScreensaver stopped showing the password dialog box when any of the higher-end, GL screensavers were enabled (e.g., GLMatrix). The password could still be entered, but the password dialog box was not displayed.

To address the issue:
1. Open xScreensaver
2. Click Settings...
3. In the "Visual" drop down box, select TrueColor.

After making this change, the GLMatrix screensaver functions properly and shows the password dialog box as expected. I haven't tested the other screensavers, but I would think they would work also after making this change.

---

