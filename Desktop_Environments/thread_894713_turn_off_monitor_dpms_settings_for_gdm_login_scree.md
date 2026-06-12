---
title: "turn off monitor: dpms settings for gdm login screen?"
date: 2008-08-19
forum: Desktop Environments
---

### Post by mathog on 2008-08-19
Where are the dpms settings for the gdm login screen on Ubuntu 8.04.1?  I want to be shorten the time the login screen is displayed, so that the LCD display goes into a low power state sooner.

When logged in this system uses xfce, and I was able to use the xscreensaver-demo tool (equivalent to main menu -> settings -> screensaver) to set up dpms so that it worked there.  However, even after doing that

% xset q

shows standby/suspend/off all set to 0 even though DPMS is enabled and xscreensaver is using nonzero times for these values.  Doing this:

% xset dpms 20 20 20

caused the session to turn off the display after 20 seconds.  However, if the session was then logged out, and the login screen came up, it did not blank at 20 seconds.

There are no specific times set in /etc/X11/xorg.conf, and usually that causes the X11 server to come up with 20,30,40 minutes for standby, suspend, off.  Either the X11 server on Ubuntu is compiled differently, or something else is overriding these values and setting them to zero.  My guess is that this same something reset them to zero when the session ended.

Suggestions?

Thanks.

---

### Post by gatewayasteroid on 2008-08-19
> **mathog said:**
> Where are the dpms settings for the gdm login screen on Ubuntu 8.04.1?  I want to be shorten the time the login screen is displayed, so that the LCD display goes into a low power state sooner.

When logged in this system uses xfce, and I was able to use the xscreensaver-demo tool (equivalent to main menu -> settings -> screensaver) to set up dpms so that it worked there.  However, even after doing that

% xset q

shows standby/suspend/off all set to 0 even though DPMS is enabled and xscreensaver is using nonzero times for these values.  Doing this:

% xset dpms 20 20 20

caused the session to turn off the display after 20 seconds.  However, if the session was then logged out, and the login screen came up, it did not blank at 20 seconds.

There are no specific times set in /etc/X11/xorg.conf, and usually that causes the X11 server to come up with 20,30,40 minutes for standby, suspend, off.  Either the X11 server on Ubuntu is compiled differently, or something else is overriding these values and setting them to zero.  My guess is that this same something reset them to zero when the session ended.

Suggestions?

Thanks.

Maybe it's related to this:

[https://bugs.launchpad.net/ubuntu/+source/xfce-mcs-plugins/+bug/200665](https://bugs.launchpad.net/ubuntu/+source/xfce-mcs-plugins/+bug/200665)

Try this step:

[I]You need to explicitly select Xfce Session in gdm login but on a clean installation this session isn't the default.

[...]

Teoh Han Hui, please select Xfce Session in gdm login and try it again. If that solves the problem then it will confirm that for some reason the default session in gdm is not calling startxfce4, as I said before.[/I]

[https://bugs.launchpad.net/ubuntu/+source/xfce-mcs-plugins/+bug/200665/comments/5](https://bugs.launchpad.net/ubuntu/+source/xfce-mcs-plugins/+bug/200665/comments/5)

[https://bugs.launchpad.net/ubuntu/+source/xfce-mcs-plugins/+bug/200665/comments/7](https://bugs.launchpad.net/ubuntu/+source/xfce-mcs-plugins/+bug/200665/comments/7)

---

