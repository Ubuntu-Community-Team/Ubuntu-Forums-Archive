---
title: "Can't login with KDE, must use Gnome instead"
date: 2010-10-31
forum: Desktop Environments
---

### Post by wiseguy12851 on 2010-10-31
I had recently installed both KDE and Gnome in the same machine, everything was going great for several hours while I was customizing KDE until I was dragging an icon across a part of the screen and suddenly the screen went black and the computer restarted, when I tried logging back into the desktop with KDE for the first few seconds it tries to login, then the screen goes momentarily black and suddenly I'm back at the login screen. When I log into Gnome everything goes normally.

I do have the latest version of everything since I update daily in case your wondering what version I have, I also am using Ubuntu 10.10.

---

### Post by Zorael on 2010-11-02
Are there any interesting errors in **/var/log/kdm.log**?

As a workaround you could try deleting all your plasma settings, making it recreate them from defaults, just incase you managed to hit some exotic bug that crashes it and cascades until it crashes X. Obviously, depending on whatever is in the logs, such a settings file may be of interest to the KDE developers, so let's just rename them for now.

```
$ mkdir ~/plasma-backup
$ mv ~/.kde/share/config/plasma* ~/plasma-backup/
```

---

### Post by wiseguy12851 on 2010-11-15
Sorry for such a long time between last response, I've been very busy, future responses will be much quicker

I checked over KDE logs, none exist that start with kde in the area you told me to look

I moved the plasma settings into a backup folder but nothing changed, I then renamed the entire .kde folder as a backup folder but still nothing changed so now everything is back how it was, for the heck of it I tried logging in again under KDE and still no change

Here's what happens in detail:

[LIST=1]
[*]I login
[*]The startup screen appears with the icons fading in based on the progress of KDE loading (The usual when your waiting for your desktop to appear)
[*]The first icon slowly fades in
[*]The screen flickers for a split second, goes to black, another second passes
[*]The drumroll happens and I'm back at the login screen
[/LIST]

---

