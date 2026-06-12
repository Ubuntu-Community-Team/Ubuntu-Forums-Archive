---
title: "Problem after removing unity"
date: 2012-09-24
forum: Desktop Environments
---

### Post by pumex1990 on 2012-09-24
Hi,
I've installed gnome-session-fallback because I prefer classic gnome. My problem is that after logout and selecting "Gnome classic" my desktop looks like I have both: Unity and Gnome running at the same time (you can see this at the screenshot). How can I deal with it?

---

### Post by robtygart on 2012-09-24
Log-out, at the sign in screen look to the right top of the log-in box, there is a Ubuntu logo, "click it!" Choose the one you downloaded.

---

### Post by pumex1990 on 2012-09-24
I did this, the screenshot is taken after I logged out, clicked on the Ubuntu logo and selected "Gnome classic" which is suppose to look as the old ubuntu (I also did this on the other computer and it worked, I have absolutely no idea why this is not working here)

---

### Post by josephmills on 2012-09-24
Please log into the DE that you want to use (gnome session I guess)  then open terminal 
enter in 
```
ps aux | grep unity 
```

then paste that her for us to see. Thanks

---

### Post by pumex1990 on 2012-09-24
delete this message please ;)

---

### Post by pumex1990 on 2012-09-24
This is what I get:

```

kacper@kacper-desktop:~$ ps aux | grep unity
kacper   11467  2.2  0.4 159580 16104 ?        Sl   18:29   0:00 /usr/lib/unity/unity-panel-service
kacper   11572  1.6  0.3  80652 12396 ?        Sl   18:30   0:00 /usr/lib/unity-lens-applications/unity-applications-daemon
kacper   11574  0.5  0.1  94988  6156 ?        Sl   18:30   0:00 /usr/lib/unity-lens-files/unity-files-daemon
kacper   11582 21.2  0.4  98404 18904 ?        Sl   18:30   0:02 /usr/lib/unity-lens-music/unity-music-daemon
kacper   11583  1.3  0.3  96772 12868 ?        Sl   18:30   0:00 /usr/bin/python /usr/lib/unity-lens-video/unity-lens-video
kacper   11706  1.3  0.3 108552 13676 ?        Sl   18:30   0:00 /usr/bin/python /usr/lib/unity-scope-video-remote/unity-scope-video-remote
kacper   11721  0.1  0.0  85040  3720 ?        Sl   18:30   0:00 /usr/lib/unity-lens-music/unity-musicstore-daemon
kacper   11750  0.0  0.0   5612   836 pts/0    S+   18:30   0:00 grep --color=auto unity
kacper@kacper-desktop:~$ 




```

---

### Post by Frogs Hair on 2012-09-24
Looks like Unity/Ubuntu 2D is still installed.

---

### Post by pumex1990 on 2012-09-25
So which packages should I remove?

---

### Post by kansasnoob on 2012-09-25
Try the classic (no effects) session:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

Regular gnome classic uses the Compiz window manager, whereas classic (no effects) uses Metacity. And it seems like a lot of Ubuntu's Unity settings are "hard-coded" to compiz :(

---

### Post by pumex1990 on 2012-09-25
No effects works, but I'd prefere to use version with effects, because it looks much better... is there anything I can try to make it works?

---

### Post by Frogs Hair on 2012-09-25
> **pumex1990 said:**
> So which packages should I remove?

I have not tried this.  [http://ubuntublog.org/how-to-remove-unity-desktop-in-ubuntu-12-04.htm](http://ubuntublog.org/how-to-remove-unity-desktop-in-ubuntu-12-04.htm)

```

sudo apt-get remove unity unity-2d-places unity-2d unity-2d-panel unity-2d-spread unity-asset-pool unity-services unity-lens-files unity-lens-music unity-lens-applications gir1.2-unity-4.0 unity-common indicator-sound indicator-power indicator-appmenu libindicator6 indicator-application evolution-indicator indicator-datetime indicator-messages libnux-1.0-0 nuxtools

```

---

### Post by robtygart on 2012-09-25
You can also open your software center and download "synaptic package manager" and look for the unity in synaptic, it will give you an option to "Remove" or "Reinstall"

---

### Post by newb85 on 2012-09-25
Do you by any chance have the CompizConfig Settings Manager installed?

If you do: open it, go to Preferences (along the left side) and see which profile is selected.  If it's "unity" switch it to "Default".

---

