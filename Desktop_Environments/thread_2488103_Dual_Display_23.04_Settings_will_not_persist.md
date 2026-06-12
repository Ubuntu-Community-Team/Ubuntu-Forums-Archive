---
title: "Dual Display 23.04 Settings will not persist"
date: 2023-06-23
forum: Desktop Environments
---

### Post by name5 on 2023-06-23
Gnome desktop with no intermittent cables continuously reverts display location on login, and often while logged in. Frequent logins result in: "Oh no! Something has gone wrong. A problem has occurred and the system can't recover. Please log out and try again." This is followed by: "rc.local Error opening display!" This error may persist across multiple logins, but eventually a login (with the wrong display layout) succeeds. The layout can be fixed temporarily using arandr at the command line. This issue did not exist with 22.10. One attempted fix was to save the arandr file as .xsession. This caused an endless loop of the "Oh no!" sequence. Saving the file as .xsession.sh and running it after logging in fixes the screens, albeit temporarily. Is there a method to get the displays in the proper position on login that persists, or must it occur post login repeatedly, for example via cron?

---

