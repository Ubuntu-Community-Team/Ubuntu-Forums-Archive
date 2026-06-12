---
title: "Ubuntu 14.04 - Awesome in Gnome 3.9"
date: 2014-10-28
forum: Desktop Environments
---

### Post by Sterling_McLeod on 2014-10-28
Hi, I am trying to use the Awesome window manager inside GNOME 3.9. I followed the instructions here: [http://awesome.naquadah.org/wiki/Quickly_Setting_up_Awesome_with_Gnome#Gnome_3.9_.2F_Ubuntu_13.10](http://awesome.naquadah.org/wiki/Quickly_Setting_up_Awesome_with_Gnome#Gnome_3.9_.2F_Ubuntu_13.10)

However, I am still having some issues. I am not sure that all of the GNOME daemons are starting.

When I start gnome-control-center and go to Brightness and Lock, I set it to turn the screen off when inactive for 1 minute and lock the screen after 2 minutes. Neither of those happen after the couple minutes. When I shut my laptop and re-open it, it takes me back to my desktop rather than taking me to the lock screen and requiring me to login. My /usr/share/gnome-session/sessions/awesome.session looks like:

```

[GNOME Session]
Name=Awesome session
RequiredComponents=awesome;gnome-settings-daemon;
DesktopName=Awesome

```

I have tried adding more things to RequiredComponents such as nm-applet, gnome-power, etc., but then the session does not start properly. After I login, nothing happens and I need to kill the session. I don't know what all other things should be starting, but if that is not working then I am assuming that other important daemons are not starting.

What else do I need to add to RequiredComponents to have all of GNOME except using Awesome as the WM and the wibox as a panel? Thanks for any help.

---

