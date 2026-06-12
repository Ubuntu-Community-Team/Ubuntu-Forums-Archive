---
title: "App Icons Do Not (and Will Not) Display on Panel in 11.10 (64-bit)"
date: 2011-11-01
forum: Desktop Environments
---

### Post by u2nTu on 2011-11-01
Trying to get app icons for all running programs to display in the panel. Sometimes a window gets buried and it's fastest/easiest to hit its icon on the panel rather than wait for the slide-out menu, or even the alt-tab switcher. Especially true when the hand is on the pointer (mouse,...) already.

But this option is apparently unavailable under 11.10/64 (amd, if of any significance) because app icons can not be made to display on the panel. Anyone here with the same setup and with all running apps showing an icon in the panel? (Ha! I knew it was impossible.)

There are lots of bug reports related to this, but they're divided by specific app and don't address the overall problem. (At least, I can't find one that does.)

Here is the **observed behavior**:[INDENT][INDENT]     Whether by dconf tools or by simply keying ```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
``` it IS possible to alter the setting. However, after rebooting, **the setting change has no effect**. Specifying programs explicitly (replace 'all' with 'app1','app2','etc') likewise has no effect.
[/INDENT][/INDENT]Verify the setting with
```
gsettings get com.canonical.Unity.Panel systray-whitelist
```Trying to avoid an addon such as tint2. (Why consume more valuable desktop when the area for icons is already available and sitting there blank?)

Any gurus with a fix, or is this heading to the bug pile?

---

### Post by mc4man on 2011-11-01
Never had the whitelist cause any issues here though never have used the "ALL" parameter.
Prefer here to just add individually, Ex. my current

$ gsettings get com.canonical.Unity.Panel  systray-whitelist 
['Vlc', 'Amarok', 'Audacious', 'Wicd']

---

### Post by u2nTu on 2011-11-02
> **mc4man said:**
> Never had the whitelist cause any issues here though never have used the "ALL" parameter.
Prefer here to just add individually, Ex. my current

$ gsettings get com.canonical.Unity.Panel  systray-whitelist 
['Vlc', 'Amarok', 'Audacious', 'Wicd']

@mc4man, thanks for the pointer to note that explicitly specifying programs by name doesn't work either. (Have updated 1st post.) Are you also running the 64-bit version?

PS  Lockups stopped on their own. (wth?)

---

### Post by JoZ3 on 2011-11-03
Two days ago all my app icons shown in the panel,but since yesterday my aap icon from gtk apps like guake or parcellite not shown but the qt app like vlc and qbitorrent is shown

Ubuntu 11.10 64bits

---

### Post by u2nTu on 2011-11-04
@JoZ3, this is the first I've seen confirmed that anyone had panel app icons visible in 11.10/64. Don't know if it makes any difference, but my upgrade went from 10.10 directly to 11.10 and I've never had even one appear on the panel.

This does not include programs like VLC, which generate their own icon that appears in the app-indicator area (on the right side of the panel). These icons do not behave the same way as those drawn by the UI. When clicked, such app-indicator icons can offer a sub-menu (like VLC), rather than switching the focus, as they would if placed by the UI.

Your post brings hope though, that some obscure setting other than 'systray whitelist' can 'restore' the desired behavior. Just need to know what that setting is.

---

