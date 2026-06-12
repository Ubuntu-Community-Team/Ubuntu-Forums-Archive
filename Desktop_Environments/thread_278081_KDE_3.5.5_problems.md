---
title: "KDE 3.5.5 problems"
date: 2006-10-15
forum: Desktop Environments
---

### Post by Latem on 2006-10-15
I just dist-upgraded my system (Dapper), and got KDE 3.5.5, and all the updates.  There were a few (like 3) conflicts in the upgrade process, kaudiocreator wanted KDE 3.5.3 specifically, and another problem with kdebase, but sudo apt-get -f install seemed to install everything without issue.  I don't think much is broken. In the Adept package list, everything looks ok.  And for the most part everything seems to be fine so far.  Amarok works, Konqi works, Konversation works, Kopete etc... I do have two problems:

1.  My in-application fonts seem different.  Either it's a different font somehow, or they aren't being AA'ed.  It looks more like they aren't being AA'ed.  My taskbar and KMenu fonts are fine, the icon fonts on the desktop are fine, and my window border fonts are fine.  But fonts in the applications, in the menu, websites, edits, etc... are different, and don't appear to be AA'ed. Even for example if I right click on this edit box, the fonts in the context menu are messed up.  If I right-click on the desktop, the context-menu fonts are fine.

2. This prompted me to go into System Settings | Appearance to check this out.  Well my Appearance section always crashes when I try to enter it.  Other sections seem to be working fine.  This is console printout:

> systemsettings
kio (KSycoca): Trying to open ksycoca from /var/tmp/kdecache-bojan/ksycoca
adding Colours /usr/share/applications/kde/colors.desktop
kutils (KCModuleProxy): [void KCModuleProxy::init(const KCModuleInfo&)]
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
kutils (KCModuleProxy): Module not already loaded, loading module
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
adding Fonts /usr/share/applications/kde/fonts.desktop
kutils (KCModuleProxy): [void KCModuleProxy::init(const KCModuleInfo&)]
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
kutils (KCModuleProxy): Module not already loaded, loading module
ScimInputContextPlugin()
kcontrol: Using fontconfig file:/home/bojan/.fonts.conf
kcontrol: Using fontconfig file:/home/bojan/.fonts.conf
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
adding GTK styles and fonts /usr/share/applications/kcmgtk-xdg.desktop
kutils (KCModuleProxy): [void KCModuleProxy::init(const KCModuleInfo&)]
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
kutils (KCModuleProxy): Module not already loaded, loading module
systemsettings: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
adding Icons /usr/share/applications/kde/icons.desktop
kutils (KCModuleProxy): [void KCModuleProxy::init(const KCModuleInfo&)]
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
kutils (KCModuleProxy): Module not already loaded, loading module
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
adding kbfx Applet /usr/share/applications/kde/kcmkbfx.desktop
kutils (KCModuleProxy): [void KCModuleProxy::init(const KCModuleInfo&)]
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
kutils (KCModuleProxy): Module not already loaded, loading module
kdecore (KConfigSkeleton): Creating KConfigSkeleton (0x833fd70)
kdecore (KConfigSkeleton): KConfigSkeleton::readConfig()
kdecore (KConfigDialogManager): Widget 'tabWidget' (QTabWidget) remains unmanaged.
kdecore (KConfigDialogManager): Widget 'btnSaveAs' (QPushButton) remains unmanaged.
kdecore (KConfigDialogManager): Widget 'btnSaveTheme' (QPushButton) remains unmanaged.
kdecore (KConfigDialogManager): Widget 'btnApplyTheme' (QPushButton) remains unmanaged.
kdecore (KConfigDialogManager): WARNING: A widget named 'kcfg_ThemeList' was found but there is no setting named 'ThemeList'
systemsettings: /root/kde355/kdelibs/kdelibs-3.5.5/./kdecore/kconfigdialogmanager.cpp:219: bool KConfigDialogManager::parseChildren(const QWidget*, bool): Assertion `false' failed.
KCrash: crashing... crashRecursionCounter = 2
KCrash: Application Name = systemsettings path = <unknown> pid = 5728

Anyone got any ideas on how to fix these?

Thanks a lot,

Latem

---

### Post by Manzabar on 2006-11-11
I'm getting a similar [error](http://ubuntuforums.org/showthread.php?t=297913) and the only way I've found to solve it so far is to delete the .kde folder in my home folder.  But that's a pain and only solved my problem temporarily.

---

