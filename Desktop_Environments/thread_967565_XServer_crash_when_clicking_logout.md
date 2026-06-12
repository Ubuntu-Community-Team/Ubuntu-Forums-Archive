---
title: "XServer crash when clicking logout"
date: 2008-11-02
forum: Desktop Environments
---

### Post by welshy20 on 2008-11-02
Hi,

Having a problem when trying to log out of GNOME.
When clicking the logout button, the XServer appears to partially crash, mouse remains active, however all interaction with the window manage other than this stops.
I've noticed in another post that someone was able to resolve this by activating the Ask Before Logout option in System > Preferences > Session, however I see no such option there, am I just looking the wrong place.
Problem is not urgent as GNOME can still be quit by forcing a reset of the XServer, but it's getting kind of annoying so any help would be appreciated.

Thanks,
Andy,

---

### Post by davidvasco on 2009-03-02
I saw this problem in 8.10 (Intrepid). I'm using the NVIDIA proprietary drivers. I was able to make the problem go away by switching the driver from version 177 to 173. Both versions were shown under System > Administration > Hardware Drivers.

Hope this helps!

---

