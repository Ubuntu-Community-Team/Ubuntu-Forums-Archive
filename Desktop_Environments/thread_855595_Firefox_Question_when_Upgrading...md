---
title: "Firefox Question when Upgrading.."
date: 2008-07-10
forum: Desktop Environments
---

### Post by sports fan Matt on 2008-07-10
Why when you get a notice to update Firefox, does it say "Not authenicated"?

---

### Post by pluckypigeon on 2008-07-10
> **sox fan Matt said:**
> Why when you get a notice to update Firefox, does it say "Not authenicated"?

Yes, because I have added the FTA Launchpad Repos. Otherwise No

---

### Post by FuturePilot on 2008-07-10
Sometimes that happens when the repository key is not authenticating correctly. Usually running ```
sudo apt-get update
``` fixes it.

---

### Post by jpeddicord on 2008-07-10
Moved to Desktop Environments. Do what FuturePilot said first; if it still happens check to make sure it isn't coming from a PPA.

If you're not sure, paste the output of:```
apt-cache showpkg firefox
```

---

