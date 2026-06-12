---
title: "Update notifier does not notify"
date: 2006-06-03
forum: Desktop Environments
---

### Post by Moonbuzz on 2006-06-03
Hello all,

About 2 months ago, I upgraded to Dapper (by using the update-manager -d option), from that point on, the "updates available" notification and other packages notifications (such as broken packages, installation notifications, etc) have stopped functioning. 

Any ideas what happened, what to do, or at least some suggestion for where to look for the solution? The notification area panel application is there and working, but other than that, nothing.

---

### Post by bluevoodoo1 on 2006-06-03
Is the "update-notifier" package installed?

---

### Post by Moonbuzz on 2006-06-03
Yes, it is

---

### Post by temcat on 2006-06-04
I have a problem with update notifier, too. When I click on the icon in the notification area, it reloads package information files, but never shows the window with update list.

---

### Post by Moonbuzz on 2006-06-05
I've tried running update-notifier a couple of times, and it keeps telling me I'm not the admin.

I have a slightly different superuser setting than the default Ubuntu setup, I created a new user (admin) with full root access (via sudo), and then removed every root capabilities from the default user. So to run update-notifier, I need to ```
su admin
sudo update-notifier
``` 
I'll try later to login as admin and see what happens.

---

### Post by girts on 2006-06-07
I also have a problem with update notifier. 
It shows that updates are available only after I do manual apt-get update. Wasn't it supposed to download and check package lists in background? I have selected automatical check for updates in software properties, but it still doesn't check for updates automatically...
I have Dapper 6.06, upgraded from 5.10 which was upgraded from 5.04. Maybe problem was caused by distro upgrade?

---

### Post by girts on 2006-06-10
Does anybody knows, how to solve this problem?

---

### Post by mat_london on 2006-06-10
Me too, thought things had been quiet for a week, just manually checked and there are 32 updates this morning.
Shouldn't update notifier have told me ?

Mat

---

### Post by dpchemist on 2006-06-17
The same thing for me. There have been no automatic update-notifier popups since I upgraded from Breezy to Dapper. However, when I run in terminal **sudo apt-get update** it shows popup in several seconds. How to force it to check and show updates automatically?

---

### Post by warjowuch on 2006-08-02
I have just replied to this thread [http://www.ubuntuforums.org/showthread.php?t=199406&highlight=update+notifier](http://www.ubuntuforums.org/showthread.php?t=199406&highlight=update+notifier)
It seems to describe the same problem. Hope someone finds/has/posts the solution.
It maybe due to the fact that when dist-upgraded to dapper, it has uninstalled several packages, like ubuntu-desktop. I have not reïnstalled these, maybe something between those packages that prevents update-notifier from checking automatically?

---

### Post by warjowuch on 2006-08-02
I have just replied to this thread [http://www.ubuntuforums.org/showthread.php?t=199406&highlight=update+notifier](http://www.ubuntuforums.org/showthread.php?t=199406&highlight=update+notifier)
It seems to describe the same problem. Hope someone finds/has/posts the solution.
It maybe due to the fact that when dist-upgraded to dapper, it has uninstalled several packages, like ubuntu-desktop. I have not reïnstalled these, maybe something between those packages that prevents update-notifier from checking automatically?

---

