---
title: "Still no graphical login in karmic koala 9.10"
date: 2009-11-18
forum: Desktop Environments
---

### Post by Dieter on 2009-11-18
Hello,

about 2-3 weeks ago I installed Kubuntu 9.10 Karmic Koala 64-bit version - and the system worked until about one week ago. I'm using nvidia onboard graphic and activated the proprietary nvidia driver. As I noticed that KPackageKit wasn't able to update the system, I installed the available updates with apt-get.
Since that update I'm not able to login with kdm. After submitting the login screen, the login screen re-appears after some seconds. The password is correct. Yesterday I installed new updates but without any change - still unable to login with kdm.

I can't find useful hints in the logfiles what component causes this bug:
- kdm?
- nvidia driver?
- pam authentification?
- apparmor?
Login on console is possible. "sudo service kdm restart" doesn't help - no login possible.
I installed xdm and tried to login with xdm instead of kdm - no login possible.
I created another user to get a new kde profile - but no login possible with the new user.

I don't want to install a "half gnome system" to try with gdm. 

Again the short info:
- Karmic Koala 9.10 fresh install (no upgrade from Jaunty)
- 64 bit system (amd_64)
- proprietary nvidia graphics driver
- error occured after update about one week ago with apt-get update && apt-get upgrade
- bug is not fixed with yesterday's update

What can I do to get my KDE desktop back?

---

### Post by Zorael on 2009-11-18
My money is on the Nvidia driver.

KDM will restart itself completely (returning to the greeter login screen) when it's trying to load the compositioner (kwin) if the video driver itself loads but then runs into missing symbols. Is nothing of the sort mentioned in either /var/log/Xorg.0.log or /var/log/kdm.log? It showed up in kdm.log when it happened to me with a development build of the Intel driver.

Try disabling the driver and see if things miraculously work again.

---

