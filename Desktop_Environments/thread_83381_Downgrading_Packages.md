---
title: "Downgrading Packages"
date: 2005-10-28
forum: Desktop Environments
---

### Post by ColinG on 2005-10-28
The latest mjpeg tools so far as dvdstyler is concerned is broken. I need therefore to downgrade to an earlier version. Is there a way of doing this via Apt or Adept, or a different approach required?

Many thanks
Colin

---

### Post by shakin on 2005-10-28
[QUOTE=ColinG]The latest mjpeg tools so far as dvdstyler is concerned is broken. I need therefore to downgrade to an earlier version. Is there a way of doing this via Apt or Adept, or a different approach required?

Many thanks
Colin[/QUOTE]

You can force it to a different version. I'm not sure what Adept's interface is, by using Synaptic I just highlight the package, go to the Package menu and click Force Version. Then it shows me all the versions available. The Force Version item will be greyed out if no other versions exist in your repositories. You could possibly add the Hoary repository, downgrade mjpeg tools, then remove the Hoary repository. After that you would need to go back to the Package menu and lock the version so it doesn't get upgraded.

Please note that I don't know if the Hoary version will work in Breezy, so it might be a very bad idea.

---

