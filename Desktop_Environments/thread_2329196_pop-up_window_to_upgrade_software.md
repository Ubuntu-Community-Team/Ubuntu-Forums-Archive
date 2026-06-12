---
title: "pop-up window to upgrade software"
date: 2016-06-28
forum: Desktop Environments
---

### Post by Skaperen on 2016-06-28
a few minutes after booting up i get a small window suggesting i upgrade.  all the admin users have themselves as the default user to do the upgrade.  all the non-admin users get to select which admin user to do the upgrade as.

how can i get these windows to *not* come up?  they come up for *every* user.

---

### Post by &amp;KyT$0P# on 2016-06-29
In Software Sources preferences, select to never automatically check for updates.  Then you will instead get a system tray icon/notification if you haven't checked for updates in a while.

---

### Post by Skaperen on 2016-06-29
> **halogen2 said:**
> In Software Sources preferences ... where do i find this?  i looked in *Ubuntu Software* and in *System Setting:System>>Software & Updates* and it is not in either.  i am running Ubuntu 16.04.

---

### Post by Skaperen on 2016-06-29
fyi: i do not want to disable any checks done by CLI "apt-get update && apt-get -y upgrade"

---

### Post by deadflowr on 2016-06-29
Upgrades, like as in release upgrade ( from version 12.04 to 14.04, as example )?

In that case in the same section Software and Updates go to the Updates section and go to the part about Notify Me of New Ubuntu Versions and set it to Never.

---

### Post by &amp;KyT$0P# on 2016-06-30
> **Skaperen said:**
> *System Setting:System>>Software & Updates* 
It should be there... not sure if Unity Ubuntu does this differently but in Xubuntu 16.04 that has is an "Updates" tab, these settings are listed there.  There are two you're looking for - one is the setting mentioned by deadflowr, the other is "Automatically check for updates:".  Set both to "Never".

And no this specific settings are not related to the command line apt-get and won't affect it, it's only controlling the one GUI frontend for it.

---

### Post by Skaperen on 2016-07-06
i was looking for "Source". just ignoring that and i find it OK.

---

