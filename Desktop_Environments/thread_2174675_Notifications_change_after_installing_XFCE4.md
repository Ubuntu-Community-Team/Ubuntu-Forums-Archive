---
title: "Notifications change after installing XFCE4"
date: 2013-09-15
forum: Desktop Environments
---

### Post by tuxpenguin42 on 2013-09-15
I decided to tell XFCE recently, but after logging back in to Unity the notifications have changed.

I tried following [these instructions]("http://askubuntu.com/questions/150438/xfce4-overrode-my-gnome-notifications-notify-osd-how-do-i-get-them-back"), but that just caused the notifications to disappear entirely. After switching the line back to the XFCE one they're still missing.

How to I change it back to the notifier used by Unity?

Thanks in advance for any help.

---

### Post by tuxpenguin42 on 2013-09-15
Fixed my own problem!

For anyone who finds this in the future, just uninstall the xfce4-notifyd package. On the downside, this means the the xfce notifier doesn't work in xfce, and the unity one is used instead.

---

