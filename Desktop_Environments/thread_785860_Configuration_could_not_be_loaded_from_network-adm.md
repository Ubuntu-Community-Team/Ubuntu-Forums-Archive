---
title: "Configuration could not be loaded from network-admin"
date: 2008-05-07
forum: Desktop Environments
---

### Post by jcnorman on 2008-05-07
I'm having a problem with Network Admin (network-admin).  It gives a message "The configuration could not be loaded
You are not allowed to access the system configuration."

I've reinstalled gnome system tools and gnome network tools without any effect.

Jim Norman

---

### Post by happynix on 2008-05-07
I have the same problem.
   It seems to effect network-admin, users-admin, services-admin and time-admin.  I don't know if this is an exhaustive list or not.

When I launch these applications from a xterm I get the following additional information:
```
** (network-admin:7509): CRITICAL **: Failed to execute program /usr/lib/dbus-1.0/dbus-daemon-launch-helper: Success
```
```
** (users-admin:7538): CRITICAL **: Failed to execute program /usr/lib/dbus-1.0/dbus-daemon-launch-helper: Success
```
```
** (services-admin:7553): CRITICAL **: Failed to execute program /usr/lib/dbus-1.0/dbus-daemon-launch-helper: Success

```
```
(time-admin:7564): Gtk-WARNING **: Unsupported tag for GtkWidget: atkproperty

(time-admin:7564): Gtk-WARNING **: Unsupported tag for GtkWidget: atkproperty

(time-admin:7564): Gtk-WARNING **: Unknown property: GtkCalendar.display-options

** (time-admin:7564): CRITICAL **: Failed to execute program /usr/lib/dbus-1.0/dbus-daemon-launch-helper: Success

```

This is an upgrade from Fiesty to Hardy.  No problems were encountered during the upgrade.

I have tried moving the hal startup to  init priority of 13 instead of 12
(ie. /etc/rc?.d/S12hal  -> /etc/rc?.d/S13hal) in case there were any race condition problems with dbus.
I have reinstalled dbus and gnome-system-tools. (unsurprisingly unhelpful)

I would welcome any suggestions or simply any reports of similar problems, just so we can make sure to enter a bug report if necessary.

---

### Post by happynix on 2008-05-08
There seem to be several threads about this so I thought I'd post them.

First there is the launchpad question: [ Question 32334: I am not allowed to run gnome-system-tools ]("https://answers.launchpad.net/ubuntu/+source/gnome-system-tools/+question/32334")

And a community request from the same guy: [gnome-system-tools problem]("http://ubuntuforums.org/showthread.php?t=784558&highlight=network-admin+dbus+hardy")

There are also seem to be some not quite related problems about greyed out unlock buttions, but I'm not getting that far.  These seem to be dbus/hal related problems. Summed up here [Polkit hell]("http://ubuntuforums.org/showthread.php?p=4866207")

Sometimes half the battle is finding the right question to ask.:confused:

---

### Post by chaeron on 2008-05-20
I have the same ** (network-admin:7509): CRITICAL **: Failed to execute program /usr/lib/dbus-1.0/dbus-daemon-launch-helper: Success problem.

Seemed to start after the latest set of Hardy updates last week sometime for me.

Any idea yet on how to resolve this?  I really don't have the time for a reinstall process on my laptop.

---

### Post by happynix on 2008-05-25
Nope, I've resigned to a reinstall. I just have not done it yet.

---

### Post by chaeron on 2008-05-25
Funny thing...I figured out that this problem began for me a week and a half ago when I had some trouble mounting CDs...which was caused by permissions. I had downloaded a script (recoverubuntulostpermissions) from the forum that fixes permissions, supposedly setting them back to stock values. That solved the needing of Admin to mount CDs automagically, but I thought maybe it had in turn screwed up the permissions for the policy manager and resulted in the problems seen in this thread.

So....having a recent backup on a portable USB drive, I did a reverse rsync to restore the Ubuntu files on my laptop (fortunately I had backed up just before I went on a road trip, which was only a few days prior to the problem manifesting).  Rebooted fine...then I updated Ubuntu to the new packages that were released a week and a half a go and which I had thought might be the problem.

My "Config could not be loaded" errors were gone!  Network, Users/Groups and other admin functions work fine again!  Yay!

So....from this I have to conclude that the issues found in this thread are likely due to screwed up permissions/ownership of a few key policy files.

I probably am back to the needing of Admin priviledges to mount CDs, but that is less of an issue for me.

Figured I would post this as it might be helpful to others in diagnosing the problem.

---

