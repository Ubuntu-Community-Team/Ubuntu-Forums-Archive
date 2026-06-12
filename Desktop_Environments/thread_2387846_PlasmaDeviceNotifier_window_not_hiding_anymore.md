---
title: "Plasma/DeviceNotifier window not hiding anymore"
date: 2018-03-24
forum: Desktop Environments
---

### Post by Chip88 on 2018-03-24
Hi there,

when I used to plug in an external device the Plasma / Device Notifier window poped up and hided itself after a few seconds.

Since some days – obviously since the laste update - the notifiere doesn't hide anymore at all. It stays open and open...

Anyone any idea how to get the notifier to auto hide again?

I am running Kubuntu 16.04.4 LTS, kernel version [FONT=monospace][COLOR=#000000]4.4.0-116-generic. 
[/COLOR][/FONT]
Thank you in advance for your help!

Chipy

---

### Post by thehipho on 2018-03-24
What happens if you just change a different plasma theme?

---

### Post by Chip88 on 2018-03-24
Hi thehipho,

what do you mean by changing a different plasma theme?!

---

### Post by thehipho on 2018-03-24
There are a lot of themes you could install from [https://store.kde.org/browse/cat/121/ord/latest/]("https://store.kde.org/browse/cat/121/ord/latest/")

Or just by going to System Settings > Workspace themes > Look and feel. Click on the “get new looks”

---

### Post by Chip88 on 2018-03-25
Hey thehipho,
I changed to different plasma themes (I used all the pre-installed ones), but the notifier still didn't hide.

Any further ideas?!

Thanks in advance,
Chipy

---

### Post by thehipho on 2018-03-25
> **Chip88 said:**
> Hey thehipho,
I changed to different plasma themes (I used all the pre-installed ones), but the notifier still didn't hide.

Any further ideas?!

Thanks in advance,
Chipy

Hi Chip88,

The pre-installed ones usually work the same, but try going with new plasma theme download option!

---

### Post by Chip88 on 2018-03-26
Hey thehipho,
I downloaded different new themes, installed them and even logged out and in again, but the notifier still didn't hide - with none of them. :mad:


This starts to drive me crazy!

I remembered today, that I had this problem already once: [https://ubuntuforums.org/showthread.php?t=1945082&p=11785301](https://ubuntuforums.org/showthread.php?t=1945082&p=11785301) .

Thanks in advance for any futher help,
Chipy

---

### Post by springshades on 2018-03-28
This is probably a dumb suggestion that you've already tried, but just in case.

If you right click on the notification area of the KDE bar, in particular the little arrow that you click to show "Status & Notification", there should be a "System Tray Settings" Option. If you go to "Entries", is it possible that the "Visibility" setting for the "Device Notifier" has been changed from the default "Auto" to "Shown"? You may also want to check in the Notifications Settings in the main system settings just in case anything there was changed that might effect things.

---

### Post by Chip88 on 2018-03-29
Hi spingshades,

thanks for your reply.
I checked already the "visibility" setting for the notifier and it was set to the default "auto".


Isn't it possible to remove somehow the whole plasmoid (with --purge remove) and reinstall it again?!
Maybe this solves the issue.

When opening the mini programes configuration it's only possible to add a new plasmoid, but you can't remove it.
I mean, I see there the notifier with a blue 1 in the upper right conner, but I can't deselect it...

---

