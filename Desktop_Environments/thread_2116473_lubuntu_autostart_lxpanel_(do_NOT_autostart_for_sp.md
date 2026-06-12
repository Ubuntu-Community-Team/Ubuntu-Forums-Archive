---
title: "lubuntu autostart lxpanel (do NOT autostart for specific users)"
date: 2013-02-15
forum: Desktop Environments
---

### Post by kdford on 2013-02-15
Couldn't find the answer to this specific question searching at large, or in this forum.

I am running Lubuntu 12.10 and have started using Cairo-Dock with xcompmgr.  It runs very well and I prefer it to the lxpanel.  I want to disable the panel.

I added a Cairo dock autostart to my ~/.config/autostart and that works fine.

The problem is how to STOP lxpanel from starting.  I can do it by commenting or remove the lxpanel line from /etc/xdg/lxsession/Lubuntu/autostart but that will cause it to stop launching globally.  If I have another user, or a guest user on my machine, they should have the generic Lubuntu experience.  So.. I want to NOT launch lxpanel for MY user account (and launch cairodock in its place), but I want to continue launching lxpanel globally.

One method that came to mind is writing a script to kill lxpanel that could be called by my local user's autostart folder but that seems really hacky.

The only clean implementation I can think of is to have the per-user autostart file allow for negations.

So, if global autostart contains
  @lxpanel --option1 --option2

and if /home/userX/.config/autostart/autostart (or similar) has
  -@lxpanel

That would cause lxpanel to launch for everybody who does NOT have a negating entry in their personal autostart file.


Any thoughts or solutions to my problem?

---

### Post by Gaygerbil on 2013-02-16
I think using a script to just kill LxPanel for a specific user might be the easiest thing for you to do.

There is an autostart file which contains the lxpanel in /etc/xdg/session/Lubuntu, you could try commenting it out there but I'm fairly certain that would affect all users for you.

Good luck!

---

