---
title: "Dropbox Fail on Ubuntu 23.04, &quot;Lunar Lobster&quot;"
date: 2023-05-01
forum: Desktop Environments
---

### Post by Kurt_Alan on 2023-05-01
Hello All,

Dropbox runs properly on 23.04 but fails because the systray icon is unclickable--no response, no menu window, no access to Preferences, Selective Sync, Move Dropbox Folder, etc. That means that if you have 1 TB of Dropbox data it will dowload all and you have no control over it.

I have installed two versions from the Ubuntu repository, the Nautilus and the Caja versions; in addition I have downloaded the .deb file from dropbox.com. All to no avail. Between trying each new iteration, I followed the Linux documentation at dropbox.com to do a complete purge before reinstall. All to no avail.

I have no issues with Dropbox on the current LTS version.

What concerns me is that if this is an OS problem, that whatever feature is the cause of the problem, if that feature continues into the next LTS, then that means that Dropbox will no longer function on Ubuntu and that will be a big problem for a lot of people.

I have three paid Dropbox accounts, $600.00 per year, and it is the center of my workflow. If Dropox does not function, I will throw out the distro. 

I have contacted support at dropbox.com I uploaded a screenshot, gave them informtion on a r/Ubuntu thread on the same problem (other have the same problem and no solution as yet). They are escalating my case and I can confirm contact via email and I can reply with updates, etc. 

Is anyong having the same experience? Any solution or ideas? Depending on what responses I get here, I will relay information from here to the Dropbox team.

---

### Post by #&amp;thj^% on 2023-05-01
There is a few that are a bit confused as well. [https://www.reddit.com/r/Ubuntu/comments/12z271n/2304_dropbox_icon_is_not_clickable/](https://www.reddit.com/r/Ubuntu/comments/12z271n/2304_dropbox_icon_is_not_clickable/)
One work-around is to try:
```
pkill -TERM gnome-shell
```
Now will it function?
EDIT: You will have to run that command each boot, to make permanent use:
Add a new item to your autostart  with this configuration (do not edit the existing Dropbox item because it is recreated in each reboot):
Remove(don't delete it just disable it) the older entry and add the above.
```

    Name: Dropbox
    Command: dbus-launch dropbox start -i
```

Be sure that the new application is enabled in the list.

---

### Post by Kurt_Alan on 2023-05-01
Thank you ror this. Unfortunately the kill command has no effect on the problem. I wasn't sure if I should effect the command when dropbox was running (by default) or not, so I tried it both ways, once when it was running and another time have "dropbox stop." In both cases, the GUI "crashed" and returrned me to my log-in. But in both cases the icon remains unclickable.

---

### Post by Kurt_Alan on 2023-05-04
The matter is resolved. I tried a different .iso in a virtual machine and had no Dropbox issues. The problem must have been unique to that particular install or it would have failed again. For this reason, always better to stick with LTS.

---

### Post by ActionParsnip on 2023-05-05
Well...yeah

---

