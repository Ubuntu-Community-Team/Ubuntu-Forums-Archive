---
title: "Application name on Launcher and Dash"
date: 2016-05-29
forum: Desktop Environments
---

### Post by slmouradian on 2016-05-29
Hi all,

I installed chromium and the first page I visited was a youtube livestream of a game. The title of that page is now the application name for chromium on both the Dash and the launcher. What happened? How can I fix this?

I checked /usr/share/applications/chromium-browser.desktop, to no avail.

Thanks,
slmouradian

---

### Post by slmouradian on 2016-05-29
FIXED: The site title had been appended in the LOCAL .desktop file, found under ~/.local/share/applications/chromium-browser.desktop

I still don't know how it got there in the first place... but at least I fixed it now.

---

