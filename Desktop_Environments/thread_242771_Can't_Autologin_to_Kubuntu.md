---
title: "Can't Autologin to Kubuntu"
date: 2006-08-24
forum: Desktop Environments
---

### Post by SpongeBob SquarePants on 2006-08-24
Morning all,

Just reinstalled Kubuntu after a few problems with my machine and everything is running reasonably well. Apart from the fact that I can't log in automatically.

I've been to login manager/convenience and ticked the enable "auto-log-in" option. I've also tried the "allow passwordless-logins" option, and tried changing the "pre-select user" option to "specific" rather than "previous".

But I still get the log-in screen in Kubuntu and have to enter my name and password manually. When I return to the Log-in manager the setting are as I changed them, so it's not dropping the settings, they're just not working for some reason.

any ideas?

---

### Post by hraposo on 2006-08-24
Try this
sudo /usr/sbin/gdmsetup

---

### Post by SpongeBob SquarePants on 2006-08-24
Worked a treat. Great stuff!!!

Any idea why I'd have to access GNOME to get KDE to get it's act together?

Anyway, problem solved, so thanks a lot :p

---

