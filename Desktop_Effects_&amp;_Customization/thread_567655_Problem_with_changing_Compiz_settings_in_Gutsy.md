---
title: "Problem with changing Compiz settings in Gutsy"
date: 2007-10-04
forum: Desktop Effects &amp; Customization
---

### Post by BulletzBill on 2007-10-04
Hey guys,

Ok, first off I am a complete Linux/Ubuntu newbie, so bear with me here if I say something that doesn't make sense. Anyway, I am using Gutsy and I trying to configure Compiz via the compizconfig-settings manager. The desktop effects themselves are currently working but when I go into the settings manager to change some of the options, they do not have any effect. Also, if I go into Preferences and change the Backend from GConf to Flat-file, I receive an error saying the manager closed unexpectedly. When I hit Report Problem I get another window saying the following:

"The problem cannot be reported:

You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs:

fontconfig, libssl0.9.8, libfontconfig1, fontconfig-config, libx11-data"

What commands do I need to run to upgrade those packages?

And does anyone have any ideas as to why I can't modify the settings succesfully?

Thanks in advance.

---

### Post by MiD-AwE on 2007-10-04
Have you tried Applications->Accessories->Terminal

```
sudo apt-get update
```

This should update everything.

---

