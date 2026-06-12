---
title: "firefox uses gnome's preferred apps instead of kde's"
date: 2011-02-20
forum: Desktop Environments
---

### Post by halfbeing on 2011-02-20
Hello

Currently Firefox uses Gnome's preferred applications to deal with downloaded files. For instance it opens the containing folders in Nautilus. How do I make it use Konqueror and my KDE preferred applications instead?

Thanks

---

### Post by ankspo71 on 2011-02-20
Hi,
Some of these preferences can be changed in firefox at Menu > Edit > Preferences > Applications. But other than that... here's a few things to try...

While in the KDE desktop environment, try going to System Settings > Default Applications > File Manager; and make sure the default file manager for KDE is Dolphin instead of Nautilus.

Also, see if you have the package called "firefox-kde-support" installed. I'm not sure what it actually does, but it seems like it might help.

The Firefox add-on called "Open With" is a very handy addon too. With it you can create menu entries in firefox menus to open images/media/files/links in different applications. I like to use it to open various media stream links and podcasts in VLC. [https://addons.mozilla.org/en-US/firefox/addon/open-with/](https://addons.mozilla.org/en-US/firefox/addon/open-with/)

Hope these ideas help.

---

### Post by aeiah on 2011-02-20
try launching with ```
export DE=kde && firefox
```

if that works, then you just need to make sure the desktop environment is set to kde. you can add export DE=kde to your .bashrc file or crate a wrapper script with:```
export DE=kde && $@;
```

call it kde_wrapper.sh

then you can launch firefox with ```
~/path/to/kde_wrapper.sh firefox
```

this is if you cant seem to get it working using the control panel or whatever though

---

### Post by svenni on 2011-05-12
The package firefox-kde-support certainly did the trick for me.

Thanks for the tip!

---

