---
title: "unity:  drop down menu from the gear icon in the far upper right"
date: 2016-06-18
forum: Desktop Environments
---

### Post by Skaperen on 2016-06-18
in *unity* there is a drop down menu from the gear icon in the far upper right corner that shows "_About This Computer_" and "_Ubuntu Help..._" and "_System Settings..._" and "_Lock/Switch Account..._" and "_Guest Session_" and a list of currently logged in users.  it remembers users previously logged in and shows them, too.  it shows no more than 12 users.  **is there a way to increase that maximum?  is there a way to customize the list of not-yet-logged-in users?  how can i find out what program code controls the set-up of this menu?**

---

### Post by mc4man on 2016-06-18
rebuild indicator-session source, install new build, better done as a .deb

The line controlling is in  src/service.c line # 1530 - (16.04, # may vary on earlier releases but in there..

```
properties[PROP_MAX_USERS] = g_param_spec_uint ("max-users",
                                                  "Max Users",
                                                  "Max visible users",
                                                  0, INT_MAX, [COLOR="#0000CD"]12[/COLOR],
                                                  G_PARAM_READWRITE |
                                                  G_PARAM_CONSTRUCT |
                                                  G_PARAM_STATIC_STRINGS);
```

---

