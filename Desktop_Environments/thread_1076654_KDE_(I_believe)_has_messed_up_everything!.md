---
title: "KDE (I believe) has messed up everything!"
date: 2009-02-21
forum: Desktop Environments
---

### Post by JakeWatkins on 2009-02-21
I can't open PIDGIN, I can't open Synaptic Manager I always get ```
Failed to run /usr/sbin/synaptic as user root. Unable to copy the user's Xauthorization file.
``` I can no longer run the bar at the top that has the "away" "busy" "shut down" "lock computer" on it, my computer will not open documents unless tricked into opening it, it is very hard to open Amarok, Freecell won't even open!

And I believe it has a lot to do with the fact that I just installed KDE (and xfce, for that matter) but I only really use GNOME (wanted to try KDE...).

Every time I try ```
apt-get remove kde
``` I get ```
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

``` I'm the only user on my computer.. could I not be root?

I can only open the KDE terminal for some reason.. but I can use that one. I'm using GNOME, also. Plus, there is a large space in between my task bar and my actual applications, like networking is the only one up, but there's about 2 inches of blank space where nothing to can happen, I've tried moving things, it doesn't help.

Any help, guys? I know this is a doozy =\

---

### Post by kellemes on 2009-02-21
You haven't been reading the standard documentation. ;-)
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Don't ever login as root.
Use "sudo" for terminal apps or "gksudo" for graphical apps ("kdesu" for KDE), this way you get root privileges for the specified application.

And so, you login as user and use a command demanding root privileges like so..
```
sudo apt-get remove kde
```

---

### Post by JakeWatkins on 2009-02-22
I restarted, and synaptic manager opened up fine.. I removed all KDE things then restarted a few times.. and now everything works again!

Even User Switcher (or whatever) works! Ubuntu is back to normal, and all is good in computer kingdom! ;- )

Thanks for the "sudo" part, though! = )

---

