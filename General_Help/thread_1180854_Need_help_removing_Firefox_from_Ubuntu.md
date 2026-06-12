---
title: "Need help removing Firefox from Ubuntu"
date: 2009-06-07
forum: General Help
---

### Post by Eyebrows Mulligan on 2009-06-07
Okay, so I've had a problem with Firefox for quite some time. For some reason, the Back, Forward, Refresh and Stop buttons have mysteriously stopped working, as well as the home page not loading on startup, and the current url not appearing either.

Since then I've always assumed it was just another of Linux's quirks, and just one more thing I'd have to live with. But it's been getting on my nerves as well as causing several pages of lost work, and I decided to do something about it.

Recently, I tried going into add/remove programs and uninstall it, but that's when it came up with this error message:

> 
**Cannot remove 'firefox-3.0-branding'**

One or more applications depend on firefox-3.0-branding. To remove firefox-3.0-branding and the dependent applications, use the Synaptic package manager.


So what should I do from here?

---

### Post by hyperdude111 on 2009-06-07
It is not one of linux's quirks. To fix dont remove firefox but remove your firefox configuration settings. 

Go to Home the press "ctrl-H" go to the .mozilla folder.

rename the firefox folder to firefox.bak and it should work. This wont remove firefox but fix your problem.

---

### Post by ActiveFrost on 2009-06-07
> System -> Administration -> Synaptic Package Manager
From there, search for "firefox" and uninstall it ! Add/Remove is good only for installing software .. if you want to remove something, use Synaptic.

---

### Post by Eyebrows Mulligan on 2009-06-07
> **hyperdude111 said:**
> It is not one of linux's quirks. To fix dont remove firefox but remove your firefox configuration settings. 

Go to Home the press "ctrl-H" go to the .mozilla folder.

rename the firefox folder to firefox.bak and it should work. This wont remove firefox but fix your problem.

Wow never would have thought of that. Okay problem solved! :p

THE END

---

