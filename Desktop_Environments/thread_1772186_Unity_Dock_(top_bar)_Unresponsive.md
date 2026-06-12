---
title: "Unity Dock (top bar) Unresponsive"
date: 2011-05-31
forum: Desktop Environments
---

### Post by jullyfush on 2011-05-31
So, I was trying to improve my boot speed and uninstalled Gwibber. Since then most of the indicator applet icons in the dock (top bar) are unresponsive (the clock and power icons are still responsive). I'm not sure the events are related, but don't know what else it could be...

I've restarted Unity, rebooted, and reinstalled Gwibber and the problem still persists. I can't find any other threads with this problem. Any ideas??


Edit:
It was from changing the whitelist to 'all'

$: gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"

I found the fix here:
[http://ubuntuforums.org/showthread.php?t=1756700](http://ubuntuforums.org/showthread.php?t=1756700)


"To fix this I opened the dconf-editor and clicked on desktop -> unity -> panel
I clicked on the Set to Default button."

---

### Post by stinkeye on 2011-05-31
Yes changing to "all" can make the indicators unresponsive.
Your better off at this stage just adding the one or two that you really need manually.
Just use the same format
eg I added gnote and artha which seem to work okay.
```
['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray', 'scp-dbus-service', '**gnote**', '**artha**']
```

---

### Post by jullyfush on 2011-05-31
Thanks! That worked for me too.

---

