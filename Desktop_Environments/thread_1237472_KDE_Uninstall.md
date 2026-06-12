---
title: "KDE Uninstall"
date: 2009-08-11
forum: Desktop Environments
---

### Post by jqke on 2009-08-11
I started out with Jaunty and GNOME, and I decided to try out KDE. So I found this to help me out:

QUOTE_______________________________________________


"There is no need to do a complete install of kubuntu to try KDE. Kubuntu is basically the same as Ubuntu (same base system), but with a different desktop environment.

But, instead of apt-get (as was suggested earlier), better use aptitude.

Apt-get does not deal very well with dependencies. If you want to remove kubuntu-desktop and installed it with apt-get, you'll have to uninstall all the programs that come with it *manually*.

Better try:

     Code:
     sudo aptitude update 


then, to install kubuntu

     Code:
     sudo **aptitude** install kubuntu-desktop 


if you ever want to remove it, just do:

     Code:
     sudo aptitude remove kubuntu-desktop



UNQUOTE_______________________________________________________________________


This information came from:

[http://ubuntuforums.org/showthread.php?t=301920](http://ubuntuforums.org/showthread.php?t=301920)

I ran the first command, and the second. The installation downloaded and installed. During the installation I got a prompt that asked which desktop should be the default. I chose KDE.

I rebooted and got the Kubuntu loading screen, as well as the login screen.

I logged in and found that my desktop did not change. I looked for help and found this:

[http://www.cyberciti.biz/tips/quick-way-to-switch-from-kde-to-gnome-or-viceversa.html](http://www.cyberciti.biz/tips/quick-way-to-switch-from-kde-to-gnome-or-viceversa.html)

It told me to try switchdesk, however I do not have switchdesk installed.

So I used this code instead:

sude startkde

That worked. But I still had the GNOME top panel, and my terminal was in constant progress (ie. "updating battery time: 2:08..." and other menial tasks).

I finally shut down the terminal and attempted to log out, only to find that "user switcher quit unexpectedly." I used the power down button instead, and rebooted.

Ubuntu loaded the same as before, with the GNOME desktop, but still with the Kubuntu loading screen and login screen.

I ran the third command listed above to uninstall. I rebooted, but I still get the Kubuntu loading screen upon reboot.


Any help would be appreciated. Hope I'm not *too* detailed.

---

### Post by slakkie on 2009-08-11
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by jqke on 2009-08-11
Why thank you.

---

