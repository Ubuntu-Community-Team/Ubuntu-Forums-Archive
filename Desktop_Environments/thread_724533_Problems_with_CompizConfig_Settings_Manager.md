---
title: "Problems with CompizConfig Settings Manager"
date: 2008-03-14
forum: Desktop Environments
---

### Post by ftpvk on 2008-03-14
I got the latest version of ubuntu and wanted to get the full compiz fusion.

I uninstalled the default compiz fushion that come with 7.10 and installed the full version.

Installation goes great as according to the [instructions ]("http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/")

Problem is I cannot launch the compiz manager from system  - preferences, I try ccsm in the terminal but get the following:

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

I suspect that when I was uninstalling the pre installed compiz,I used a command that I found in [these forums]("http://ubuntuforums.org/showthread.php?t=533201") that messed it up:

sudo aptitude remove libgnome-compiz-manager0 compiz-extra libcompizconfig0 compiz-dev compiz-gtk compiz-kde compiz-settings libcompizconfig-backend-gconf compiz-config-ini gcompizthemer compiz-plugins libgnome-compiz-manager-dev compizconfig-backend-kde compizconfig-settings-manager python-compizconfig compiz-config-gnome taskbar-compiz compizconfig-plugin compiz-freedesktop-dev compiz-fusion-plugins-unofficial compiz-bcop compiz-ccs-settings-manager libgnome-compiz-manager libcompizconfig0-dev compiztools compizconfig-settings-legacy compiz-fusion-plugins-extra compiz-compcomm-plugins-main compiz-fusion-plugins-unsupported compiz compiz-extra-plugins compiz-fusion-plugins-main libcompizconfig-backend-kconfig compiz-core compiz-decorator gnome-compiz-manager compiz-fusion-plugins-main compiz-gnome libcompizconfig-dev libgnome-compiz-manager0-dev libcompizconfig0 libcompizconfig-backend-gconf libcompizconfig0-dev libcompizconfig-backend-kconfig libcompizconfig-dev

can anyone please suggest how to fix this 

thanks!

---

