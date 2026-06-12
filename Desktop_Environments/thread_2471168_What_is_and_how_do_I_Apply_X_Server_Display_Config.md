---
title: "What is and how do I Apply X Server Display Configration in Nvidia settings?"
date: 2022-01-22
forum: Desktop Environments
---

### Post by makem2 on 2022-01-22
I am using a dual screen windows/ubuntu system with an nvidia gfx card and use the proprietary settings from ubuntu settings. 

I am able to us the 'nvidia-settings' applet to configure the card settings and i make sure ubuntu Display settings match. However, _after saving the settings to 'X Configuration File'_ via the applet and then going to the 'quit' I am asked if I really want to quit. This popup tells me: You have pending changes on following page(s): X Server Configuration - Apply and asks if I really want to quit.

I am unable to find a place within the applet to do this and usually just quit. But, I have niggling problems and want to get rid of this 'Apply' nag.

Does anyone know how to do this?

In the corresponding terminal I have this output which does not seem to apply to ubuntu 21.10:

```

makem@makems-TUF:~$ sudo nvidia-settings
[sudo] password for makem: 

(nvidia-settings:7860): GLib-GObject-CRITICAL **: 13:01:36.382: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
** Message: 13:01:36.532: PRIME: No offloading required. Abort
** Message: 13:01:36.532: PRIME: is it supported? no
Package xorg-server was not found in the pkg-config search path.
Perhaps you should add the directory containing `xorg-server.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xorg-server' found
Package xorg-server was not found in the pkg-config search path.
Perhaps you should add the directory containing `xorg-server.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xorg-server' found
makem@makems-TUF:~$

```

---

### Post by MAFoElffen on 2022-02-06
For the graphic engine... Are you using Wayland or Xorg XServer? Because what you are describing works with Xorg XServer (not with Wayland), but the error messages are saying that Xorg XServer is not there(?) Or is it actually saying that you are running Wayland so Xorg XServer is not loaded? Not sure at the moment...

---

