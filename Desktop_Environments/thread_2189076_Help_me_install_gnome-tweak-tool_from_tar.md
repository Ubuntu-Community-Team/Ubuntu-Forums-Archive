---
title: "Help me install gnome-tweak-tool from tar"
date: 2013-11-20
forum: Desktop Environments
---

### Post by miceagol on 2013-11-20
I'm trying to install the [latest gnome-tweak-tool]("https://wiki.gnome.org/GnomeTweakTool"). However, I'm stuck at an unmet dependency when running autogen.sh:

```

configure: error: Package requirements (gsettings-desktop-schemas >= 3.4.0) were not met:

No package 'gsettings-desktop-schemas' found

```

I have gsettings-desktop-schemas from the repo, but it's an older version than required. Could anybody assist me to install the correct version from source?

---

### Post by Frogs Hair on 2013-11-20
Are you using Gnome 3.9 ? If you are using the 3.9/3.10  gnome 3  team ppa that should be  a software center or synaptic installation and if not you won't be able to install the package due to dependency differences between the Gnome versions  . Whether using the ppa or not the package is in the software center for the version of gnome currently in use.

---

### Post by miceagol on 2013-11-20
I'm using Gnome 3.10. The version that is in the software center is [crashing]("http://ubuntuforums.org/showthread.php?t=2186689"), so I'm trying to install the latest to see if that helps.

---

