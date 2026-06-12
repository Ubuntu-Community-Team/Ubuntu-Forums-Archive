---
title: "kubuntu: configuring the kde panels"
date: 2007-06-07
forum: Desktop Environments
---

### Post by NeoNecro on 2007-06-07
Hello,

I would like to have to panels: one at the top of my screen and one at the bottom. I know how to ad a panel to my desktop, but I have problem configuring them.

When I ad a second panel to my desktop I can only configure the first one. When I right-click on the new panel and choose "Configure Panel..." I get a menu, but it only configures my old panel, it doesn't matter on which panel I right-click.

I don't think this is what's meant to happen? I would like to change the size and position of my new panel. (I can drag the new panel around and add applets to it)

---

### Post by thehuman on 2007-06-07
This is an actual bug. Simple fix, though, thankfully:

[KDE Panel Config Bug]("https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/68926")

---

### Post by NeoNecro on 2007-06-07
Thank you,

doing: "touch ~/.kde/share/config/kickerrc" after adding a new pannel did it.

---

### Post by bailout on 2007-06-10
If you run kcontrol you can configure the second panel with that. It seems to be a bug in system settings. Or this was the case in dapper, I have just stuck with one panel in fiesty.

---

### Post by dolphinsonar on 2007-09-25
Thanks!  That was driving me crazy.

Its a problem, whenever there is a bug I think that the problem is with me.  I should have more confidence in myself.

Bugs happen.  Thanks for pointing us to the fix!

---

