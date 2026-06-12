---
title: "How to delete/uninstall workspace themes?"
date: 2010-08-03
forum: Desktop Environments
---

### Post by murphycc on 2010-08-03
Hi everyone,

Occasionally my theme changes from Air back to Oxygen or another theme I had installed (using 10.04). I'm not sure why it does this. So I would like to know how to delete/uninstall a theme. I'm using the System Settings gui under the Appearance menu in KDE. There is a button to install new themes, and I can choose a different theme by clicking on it, but I would like to permanently remove a couple themes I have installed.

In case anyone else has seen themes randomly change from Air back to Oxygen, that is another discussion I would be interested in.

Thanks,
Chris

---

### Post by bschelst on 2010-08-05
Login on terminal
rm -R ~/.kde/share/apps/desktoptheme/[NAME_OF_THEME]

Refresh (open and close) your desktop theme manager.

---

