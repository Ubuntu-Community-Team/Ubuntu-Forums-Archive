---
title: "KPackageKit Update Notifications"
date: 2009-11-12
forum: Desktop Environments
---

### Post by Scarfy on 2009-11-12
Whenever I have system updates, the update icon appears in the system tray for only a couple of seconds before it vanishes. I therefore have to manually refresh in KPackageKit to find out if I have updates.

I've heard this might be a bug in the system tray or something? But does anyone have a fix at all?

I upgraded from Ibex; so this wasn't a fresh install, if that helps.

---

### Post by mrboojive on 2009-11-12
That sounds like the normal behavior for when KPackageKit checks for updates but you do not have any. When you go KPackageKit after you see the icon in the taskbar do you find that you actually do have updates? Have you ever gotten the popup with the picture of a bug that tells you that you have updates?

---

### Post by Scarfy on 2009-11-12
Yep.

If I go into KPackageKit, go to Software Updates and do a Refresh, I will get a list of updates that are available. However, even then there won't be an icon in the system tray.

So, a system tray icon will only show for a brief couple of seconds when there are updates. And, of course, if you happen to not be paying attention, then you'll never know.

And, yes, in KPackageKit -> Settings, I have Notify when updates are available checked. I've even unchecked it, rebooted, re-checked it, rebooted, but it makes no difference.

Anyone know if this is a known bug?

---

### Post by mrboojive on 2009-11-12
Your problem sounds a lot like this bug report: [https://bugs.launchpad.net/kdebase/+bug/342017](https://bugs.launchpad.net/kdebase/+bug/342017), which is supposed to be fixed in Karmic. Are you running Karmic or Jaunty?

---

### Post by Scarfy on 2009-11-12
Yes, that describes it exactly, unfortunately.

I'm running Karmic. I did upgrade from Jaunty, though, so perhaps it's something that's carried over..?

---

### Post by Scarfy on 2009-11-12
Actually, it might be that I'm expecting to see an icon rather like there was in Jaunty and KDE 4.2. Apparently it's now a (1) that appears in place of the i in the notification area. Hmmmmm.

---

