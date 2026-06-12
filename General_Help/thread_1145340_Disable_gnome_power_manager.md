---
title: "Disable gnome power manager ?"
date: 2009-05-01
forum: General Help
---

### Post by Eemeez on 2009-05-01
Is there are way to fully disable the gnome power manager?

My laptop charger is not working right (for some years now), It keeps giving the power 2 seconds, then stops for 2 seconds. With the Ubuntu 9.04 new notification systems, the system gives me a notification for every two seconds (charging/ not charging). There is no way to disable the notification, but I can kill the process "gnome-power" and disable it from the startup.

But the problem is, that "gnome-power" starts up with some programs. Most importantly with VLC. And those notifications kill the movie watching (proceessor is fully occupied with notifications and cannot play video).

Can somebody give me a hint how to fully disable power manager ?

Regards,
Eemeez

---

### Post by soro2005 on 2009-05-01
In System --> Preferences --> Startup Applications, clear the box next to Power Manager. Log out and in and see whether that's doing the job. :-)

Oops sorry, you've already done that. My bad.

You can uninstall the package gnome-power-manager. It's going to take down the package ubuntu-desktop, which is just a meta package to ensure that you always have all the packages that are part of the Ubuntu Desktop. So uninstalling it won't have an immediate effect, but might have consequences down the road.

I guess the power manager starts with vlc to make sure that the screensaver doesn't kick in while reproducing a video.

---

### Post by Eemeez on 2009-05-02
> **soro2005 said:**
> In System --> Preferences --> Startup Applications, clear the box next to Power Manager. Log out and in and see whether that's doing the job. :-)

Oops sorry, you've already done that. My bad.

You can uninstall the package gnome-power-manager. It's going to take down the package ubuntu-desktop, which is just a meta package to ensure that you always have all the packages that are part of the Ubuntu Desktop. So uninstalling it won't have an immediate effect, but might have consequences down the road.

I guess the power manager starts with vlc to make sure that the screensaver doesn't kick in while reproducing a video.

I did not uninstall the power manager (and ubuntu-desktop), but the last line gave me a tip and I found out the option in VLC, that started the power manager and disabled it. Thanks!

---

