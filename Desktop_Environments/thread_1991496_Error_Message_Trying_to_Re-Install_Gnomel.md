---
title: "Error Message Trying to Re-Install Gnomel"
date: 2012-05-30
forum: Desktop Environments
---

### Post by Valkyr333 on 2012-05-30
As best as I can tell, my computer has uninstalled the Gnome desktop (without my say-so, mind you) and this is causing me problems. I tried re-installing it in Synaptic, but it gives me an error message,

```
Could not mark all packages for installation or upgrade

The following packages have unresolved dependencies. 
Make sure that all the required repositories are added and enabled in preferences.

gnome:
Depends: swfdec-mozilla but it is not going to be installed
```I searched for swfdec-mozilla and found/installed it, but then trying to install gnome got me the same error but saying it depends on epiphany. Installing epiphany necessitates removing swfdec-mozilla, and gnome can't seem to be installed without both.

I have checked to make sure that all the default software sources are enabled.

Am I missing something, here?

---

### Post by linux12 on 2012-05-30
How are you installing it? Wubi or the Livecd?

---

### Post by Valkyr333 on 2012-05-30
Live CD. =)

---

