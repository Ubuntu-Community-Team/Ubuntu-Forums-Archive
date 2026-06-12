---
title: "slow plasma and kwin after upgrade to 4.3.4"
date: 2010-01-13
forum: Desktop Environments
---

### Post by baxeico on 2010-01-13
I recently upgraded to kde 4.3.4 from backports (Unsupported updates) repository. Previusly I had kde 4.3.2 (Karmic default).

I noticed that now my desktop is way less responsive. For instance Plasma dashboard takes about 5 seconds to show up when I press CTRL-F12. I can see Xorg going to 90% of CPU in the process. With desktop effects disabled the dashboard takes about 3 seconds to show up.

I also see some graphic corruptions sometimes, for example when I maximize Amarok window clicking on the systray icon, sometimes I see a completely garbaged window.

I have a Nvidia GeForce 8400M GS (on a Dell XPS M1330 laptop), and I use the Nvidia binary driver (latest stable version).

On 4.3.2 I didn't have this kind of problems. Someone of you noticed a similar issue?
I'm tempted to downgrade to 4.3.2 again, but I'm not sure how to do it without screwing up my system.

Any idea? Thank you very much for your assistance!

---

### Post by baxeico on 2010-01-14
I want to add that when I log in in KDM the KDE splash screen appears, but when all icons appear (also the big K) I have to wait about 13 seconds before seeing the fade effect on my desktop.

This issue also occurs only after the upgrade from 4.3.2 to 4.3.4 (backports).

Please, is there a way to rollback to 4.3.2 in a simple and safe way?

---

### Post by kellemes on 2010-01-15
What Window-manager are you using?
System Settings -> Default Applications -> Window Manager

In case of Kwin (default window-manager for KDE).
You can fine-tweak features and performance by visiting..
System Settings -> Desktop -> Desktop Effects

Hope this helps.

---

### Post by nerdy_kid on 2010-01-15
create a new user and see if the same issues exist -- often the KDE configs get fried between versions.
Also, what gfx card are you using?  I am using NVIDIA Geforce 8600M with 4.3.4 and no issues.

---

