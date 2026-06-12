---
title: "Remove the &quot;create launcher&quot; menu at right click on desktop"
date: 2009-07-06
forum: Desktop Environments
---

### Post by chang5562 on 2009-07-06
I tried the following method to remove the "create launcher" menu from right clicking on desktop but it won't work.

modify /usr/share/nautilus/ui/nautilus-desktop-icon-view-ui.xml
and add hidden="true" to line:
<menuitem name="New Launcher" action="New Launcher Desktop"/>

as this way:
<menuitem name="New Launcher" action="New Launcher Desktop" hidden="true"/>

I have both 8.10 and 9.04 version. Did I miss anything?

---

