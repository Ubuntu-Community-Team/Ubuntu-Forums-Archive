---
title: "How to prevent &quot;autorun&quot;?"
date: 2008-04-11
forum: Desktop Environments
---

### Post by IainPurdie on 2008-04-11
I've had a look (on here and on the system) and can't see an obvious way to prevent this...

We have an external USB drive used as a backup device on our "server" (old PC running 6.06 desktop and the default GNOME environment). However, every time it's removed and re-attached a new File Manager window opens up. The machine is ideally left lying more or less dormant, with the desktop logged in as Admin and locked.

As it stands, when Admin logs in there are several FM windows to close which is a pain. Depending on how frequently desktop maintenance is required, this could result in dozens of the flipping things!

Is there any way to prevent these popping up?

---

### Post by Linder on 2008-04-11
I believe there's a setting in Nautilus settings....I have a different local version, but I'll try to guide you nonetheless.

Open nautilus and go to "Edit -> Settings -> Media". At the bottom of that window there should be something similar to "Browse media when connected". Untick that one and see if it helps.

---

### Post by ryanhaigh on 2008-04-11
System > Preferences > Removable drives and media. You can probably also change specific options for your device using udev-rules if you want to preserve this functionality for other devices.

---

### Post by IainPurdie on 2008-04-11
Sadly, nope. The version I have doesn't have a "Settings". It's got Preferences, but I've been right through it and there's nothing on any of the tabs relating to the problem I have.

Perhaps there's a tweak I could make to the Device Management settings for the drive? I've looked at the labels there and there is a "volume.police.mount_option.quiet" label, but that's set to "true" already. Probably completely unrelated anyway!

*UPDATE* Just got Ryan's reply - does the job, thanks for that! Now I just need to tidily "unmount" the device each night before the office volunteer unplugs the drive to store it in the safe... ;) That bit I can do!

---

