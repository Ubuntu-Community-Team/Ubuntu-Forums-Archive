---
title: "Unable to locate theme engine in module_path"
date: 2010-08-02
forum: Desktop Environments
---

### Post by hazmatzak on 2010-08-02
Yesterday, after installing suggested updates since I last updated a few weeks ago, themes are broken. I am using 10.04 Lucid, now running 2.6.32-24. (Booting the previous kernel did not help.)

After rebooting, I noticed that the login screen had less attractive widgets, which persisted after I logged in. Opening the Appearance Preferences, there were no themes listed. There are a bunch of them in /usr/share/themes. If I copy the Ambiance folder from there to ~/.themes, it will appear in the dialog; but when selected, the Window Border changes, while the Controls do not.

If I run gedit from the shell, I get these messages:
```
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

(gedit:2766): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

```the latter repeated many times. gtk2-engines-murrine (0.90.3+git20100323-0ubuntu3) is installed, including the file /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so. There is also a /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so

There was no GTK_PATH environment variable. (Where does it and GTK_MODULES get set globally?) I tried setting it to /usr/lib, but that had no effect.

It looks like a problem finding and/or loading the required files? Permissions? Dependencies? How do I go about diagnosing this problem?

---

### Post by hazmatzak on 2010-08-16
Bump. Looking at .xsession-errors, the same "warning" is reported for gnome-session, which is certainly reflected by the login screen.

Since the lib*.so file is apparently in the right place, how is the module_path configured?

---

### Post by wkhasintha on 2010-08-27
I'm suffering from the same problem.

---

### Post by Frogs Hair on 2010-08-27
I got a message that my current theme using the murrine engine was no longer a valid theme and one of the colors changed from gray to light blue.

---

### Post by Frogs Hair on 2010-08-28
I discovered that my problem was caused by my Ubuntu Tweak PPA . There is a feature for saving desktop settings , and the more I experimented with it the worse the function of appearance preferences became . I could not even get the ambiance theme to work.

I purged the PPA removed the murrine engine and Ubuntu light themes and ran the GConf Cleaner. I restarted the computer and installed the themes and engine , now , all is well . I will stick with the stable version of Ubuntu Tweak for now , my issues began when I installed the PPA.  Good Luck

---

