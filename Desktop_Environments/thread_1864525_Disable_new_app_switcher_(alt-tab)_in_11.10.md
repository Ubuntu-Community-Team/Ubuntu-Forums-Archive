---
title: "Disable new app switcher (alt-tab) in 11.10?"
date: 2011-10-19
forum: Desktop Environments
---

### Post by chrisjoha on 2011-10-19
I upgraded to 11.10, and for the most part I'm pretty happy. However, the new app switcher is causing me lots of head-aches. Is there a way to disable it to get per-workspace "normal" alt-tab like in previous versions?

---

### Post by chrisjoha on 2011-10-20
*bump*

---

### Post by justynbutler on 2011-10-20
I don't believe there is.

But you can install compizconfig-settings-manager and enable the application switcher plugin. You'll need to either disable the Unity switcher or use different shortcut keys.

I personally recommend leaving the Unity switcher as it is and using the application switcher with the shortcut keys changed to ctrl-alt-tab instead of alt-tab.

Then you can use ctrl-alt-tab when you want to switch between windows on the current workspace, without them grouped under their application icon as they are in the Unity switcher.

I think this should be added as a default, bug here: [https://bugs.launchpad.net/unity/+bug/863399](https://bugs.launchpad.net/unity/+bug/863399)

---

### Post by chrisjoha on 2011-10-22
Thanks. Based on your feedback I at least managed to replace the horrible new switcher with the application switcher plugin. This is less frustrating, but not as good as the app switcher that shipped with 11.04. I hope this change will be revisited in future versions as I think it significantly degrades the Ubuntu experience.

---

### Post by Copper Bezel on 2011-10-22
All the switchers that shipped with 11.04 are available in 11.10. You may have been using the Static Application Switcher or one of the others previously. Try them out.

In fact, the Launcher and Alt+Tab *are* getting workspace awareness in the near future, possibly for Precise in April.

---

### Post by Humphreybas on 2011-10-25
I agree with the statement made in the bug report:
> The omission of the ability to switch between windows only on the  current workspace removes some core functionality of workspaces.Since disabling the unity key binding of alt-tab was not so straight forward to me (disabling or changing did not take effect) I thought I should post here for others who encounter the same problems.

If you want to disable Unity application switcher to use another switcher:
-After disabling the unity key binding in compiz config settings restart your GDM (simply put: log out of ubuntu and then log in again).

---

