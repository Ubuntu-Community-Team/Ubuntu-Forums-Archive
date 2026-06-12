---
title: "Two iBus icons in KDE systray"
date: 2010-11-21
forum: Desktop Environments
---

### Post by Rondonjin on 2010-11-21
As per title. Kubuntu 10.10 new install fully updated. Installed KDE 4.5.3 from Kubuntu PPA repo. Then installed Japanese language support. Two iBus icons are showing up in the KDE systray. One appears to be inactive when switching input method to Japanese.

Known bug? Freak of nature? Workaround available?

TIA.

---

### Post by mogliii on 2011-08-06
Hi,

I had the same problem with KDE4.7 Kubuntu 11.04. (Running Netbook Plasma)

However I resolved it, kind of. I created an autostart entry for "ibus-daemon", and now when its autostarted at the beginning I only have one icon (the one that changes depending on input method).

So have a try if autostarting resolves it. The automatically created Menu item for ibus in KDE appears to be "ibus-setup".

---

