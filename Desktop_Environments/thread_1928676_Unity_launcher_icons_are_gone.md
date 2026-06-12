---
title: "Unity launcher icons are gone"
date: 2012-02-20
forum: Desktop Environments
---

### Post by pallo on 2012-02-20
I returned to my computer today after having left it idle since yesterday. When I unlocked the screen-saver it turns out all icons in the Unity launcher have disappeared. It seems like they have all been moved to the top of the launcher, but are unavailable (cannot be clicked).

No new packages have been installed on the system ("find /var/lib/dpkg/ -ctime -2" does not find any files and the only config files I find in $HOME/.* that have changed (except for firefox and mail) are .cache/dconf/user, .config/dconf/user and .cache/compizconfig-1/scaleaddon.pb.

Does anyone have any idea what might have caused this (given an idle system with no changes in packages) and more importantly how to fix it without resetting everything (i.e. files to restore from backup)?

---

### Post by youngunix on 2012-02-20
What was the system doing when you left it running?
Did you try logging out and logging back in? (reboot or shutdown; wait a few seconds and turn it back on)

---

### Post by zim2dive on 2012-04-20
This happens to me too.. usually only after several weeks of uptime.  I have yet to find a way to get the icons back.

some of them do appear to be there, just invisible.. I can hover over the bar and see some of the names pop up.

---

### Post by jkgung on 2012-08-13
Is there any update regarding this issue? I have exactly the same problem

---

### Post by Warprunner on 2012-08-13
Not sure it will help you. I had the same problem. I solved it by merely changing the background. 
I did this for a few days and a couple of reboots. Now it doesn't happen. 
Not sure what caused it but I feel your pain!
Hope this helps.

---

### Post by jkgung on 2012-08-13
sound like a bug - that means at some sunny day your launcher icons appeared again? May I sak what graphic card you use?

---

### Post by Warprunner on 2012-08-13
I have a Sony Vaio Laptop. The Graphics are: Intel® Ironlake Mobile

Yes, it happened one Sunny Day. I looked for a reason and found none. I guess the Ubuntu Gods knew and fixed it with an update.

---

### Post by jkgung on 2012-08-14
I use Intel® HD 4000 - It seams that Intel Graphics are not yet 100% compatible ...

---

### Post by jkgung on 2012-08-14
When Using Alt+Tab the window is without icons as well

---

### Post by jkgung on 2012-08-14
unity -v shows:
[I]WARN  2012-08-14 19:23:20 unity.gtk <unknown>:0 Theme file for default has no name

WARN  2012-08-14 19:23:20 unity.gtk <unknown>:0 Theme file for default has no directories

ERROR 2012-08-14 19:23:20 unity.gtk <unknown>:0 gtk_icon_info_get_filename: assertion `icon_info != NULL' failed
ERROR 2012-08-14 19:23:20 unity.gtk <unknown>:0 gtk_icon_info_free: assertion `icon_info != NULL' failed
ERROR 2012-08-14 19:23:20 unity.gtk <unknown>:0 gtk_icon_info_load_icon: assertion `icon_info != NULL' failed
ERROR 2012-08-14 19:23:20 unity.gtk <unknown>:0 gtk_icon_info_free: assertion `icon_info != NULL' failed
WARN  2012-08-14 19:23:20 unity.launcher LauncherIcon.cpp:433 Unable to load 'workspace-switcher' from icon theme: [/I]

Is someone able to understand this?
Thanks for every reply

---

### Post by roboknight on 2013-01-11
Has anyone found a resolution for this?  I have this same problem.  It appears that compiz is running into several errors when this occurs, unfortunately, I can't post the list of errors I end up seeing because I didn't grab it before a reboot.  But it appears to happen after several days (maybe a week or two) of uptime.

I thought some Ubuntu updates might take care of it, but so far, no luck.  I got at least one bug with compiz that said it probably should be reported as a bug (the machine doesn't have access to the internet, so there isn't a good way to do that)...

Anyone else still experiencing this issue and getting useful logs really needs to report this.  It certainly is annoying as it seems to require a reboot.

---

