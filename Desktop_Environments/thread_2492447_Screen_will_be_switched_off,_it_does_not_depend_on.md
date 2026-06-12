---
title: "Screen will be switched off, it does not depend on power-management settings"
date: 2023-11-11
forum: Desktop Environments
---

### Post by gloster10 on 2023-11-11
6.2.0-36-generic
 lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.3 LTS
Release:    22.04
Codename:    jammy

Please refer to the attached pic, to see my power management settings.

Screensaver is also Off.

Also after deinstallation of xfce4-power-manager (complete) and rebooting the system, the screen will be switched off after 5min.
 firefox in use, to play a video and to save the video with simplescreerecorder is not possible any more.

Also checked Bios-Uefi, whether there is a power management setting, it is not.

I have no further idea, what to do, but there must be one setting (config file ???), where the 5min Off time will be set.

Any one an idea what to do, to switch off the "switch Off feature" ?

---

### Post by TheFu on 2023-11-11
```
$ more ~/bin/ssr.sh 

xset s off &
xset -dpms &

# Disable the screensaver
/usr/bin/xscreensaver-command -exit

/usr/bin/simplescreenrecorder

# Enable the screensaver
/usr/bin/xscreensaver &

xset +dpms &
xset s on &
```

I wrap SSR in the script above to prevent the issue.

---

### Post by gloster10 on 2023-11-11
@TheFu,

thank you !

---

### Post by gloster10 on 2023-11-11
Does someone know how to correct a typo in the headline ?
Instead of "of" to "off"

---

### Post by deadflowr on 2023-11-11
You can report it, and staff will edit it for you. (click on the report post to report issues)
but i edited it so the first post and all new posts will get the title change.
(Unfortunately, existing posts would need to be edited, or there's probably a way to change all at once but I'm rather lazy right now, so...)

---

### Post by gloster10 on 2023-11-11
@deadflowr,
thank you !

---

