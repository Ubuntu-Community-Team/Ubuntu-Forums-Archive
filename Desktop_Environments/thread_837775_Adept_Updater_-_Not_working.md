---
title: "Adept Updater - Not working?"
date: 2008-06-22
forum: Desktop Environments
---

### Post by scfamily on 2008-06-22
Running 8.04 Kubuntu 32bit.

When the system boots, I get the green light in the system tray stating there are no updates, but if I launch adept manager and fetch updates, the icon from Adept updater will show up in the system tray.

I kinda goof'd and installed the updater for gnome when I was trying to figure this out, but have since uninstalled the gnome updater.

I also have uninstalled/reinstalled adept-updater, but how can I be sure it is running properly?

I ask because I run Ubuntu at my shop, and when the desktop there has updates I check at home and K will not have the update notification until I launch Adept manager and fetch updates. Lo and behold the similar updates appear.

I understand gnome may have different updates than KDE at times, but even the recent linux core updates were not picked up by my curent Kubuntu install till I fetched the updates in Adept Manager.

Any ideas or suggestions you have would be appreciated.

Thanks.

Steve

---

### Post by Happy_Man on 2008-06-22
Hm, it seems to be an issue specific to your Adept settings. Maybe you set it to not automatically check for updates?

---

### Post by scfamily on 2008-06-22
> **Happy_Man said:**
> Hm, it seems to be an issue specific to your Adept settings. Maybe you set it to not automatically check for updates?

How could I verify those settings?

I have not been able to find the launcher for the updater, but I am also no stranger to terminal.

Come to think about it, I have not checked the settings in the adept manager, Ill check there first.

I guess next time I force a update to the packages I will see if there is a settings option in the updater, but if you have an better method I would love to hear it..

:)

Thanks Happy Man.

---

### Post by Zorael on 2008-06-23
Perhaps the update *notifier* itself has some settings?

Run the following in a terminal and be ready at the systray to click it.
```
$ killall adept_notifier; adept_notifier &
```

---

### Post by scfamily on 2008-06-23
> **Zorael said:**
> Perhaps the update *notifier* itself has some settings?

Run the following in a terminal and be ready at the systray to click it.
```
$ killall adept_notifier; adept_notifier &
```

:oops:

I ran your suggestion in terminal..

"The program 'adept_notifier' is currently not installed."

I used apt-get to install it, It may have been removed when I installed the gnome updater.

Ill see how this pans out, Thanks.. 8-[

Confirmed, the update notification popped up about 2 mins after (re)installing the notifier.

Thanks again!

---

