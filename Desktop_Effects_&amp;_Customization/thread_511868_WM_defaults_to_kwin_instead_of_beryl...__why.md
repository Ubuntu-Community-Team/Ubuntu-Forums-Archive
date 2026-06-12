---
title: "WM defaults to kwin instead of beryl...  why?"
date: 2007-07-28
forum: Desktop Effects &amp; Customization
---

### Post by NiksaVel on 2007-07-28
hey...

I have an edgy setup ubuntu...  with KDE installed over it later on...


the problem that I am experiencing in KDE sessions is that beryl defaults to kwin as the WM instead of beryl...   I change it manually... works fine...  reboot... back to kwin.  Why?

Gnome sessions work just fine.


thanks for any help!

---

### Post by Happy_Man on 2007-07-28
Because KDE doesn't use GNOME's autostarting rules. To get Beryl to start on login:

```
kate ~/.kde/Autostart/Beryl
```

In that file, place: > #!/bin/bash
beryl-manager

And then, ```
chmod a+x ~/.kde/Autostart/Beryl
```

And you're done!

---

