---
title: "Sudo disables GTK-ish stuff?"
date: 2008-05-15
forum: Desktop Environments
---

### Post by AeroCross on 2008-05-15
I've been noticing that, since when I'm starting to use Themes, they deactivate when I use Sudo or I enter an Administrator Mode application (Such as Synaptic). For example:

[Image showing Synaptic in GNOME's Default config and the Firefox window and the Apps menu with the Theme Activated]("http://img160.imageshack.us/img160/6726/wtfsy4.png")

Any way to work around that?
If it helps: I have Compiz Fusion installed, using Emerald, and GTK themes.

---

### Post by watchitman on 2008-05-15
Your themes aren't deactivated. You've installed them in your ~/.themes folder, consequently, they aren't available to root. If you want them available system wide, install the themes in /usr/share/themes and icons in /usr/share/icons.

---

### Post by AeroCross on 2008-05-15
Oh, simply fabulous. Thanks a lot, it worked like wonders.

---

