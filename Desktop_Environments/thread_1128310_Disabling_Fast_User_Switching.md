---
title: "Disabling Fast User Switching"
date: 2009-04-17
forum: Desktop Environments
---

### Post by hundredpercentjuice on 2009-04-17
(First post, please alert me to any faux pas, etc.)

I'm administering a few machines w/ ATI video cards, which crash on fast-user-switching. (Login/Logout works correctly).

I want to disable the "fast-user-switching" applet, and remove the option from the System->Logout screen.

I tried setting /desktop/gnome/lockdown/disable_user_switching in gconf-editor, but that doesn't seem to do anything.

Gnome: 2.24.1
Ubuntu: 8.10

Thanks for your time.

---

### Post by danl on 2009-08-30
I'd like to do this too under 9.04. I've tried everything I can find in these forums:

-removed fast-user-switch-applet using apt-get remove

-added settings for apps/panel/global/disabled_applets and desktop/gnome/lockdown/disable_user_switching in /etc/gdm/gconf.xml.mandatory/%gconf-tree.xml

The Switch User option persists. Is this a bug?

---

### Post by kerry_s on 2009-08-30
> **danl said:**
> I'd like to do this too under 9.04. I've tried everything I can find in these forums:

-removed fast-user-switch-applet using apt-get remove

-added settings for apps/panel/global/disabled_applets and desktop/gnome/lockdown/disable_user_switching in /etc/gdm/gconf.xml.mandatory/%gconf-tree.xml

The Switch User option persists. Is this a bug?

i'm using 9.04 and locked mine. can't remember which setting it was.

---

### Post by danl on 2009-08-31
Thanks for posting the screen shot. Surprising that there is nothing related to user switching in your settings. I'm trying to add the "Log Out..." applet to a panel. On my system it includes both a Logout and Switch User button. Is the Switch User button on yours?

---

### Post by kerry_s on 2009-08-31
> **danl said:**
> Thanks for posting the screen shot. Surprising that there is nothing related to user switching in your settings. I'm trying to add the "Log Out..." applet to a panel. On my system it includes both a Logout and Switch User button. Is the Switch User button on yours?

yeah, that was the stock switch-user-applet.

---

### Post by mightyiam on 2009-10-12
I'm looking to disable fast user switching, too. This is due to lack of memory in systems. I would like to avoid the use of swap and that in order for another user to login, the current will have to logout.

I'll look it up.

---

### Post by mightyiam on 2009-10-13
Dear friends,

While trying to solve this issue using the information [here]("http://library.gnome.org/admin/deployment-guide/"), I've stumbled across [two]("https://bugs.launchpad.net/gnome-session/+bug/363871") [bugs]("https://bugs.launchpad.net/gnome-session/+bug/450354") which prevent this from working smoothly or at all. Please mark these bugs as affecting you in launchpad.

Blessings.

---

### Post by msp3k on 2009-12-03
It's now December, was a solution ever found?

---

### Post by mightyiam on 2009-12-04
> **msp3k said:**
> It's now December, was a solution ever found?

There's a bounty on this bug at:
[http://www.fossfactory.org/project/p186](http://www.fossfactory.org/project/p186)

---

### Post by jmprox on 2010-06-08
Have you seen this thread?
[http://ubuntuforums.org/showthread.php?t=700675](http://ubuntuforums.org/showthread.php?t=700675)

---

### Post by Tybion on 2011-02-26
I have confirmed that the gconf-editor setting -
desktop - gnome - lockdown - disable_user_switching
- works in both Lucid (10.4) and Maverick (10.10) for me
- ie. it removes the 'Switch User' from the 'Indicator Applet Session' - the default logout, shutdown, etc. button at the right of the panel.

Important: do not type 'sudo' before gconf-editor

---

