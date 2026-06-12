---
title: "Deleted the shutdown button"
date: 2014-04-19
forum: Desktop Environments
---

### Post by wamgx on 2014-04-19
Hey guys,

I've already screwed up lubuntu 14.04: I've deleted the shutdown button in the task bar.

Normal situation: 
[IMG]http://trackmania-carpark.com/imagespark/odd/up/5352ab8b0b582.png[/IMG]
Now:
[IMG]http://trackmania-carpark.com/imagespark/odd/up/5352abb63d9ef.png[/IMG]The problem is, I can't add the 'Shutdown' icon again because it is not in the available applications.

Does someone have a solution?

TIA :)

---

### Post by 23dornot23d on 2014-04-19
There is some information about where all the files are towards the bottom of this help link - from xfce

[https://wiki.xfce.org/tips?&#handle_acpi_event_for_power_button_show_xfce_logout_options](https://wiki.xfce.org/tips?&#handle_acpi_event_for_power_button_show_xfce_logout_options)

---

### Post by bapoumba on 2014-04-19
Probably here: [http://ubuntuforums.org/showthread.php?t=1860263](http://ubuntuforums.org/showthread.php?t=1860263)

Here is my /usr/share/applications/lubuntu-logout.desktop on Trusty:
```
[Desktop Entry]
Name=Shutdown
Name[zh_TW]=&#38364;&#27231;
Comment=Shutdown or Reboot
Icon=system-shutdown-panel
Exec=lxsession-default quit
NoDisplay=true

```

Please check with yours.

---

### Post by Dennis N on 2014-04-19
Same problem as here:

[http://ubuntuforums.org/showthread.php?t=2134948](http://ubuntuforums.org/showthread.php?t=2134948)

See Post #10 for a solution.

---

### Post by bapoumba on 2014-04-19
> **Dennis N said:**
> Same problem as here:

[http://ubuntuforums.org/showthread.php?t=2134948](http://ubuntuforums.org/showthread.php?t=2134948)

See Post #10 for a solution.
Thanks :)

---

### Post by wamgx on 2014-04-19
My */usr/share/applications/lubuntu-logout.desktop* on Trusty was the same as yours, bapoumba.

I copy-pasted amjjawad code except I left the *Exec=lxsession-default quit* of Thrusty (instead of the *Exec=lubuntu-logout*)
```

[Desktop Entry]
Name=Shutdown
Name[zh_TW]=&#38364;&#27231;
Type=Application
Comment=Shutdown or Reboot
Icon=system-shutdown-panel
Exec=lxsession-default quit
#NoDisplay=true
Categories=Settings;DesktopSettings
```

It worked just fine, thank you very much. :D

---

### Post by bapoumba on 2014-04-19
Glad to see you fixed it. Had you tried Dennis N's solution before modifying the /usr/share/applications/lubuntu-logout.desktop file ?
Anyway, please mark your thread as solved (under Thread Tools menu), thanks :)

---

### Post by wamgx on 2014-04-19
Nope, didn't try Dennis N's solution. I fixed it when there where only 2 replies to my post :KS

Big thanks to all of you :)

---

