---
title: "Todays Update broke my Deleted items"
date: 2008-06-04
forum: Desktop Environments
---

### Post by schtufbox on 2008-06-04
I'm using ubuntu 8.04 (hardy heron)
I did an update around an hour ago, and now my 'Deleted items' icon is no longer showing on the panel.
It still works, I can click on the area it should be, and open the deleted items folder, and I can right click the area and select 'empty deleted items'  but there is no icon
I even changed icon themes a couple of times, just in case...no matter which theme I use..no deleted items icon appears.

Anyone have any ideas what to do to fix it?
I did a forum search for related issues but nothing helped in the ones that were similar.

---

### Post by schtufbox on 2008-06-04
Anyone got any ideas? :)

---

### Post by temaki on 2008-06-05
This happen to me as well, try rebooting..

---

### Post by ChameleonDave on 2008-06-05
Strange bug.  I don't have GNOME, so I can't duplicate it.

Have you tried removing the trashcan applet and re-adding it?

---

### Post by ludidado on 2008-06-08
Same problem here.
There is no applet to remove.
It's just gone and can not be added on any panel or drawer.
P.S.
The .Trash folder is gone too.

---

### Post by ChameleonDave on 2008-06-08
Perhaps the update removed a package providing panel applets.

Go to /var/log/apt.  It contains logs of your recent installation and uninstallation activity.  Perhaps you could have a look, or show us your logs.  That way we can work out what was removed.

---

### Post by sidran on 2008-06-08
I have the same issue.  The icon isn't there, though I can click the area to get the trash window.  Though my last update was days ago and I don't look at that part of my screen that often, so I don't know when it exactly started happening.

Removing and re-adding the Trash icon does nothing but remove and re-add a 0 (or 1, since I can click it?) invisible trash icon.  Rebooting doesn't help either.  My only idea is perhaps the icon graphic isn't loading for some reason, but I have no idea how it does this nor how to fix it.

---

### Post by sstusick on 2008-06-08
This reminds me why I don't do updates.

---

### Post by joechummer on 2008-06-08
> **sstusick said:**
> This reminds me why I don't do updates.

I'm right there with you.  I have an EeePC with Xandros on it and updated all the software with apt.  For some reason, the Perl update (which I didn't need since I don't even use Perl -- I'm a Ruby man) broke a half dozen packages, and fixing those packages broken two dozen more, and so on and so on until my entire desktop environment was uninstalled.  When I rebooted, all I got was a blank screen after POST.  Needless to say, I had to restore the whole thing, but thank God I backed up all of my relevant data to an external source before rebooting, or else I'd have lost everything!

But, back to the subject.  Even though Ubuntu is free/open-source, I thought updates were thoroughly tested and debugged before being released?  I'm about to install Ubuntu on my main desktop at home, and stories like these make this (relative) Linux newbie a little worried.

---

### Post by schizoman on 2008-06-14
I've got a trash icon, but it doesn't point to my .Trash folder.  I have to use the command line to empty most of my trash.  Geesh.

---

### Post by sidran on 2008-06-22
Well, I just updated today, and apparently one of the updates fixed this problem.  I now have 17 Deleted Items icons peppered throughout both my panels in Gnome.  Thanks whoever fixed it!  Hopefully it doesn't go broke again.

---

