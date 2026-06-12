---
title: "Uninstalled Show Desktop widget - how to get it back?"
date: 2010-01-14
forum: Desktop Environments
---

### Post by garryknight on 2010-01-14
While trying to cram as much Kubuntu as possible onto my EeePC 701 4G (should be called the 3.7G), I managed to uninstall the Show Desktop plasma widget. Probably because it isn't actually called plasma-widget-show-desktop. So now I can't find it in Synaptic or using apt-cache search because I don't know what it *is* called.

Can someone tell me how I can get it back on my panel, please?

---

### Post by warfacegod on 2010-01-14
I believe they are called screenlets in GDM. Not sure about KDE.

---

### Post by hansdown on 2010-01-14
Hi garryknight.

I think it is called 

```
kdeplasma-addons
```

---

### Post by OldAlgis on 2010-01-15
> **hansdown said:**
> Hi garryknight.

I think it is called 

```
kdeplasma-addons
```

Since you know what it is called, how do you install (or re-install) kdeplasma-addons?  I did delete it once upon a time and never restored it...  It must be a simple operation, surely - but what?

---

### Post by hansdown on 2010-01-15
Hi OldAlgis.

You should be able to install it using adept.

---

### Post by nerdy_kid on 2010-01-15
```

sudo apt-get install kdeplasma-addons

```

---

### Post by garryknight on 2010-01-15
I thought it might be in there when I read the description for kdeplasma-addons, so I marked it for reinstallation in Synaptic and clicked Apply. Logged out of KDE and back in but it didn't make any difference. I'll have another go... Tomorrow, as it's 2:10 am here.

---

### Post by garryknight on 2010-01-15
Ok, that was it. This time it took and all the old familiar widgets were in the Add Widget list. I now have my Show Desktop widget back. Thanks everybody.

---

### Post by warfacegod on 2010-01-15
Glad to help. Please mark as solved.

---

