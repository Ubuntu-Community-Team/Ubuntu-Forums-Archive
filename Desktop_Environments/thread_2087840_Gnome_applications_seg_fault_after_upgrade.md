---
title: "Gnome applications seg fault after upgrade"
date: 2012-11-24
forum: Desktop Environments
---

### Post by morgan71 on 2012-11-24
I am on Ubuntu 12.10 32 bit and have been using Gnome 3.6 from the **gnome3-team** ppa for a while without problems, but after the latest upgrade, a lot of Gnome applications, including gnome-shell and nautilus, get segmentation fault when started. As a consequence, GDM never produces the login window, for instance.

Here's the error message:

 [FONT=Courier New]$ nautilus

(nautilus:3921): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:3921): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Segmentation fault (core dumped)[/FONT]

These are the packages that were upgraded:

[FONT=Courier New]2012-11-24 21:52:42 upgrade gnome-accessibility-themes:all 3.6.0.2-0ubuntu1 3.6.2-0ubuntu2~ubuntu12.10.1
2012-11-24 21:52:46 upgrade nautilus-data:all 1:3.6.2-0ubuntu0.1~quantal1 1:3.6.3-0ubuntu2~ubuntu12.10.1
2012-11-24 21:52:47 upgrade gnome-settings-daemon:i386 3.4.2-0ubuntu14 3.6.3-0ubuntu1~ubuntu12.10.1
2012-11-24 21:52:47 upgrade gnome-themes-standard:i386 3.6.0.2-0ubuntu1 3.6.2-0ubuntu2~ubuntu12.10.1
2012-11-24 21:52:48 upgrade libgnome-control-center1:i386 1:3.4.2-0ubuntu19 1:3.6.3-0ubuntu6~ubuntu12.10.1
2012-11-24 21:52:48 upgrade libnautilus-extension1a:i386 1:3.6.2-0ubuntu0.1~quantal1 1:3.6.3-0ubuntu2~ubuntu12.10.1
2012-11-24 21:52:49 upgrade nautilus:i386 1:3.6.2-0ubuntu0.1~quantal1 1:3.6.3-0ubuntu2~ubuntu12.10.1
2012-11-24 21:53:25 upgrade gnome-control-center:i386 1:3.4.2-0ubuntu19 1:3.6.3-0ubuntu6~ubuntu12.10.1
2012-11-24 21:53:26 upgrade gnome-control-center-data:all 1:3.4.2-0ubuntu19 1:3.6.3-0ubuntu6~ubuntu12.10.1[/FONT]

Anyone else experiencing this?

---

### Post by Mr. Picklesworth on 2012-11-24
Yeah, I am seeing this on two different computers which I foolishly updated at the same time. Looks a really messed up update :(

I'm guessing the problem is the new gnome-settings-daemon, so I will try reverting it and I'll let you know how it goes.

Edit:
Yep, that solves it. Pretty sure it's just gnome-settings-daemon, but I broke it again trying to pinpoint it. As long as the new settings daemon is running, GTK apps crash. (I was thinking it might be the updated Canberra module, but I don't really have the time to fiddle with that right now).

---

### Post by morgan71 on 2012-11-24
Ok, I'll give it a try later. Thanks a lot for the help.

---

### Post by Quicksand on 2012-11-25
Oh good. I thought I did something to b0rk things up.

Upgraded, couldn't log in, grabbed the iPad, and found this thread. Ubuntu Forums delivers.

---

### Post by morgan71 on 2012-11-25
I reverted gnome-settings-daemon, but that didn't make any difference for me even though I rebooted. After that I reverted the other packages and now it's working. I think it was gnome-themes-standard that solved it for me, perhaps in combination with gnome-settings-daemon and some of the other packages.

---

### Post by Phred on 2012-11-25
There is an update in Gnome3 PPA for GTK+ that solve that problem.

---

### Post by papabean on 2012-11-25
> **morgan71 said:**
> I think it was gnome-themes-standard that solved it for me

That was the culprit for me. Reverted gnome-settings-daemon first - no change - GDM never finishes loading and no desktop.

Reverted gnome-themes-standard and upgraded gnome-settings-daemon - back in the gnome-shell via GDM.

Now I just have to remember NOT to upgrade gnome-settings-daemon until the NEXT version.

---

### Post by papabean on 2012-11-25
> **Phred said:**
> There is an update in Gnome3 PPA for GTK+ that solve that problem.

Could you be more specific?  The packages I have installed and available for update are in sync with the PPA.

---

### Post by Phred on 2012-11-25
> **papabean said:**
> Could you be more specific?  The packages I have installed and available for update are in sync with the PPA.

Earlier when I made the update, the only upgradable packages were (From Gnome3 team PPA):
gir1.2-gtk-3.0
libgail-3-0
libgtk-3-0
libgtk-3-bin
libgtk-3-common

And after upgrading these, everything works fine again.

Now I can also upgrade gnome-accessibility-themes and gnome-themes-standard, but I don't dare to do so as they seem to break things again. See that thread:
[http://ubuntuforums.org/showthread.php?p=12372368](http://ubuntuforums.org/showthread.php?p=12372368)

---

### Post by papabean on 2012-11-25
Those were the same updates I had just prior to the loss of functionality. I'm still pointing the finger at gnome-themes-standard, but I'm reluctant to upgrade it again just to be sure.

---

### Post by morgan71 on 2012-11-25
> **Phred said:**
> 
Now I can also upgrade gnome-accessibility-themes and gnome-themes-standard, but I don't dare to do so as they seem to break things again. See that thread:
[http://ubuntuforums.org/showthread.php?p=12372368](http://ubuntuforums.org/showthread.php?p=12372368)
I have done a complete upgrade now, including those two packages, and everything works fine for me. I suspect it was the purging that bricked the other guy's system. It's not 100% safe fiddling with ppa's.

---

### Post by Quicksand on 2012-11-25
Fixed for me now -- the overnight set of updates cleared the problem, just as Phred reported.

---

### Post by papabean on 2012-11-25
Curious why I ran into this problem since I performed the upgrades this morning. I will try upgrading again when I'm back in front of my computer.

UPDATE: Still cannot upgrade gnome-themes-standard without causing breakage. Currently using 3.6.0.2-0ubuntu1 without issues.

---

