---
title: "how to enable auto suspend after inactive for 30 min"
date: 2009-02-08
forum: General Help
---

### Post by afeasfaerw23231233 on 2009-02-08
In System -> Preference -> Power Management Preferences it only shows "Put computer to sleep when inactive for ..." but no suspend to RAM option. Thanks in advance.

---

### Post by utnubuuser on 2009-02-08
That's a laptop feature isn't it? If your comp isn't a laptop, maybe check in synaptic for "laptop".  There are laptop specific apps that you might be able to implement on a desktopPC.

---

### Post by sdennie on 2009-02-09
It should be suspend to RAM by default.  If it isn't, hit Alt-F2, run gconf-editor and go to /apps/gnome-power-manager/actions.  Change sleep_type_ac and sleep_type_battery to "suspend".  If you click on the keys, it will give you information about them.

---

### Post by afeasfaerw23231233 on 2009-02-10
Thanks!

---

