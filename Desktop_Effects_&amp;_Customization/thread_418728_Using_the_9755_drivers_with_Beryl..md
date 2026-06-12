---
title: "Using the 9755 drivers with Beryl."
date: 2007-04-22
forum: Desktop Effects &amp; Customization
---

### Post by Thiago Tomei on 2007-04-22
I found out that using NVidia "new" (9755) drivers with Beryl can be a little tricky. Here is what I found out. Maybe somebody has a use for this tip.

First, I installed the NVidia Restricted Drivers via the Restricted Drivers Manager (System > Administration > Restricted Drivers Manager). This installed the
```
nvidia-glx (1:1.0.9631+2.6.20.5-15.20)
``` package, 
the one we do NOT want.

Then, Beryl... (I did it the mindless way: search for "beryl" in Synaptic, then check the "beryl" package.)

```
beryl (0.2.1.dfsg+git20070318-0ubuntu2)
beryl-core (0.2.1.dfsg+git20070318-0ubuntu2)
beryl-plugins (0.2.1-0ubuntu2)
beryl-plugins-data (0.2.1-0ubuntu2)
beryl-settings (0.2.1-0ubuntu1)
beryl-settings-bindings (0.2.1-0ubuntu1)
libberyldecoration0 (0.2.1.dfsg+git20070318-0ubuntu2)
libberylsettings0 (0.2.1.dfsg+git20070318-0ubuntu2)
```

and Emerald. (Once again, search for "emerald" and check it.)

```
emerald (0.2.1-0ubuntu1)
emerald-themes (0.2.1-0ubuntu1)
libemeraldengine0 (0.2.1-0ubuntu1)
```

To have it load automatically when your session starts, install "beryl-manager"
```
beryl-manager (0.2.1-0ubuntu1)
```
and put the beryl-manager command in the list of Startup Programs, in System > Preferences > Sessions.

Does it work? Good. However, I felt that it worked a little too slow and choppy. Searching for "nvidia" in Synaptic brought to light the existence of the "new" package:
```
nvidia-glx-new (1.0.9755+2.6.20.5-15.20)
```
which contains the 9755 drivers.

So, I completely removed the nvidia-glx, and installed the nvidia-glx-new. For good measure, I removed the .gconf and .gconfd hidden directories (always do that when I mess with X manager / Window Manager stuff - I lose some configurations, but nothing really dramatic. I don't know if it is really necessary though.)  I then run:
```
sudo nvidia-glx-config enable
```
as the package description says, and
```
sudo nvidia-xconfig -add-argb-glx-visuals
```
as the forums say. :)

Unfortunately, i don't remember if I also had to turn the drivers on in the Restricted Drivers Manager or if they turned on themselves. In any case, they must be enabled and in use.

From my experience, Beryl works better with the new drivers. But your mileage may vary.

Feel free to post comments, questions and flames.

---

