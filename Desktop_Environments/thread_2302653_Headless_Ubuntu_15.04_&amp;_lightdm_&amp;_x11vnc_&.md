---
title: "Headless Ubuntu 15.04 &amp; lightdm &amp; x11vnc &amp; multiuser"
date: 2015-11-12
forum: Desktop Environments
---

### Post by pliit on 2015-11-12
Hi!

I have an Ubuntu 15.04 desktop version running headless (besides the TV, that's connected to it) and doing a bunch of stuff.

The desktop manager is the default LightDM.

It has several users who should be able to log in through x11vnc. Everything was working fine, untill we introduced a second user to the VNC.

When you log in with a second user, a new session of X (:1) is created, which means your current VNC session will not see it, since it's connected to the :0 display.
I have googled this problem, but found no solution with x11vnc.

So basically when you change the user the x11vnc server will be still connected to the same display as it was in the start and the screen will just stay black unless you manually restart x11vnc and connect it to the other display with -display :1 or -display :0

It is important for us to always see the same video feed as the display output shows (HDMI in our case).

Is there any nice solution for our situation? I wouldn't mind swaping out x11vnc, as long as it worked without any dirty hacks.

My current systemd service script looks like this:
> ExecStart=/usr/bin/x11vnc -xkb -noxdamage -noxrecord -display :0 -forever -auth guess -rfbauth /etc/x11vnc.pass

I have tried -find and some other stuff, but no dice so far.

Thank you!

---

