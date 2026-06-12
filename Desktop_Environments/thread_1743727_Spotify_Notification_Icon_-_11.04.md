---
title: "Spotify Notification Icon - 11.04"
date: 2011-04-29
forum: Desktop Environments
---

### Post by scooby359 on 2011-04-29
It seems there's a glitch with the Notification applet when using Classic Ubuntu - not sure if it's an issue in Unity as I can't use it on my computer.

Normally, when Spotify runs, it puts it's icon in the notification tray, and when the window's been closed, you can use the icon to open the window again.

But at the moment, it's not showing. The only way I can get it is to remove the applet from the panel, then add it again and the icon shows. The effect isn't sticking though - when the computer is rebooted, the applet stops working again.

Any ideas on how to fix this?

Cheers

---

### Post by KrisDouglas on 2011-05-03
If you click the volume control the Spotify interface has been moved there. This is just extending the level of integration Ubuntu has to Spotify Linux.

---

### Post by davidjmemmett on 2011-05-03
This does mean that you cannot close the app through the right click menu that used to be available, instead having to use `kill` or `killall`.

---

### Post by MrQuincle on 2011-05-27
I can confirm this behavior.

In Unity no icon shows up, neither under the sound/loudspeaker icon (only Banshee does). So, if I accidently minimize spotify, there is no way to get it back. Only solution is "pkill -9 spotify" and run it again.

---

### Post by HiImTye on 2011-06-14
open a terminal and enter the following
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

restart

your icon should appear

---

### Post by MrQuincle on 2011-06-22
> **HiImTye said:**
> open a terminal and enter the following
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

Thank you, that works indeed! The default icons become a little less responsive now. I have first to click on the clock, and then I can move to the left and see the pop-down menu for music, network, or bluetooth. But it works! Thanks again!

---

