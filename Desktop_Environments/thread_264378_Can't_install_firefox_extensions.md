---
title: "Can't install firefox extensions"
date: 2006-09-24
forum: Desktop Environments
---

### Post by GarBhaD on 2006-09-24
Everytime I try to install [Videodownloader]("https://addons.mozilla.org/firefox/2390/") (or any other) extension, the yellow bar appears on top with the next message:
"Software installation is currently disabled. Click Edit Options... to enable it and try it again."
The funny thing is that I have that option **enabled**, and addons.mozilla.org **is** in the list (it's there by default anyway).
I even tried to add releases.mozilla.org to the whitelist because that's where the installation link points to, but I get the same message.
Please help.

I'm using Ubuntu 6.06 and up to date.

---

### Post by CaveRat on 2006-09-24
Check this link out and see if might help resolve your problem.

[http://kb.mozillazine.org/Unable_to_install_themes_or_extensions_(Firefox](http://kb.mozillazine.org/Unable_to_install_themes_or_extensions_(Firefox))

---

### Post by GarBhaD on 2006-09-24
> **CaveRat said:**
> Check this link out and see if might help resolve your problem.

[http://kb.mozillazine.org/Unable_to_install_themes_or_extensions_(Firefox](http://kb.mozillazine.org/Unable_to_install_themes_or_extensions_(Firefox))

Thanks a lot!
For some reason, *xpinstall.enabled* was set to *false*. Now it works like it should :D 

I could install the extension without this. I manually downloaded the xpi file and moved it to the extensions folder inside my home directory. When I restarted firefox, it asked for confirmation to install and it worked :p 
Still, the normal behaviour is much better ;) Again, thank you.

---

