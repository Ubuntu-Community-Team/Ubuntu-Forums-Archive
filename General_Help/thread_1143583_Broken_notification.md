---
title: "Broken notification?"
date: 2009-04-30
forum: General Help
---

### Post by EvilBro on 2009-04-30
Today I started ubuntu 9.04 and at some point I noticed there was an update manager in the bottom panel. I looked at the top panel where the notification area is (used to be?), but I did not see the "there are updates"-icon there. This leads me to my first question: should I expect that icon to still be there?

I think that I should not expect the icon because of the new notification thingy (the 'roundish' popups). This lead me to investigate whether I could get such a popup. I checked for mail, as I remembered that the notification popup was used there, however no popup appeared. I played a few songs with rhythmbox as I thought that would cause a popup, but no popup. Should I be expecting popups? if so, how do I discover what has broken?

Edit: As always 1 minute after I post on here, I figure out a way to do an additional check. I just started Pidgin and it does still produce popups. So I guess the system is not totally broken. :) Still leaves the questions I posted above though...

---

### Post by mb_webguy on 2009-04-30
The behavior of the Update Manager has been changed, and is actually a topic of a lot of somewhat heated discussion recently.

The developers feel that the notification area has become a bit of a dumping ground, and are trying to move actual system notifications out of the notification area and make them more noticeable.  That's why you'll now see some black pop-up boxes in the corner of the desktop from time to time -- it's the new notification system being used in Jaunty.  Which is a good thing, at least for transient notifications.  For persistent notifications, it still needs some work.

Because notification of updates, especially security updates, should be persistent, they're still trying to figure out just how to handle update notification.  The current solution is rather than have the familiar icon in the notification area, to have Update Manager open when updates are available.  It will open within a week of the release of regular updates, or within 24 hours of security updates.  In order to not be too obtrusive, Update Manager will open under other open windows.

That's the new behavior of Update Manager, and why you haven't seen a notification icon for it informing you of updates.  I personally think it's a bad idea, and that they should instead go back to using the notification icon in conjunction with the new notification windows when security updates are released (once when they're first detected, and again to remind you every time you login until you've updated).  But this is the way it is in Jaunty.

If you want to go back to the old behavior with the notification icon, just enter the following command in the terminal, or change the value in gconf-editor:```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```

---

