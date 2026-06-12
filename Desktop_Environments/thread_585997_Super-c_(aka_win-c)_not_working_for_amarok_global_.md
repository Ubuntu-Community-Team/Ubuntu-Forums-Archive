---
title: "Super-c (aka win-c) not working for amarok global shortcut"
date: 2007-10-21
forum: Desktop Environments
---

### Post by rwh on 2007-10-21
Hi All,

Since upgrading to Gutsy, using <Super>c as an Amarok global shortcut no longer works, which is a bit strange, seeing as it's the default.  The best I can work out is that the compiz "zoom" plugin is grabbing this key to center the mouse pointer on the screen.  I can't work out how to disable this through gconf-editor, as neither compiz nor the zoom plugin have a relevant option.  Also tried searching for <Super>c in the key values, but no luck.

Actually, after further testing, <Super>v doesn't work either, it appears to refresh the screen.  All the other amarok global shortcuts are working for me though.

Any ideas?

Thanks,

Rob

---

### Post by rogeer on 2007-10-22
Had the same problem. I fixed it by instaling compizconfig-settings-manager, it wasn't installed after upgrade. Then System->Preferences->Advanced Desktop Efects Settings and there you can disable at all the Enhanced Zoom Desktop or change it's shortcuts. After that i had to restart Amarok and it works just fine now.
Hope it helps:)

---

### Post by rwh on 2007-10-22
Thanks!  That worked perfectly.

The procedure was as you said, the specific options being:

Acessibility->Enhanced Zoom Desktop->Actions->General->Fit the window to the zoom level
Acessibility->Enhanced Zoom Desktop->Actions->Mouse Behavior->Center the mouse

Restarted Amarok, and now it's all working fine. :)

---

### Post by zappa on 2007-10-23
Thanks a lot! Perfect solution, and compizconfig-settings-manager is good for so much more ;-)

---

