---
title: "3D Desktop - Newb help"
date: 2007-12-28
forum: Desktop Environments
---

### Post by drw1978 on 2007-12-28
Hi

I have installed all of the compiz applications from synaptic manager.

I have went to GL desktop which shows my graphics card ATI Mobility x700. However ticking the "enable GL desktop" the screen flickers but does not change and im presented with "do you want to keep these settings" i click yes but nothing has changed.

Then under the workspaces tab i have selected "cube and rotation" and set number of viewports to 4 but still I have the regular default desktop.

Is this a problem with the setup/config or are there more settings within the "gnome compiz preferences" that I need to adjust?

Any advise and ideas and guides would be greatly appreciated.

Thank you in advance!

---

### Post by Perpetual on 2007-12-28
What version of Ubuntu are you using?  7.10 comes with compiz-fusion installed by default and can be enabled (if it wasn't enabled during install) by going to System > Preferences > Appearance.  The only thing that needs installed is Compiz Config Settings Manager.

```

$ sudo apt-get install compizconfig-settings-manager

```

Note: you must have the universe repo enabled.

---

### Post by drw1978 on 2007-12-28
I installed 7.10 Gutsy only a few days ago.

Where would I enable it in appearance settings?

---

### Post by Perpetual on 2007-12-28
> **drw1978 said:**
> I installed 7.10 Gutsy only a few days ago.

Where would I enable it in appearance settings?

Visual Effects tab.  Then after installing CCSM, it will be found under System > Preferences > Advanced Desktop Effects Settings.

---

### Post by drw1978 on 2007-12-28
I have went to advanced desktop settings and ticked desktop cube.... nothing has changed?

---

### Post by drw1978 on 2007-12-28
iam also getting "Desktop effects could not be enabled"

---

### Post by Perpetual on 2007-12-28
> **drw1978 said:**
> iam also getting "Desktop effects could not be enabled"

[this may help you.]("http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support")  Also, please backup any important data.  My specialty IS NOT graphics cards so I am only linking this as a reference.  Someone else will be more suited to assist you with this.

---

