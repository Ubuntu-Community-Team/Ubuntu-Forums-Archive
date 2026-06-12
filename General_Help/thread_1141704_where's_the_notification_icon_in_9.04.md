---
title: "where's the notification icon in 9.04?"
date: 2009-04-28
forum: General Help
---

### Post by banana jama on 2009-04-28
I've notice that theres not notification icon (the red down arrow & the orange star with a small arrow in it) is it just me? is there anyway to get it back?

---

### Post by freonchill on 2009-04-28
you mean the notification for the update manager?

you need to hit ALT+F2 and type in "update-manager -d"

if should add the option to upgrade at the top of the update manager window that you can select to upgrade.

---

### Post by Brandon Williams on 2009-04-28
There are already multiple threads about this. Please search the forum before posting!

Read the release notes to get more info about this new behavior and how to reconfigure.

---

### Post by banana jama on 2009-04-28
to freonchill: 
      i know how to check for updates what i want is the notification icons that was on the gnome upper toolbar. i have to check for updates twice by going to system administration and update manager to manually check for updates. i perfer previous versions of ubuntu where a small icon pop up on the toolbar and told me new updates were availble. heres a picture of what im talking about (found it on the web).

---

### Post by leonardo_neo on 2009-04-28
This is what I found from the Ubuntu 9.04 release notes.....

> Change in notifications of available updates

Ubuntu 9.04 introduces a change to the handling of package updates, launching update-manager directly instead of displaying a notification icon in the GNOME panel. Users will still be notified of security updates on a daily basis, but for updates that are not security-related, users will only be prompted once a week.

Users who wish to continue receiving update notifications in the previous manner can restore the earlier behavior using the following command:

gconftool -s --type bool /apps/update-notifier/auto_launch false



Hope this helps you :)

---

### Post by SentientFluid on 2009-04-28
Just to confirm what leonardo_neo said, the icon no longer shows by default. Instead, when there are updates the Update Manager window will open and show you a list of the current updates.
Running the command that was provided will restore the old notification icon you're asking about.

---

