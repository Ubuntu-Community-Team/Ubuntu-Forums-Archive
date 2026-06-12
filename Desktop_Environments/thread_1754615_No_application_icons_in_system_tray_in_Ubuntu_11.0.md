---
title: "No application icons in system tray in Ubuntu 11.04"
date: 2011-05-10
forum: Desktop Environments
---

### Post by Uewd on 2011-05-10
When I use the Classic Ubuntu look in Ubuntu 11.04 and open an application such as Multiget File Downloader or Parcellite clipboard manager (or any application that displays its Icon in system tray), I can see their icons in the notification area. In Unity, when I open an application such as Multiget File Downloader or Parcellite clipboard manager or any application that displays its Icon in system tray), I can't find their icon in system tray. How can I fix this problem?

Explanation was a bit confusing, sorry.
Please help.
Thanks,
Uewd.

---

### Post by kherring7383 on 2011-05-10
Have you tried to enable the Notification Area on the Panel? Right click on the Panel, then from the Add to Panel options select Notification Area and see if this helps.

---

### Post by Krytarik on 2011-05-10
In Unity, most systray icons of applications are blocked by default, see here on how to whitelist specific or all applications:
[http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html](http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html)

Greetings.

---

### Post by Uewd on 2011-05-10
> **kherring7383 said:**
> Have you tried to enable the Notification Area on the Panel? Right click on the Panel, then from the Add to Panel options select Notification Area and see if this helps.
This does not apply to Unity.

---

### Post by Uewd on 2011-05-10
> **Krytarik said:**
> In Unity, most systray icons of applications are blocked by default, see here on how to whitelist specific or all applications:
[http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html](http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html)

Greetings.
Thank you very much. Worked perfectly!!!
Also Thanks for all who replied to help me.

---

### Post by fallenfruit on 2011-05-10
I ran the command to whitelist all applications, which worked.  But the application icons are now covering up the networking icon and the volume icon.  Specifically, the Workrave application icon is covering them.  Maybe Workrave is taking up more space that it is allotted.

---

