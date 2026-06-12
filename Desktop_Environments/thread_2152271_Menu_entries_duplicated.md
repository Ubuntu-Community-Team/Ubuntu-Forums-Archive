---
title: "Menu entries duplicated"
date: 2013-06-07
forum: Desktop Environments
---

### Post by Andrinho7 on 2013-06-07
Hi guys,
I just installed Lubuntu 13.04 and since the icon size of the menu entries of lxpanel cannot be modified I installed fbpanel. I want to use fbpanel menu so I have deleted the menu from lxpanel.
The problem is that all fbpanel menu entries are duplicated. And I mean all of them. So I have two gimp entries, two leafpad entries and so on. What can I do?
I checked /usr/share/applications and there are no duplicate files there. I also checked my /home/USER/.local/share/applications and the folder is empty.
Any suggestions?

---

### Post by vasa1 on 2013-06-07
from apt-cache show fbpanel:
Description-en: lightweight X11 desktop panel
 FBPanel is a spinoff of the fspanel with more eye
 candy.  It provides a taskbar (list of all opened windows), desktop
 switcher, launchbar, clock, is EWMH/NETWM compliant, and has modest
 resource usage.

---

### Post by Andrinho7 on 2013-06-07
> **vasa1 said:**
> from apt-cache show fbpanel:
Description-en: lightweight X11 desktop panel
 FBPanel is a spinoff of the fspanel with more eye
 candy.  It provides a taskbar (list of all opened windows), desktop
 switcher, launchbar, clock, is EWMH/NETWM compliant, and has modest
 resource usage.

So?

---

### Post by vasa1 on 2013-06-07
> **Andrinho7 said:**
> So?
We wait. I'd have done what you did. Can't think of anything else.

---

### Post by Rex Bouwense on 2013-06-07
LXPanel is configurable.  Just right click on any open space on the panel and choose Panel Settings->Geometry.  From there you can configure the panel size and the icon size.

---

### Post by Andrinho7 on 2013-06-07
> **Rex Bouwense said:**
> LXPanel is configurable.  Just right click on any open space on the panel and choose Panel Settings->Geometry.  From there you can configure the panel size and the icon size.

Yes, in fact I have lx panel with a 48 px height and 46 px icons. But that doesn't affect the menu icons. I'll show you the difference restoring lxpanel's menu for a moment.

[http://img19.imageshack.us/img19/5281/fbpanelvslxpanel.png](http://img19.imageshack.us/img19/5281/fbpanelvslxpanel.png)

As you see I have both panel the same dimension but in fbpanel I can modify menu's icon size (actually 36). In lxpanel I can't.

---

