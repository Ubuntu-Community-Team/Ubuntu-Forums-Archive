---
title: "gnome very slow to load.Gnome settings daemon"
date: 2008-05-03
forum: Desktop Environments
---

### Post by willem_rt on 2008-05-03
Hi,


I am running a wubi install of Hardy and am experiencing extremely long Gnome load times, with the following error message appearing. Themes and the sstartup sound will often load 2 or three minutes after login.



"[B]There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in"
[/B]

i tried to login using the command prompt failsafe mode and tried to run 

[B]
sudo gnome-settings-daemon[/B]


i then got these error messages

[IMG]http://farm4.static.flickr.com/3251/2460777188_f3d86f6fef_b.jpg[/IMG]

I'm not sure what it is but this has happened twice and the only things I can think that I changed just before it crashed were changing to a static ip. But changing back did not fix it. That seemed to be something that worked for some people.

Any Ideas?

---

### Post by cmnorton on 2008-05-03
Once in a while I get this message on a slower P4 laptop with 1GB RAM running 7.10. If I log out and back in, the login seems to be fine. Have you thought of posting this as a question or bug in Ubuntu Launchpad?

---

### Post by wormeyman on 2008-05-03
I've had this problem as well try restarting, also another thing you could try would be to add a new user and see if that user has the same problem something might just be mis-configured.

---

