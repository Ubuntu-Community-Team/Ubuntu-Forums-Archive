---
title: "kde systemsettings crash"
date: 2009-12-08
forum: Desktop Environments
---

### Post by piedro on 2009-12-08
Hi! 

I installed karmic as ubuntu. afterwards I installed kubuntu-desktop for some users like to have it as alternative. 

but when I use the kde systemsetings for k3b & for policykit-settings 
it crashes. the crash handler says something like: 

> 
[KCrash Handler]
#5  0x00007fa8476ba4b5 in raise () from /lib/libc.so.6
#6  0x00007fa8476bdf50 in abort () from /lib/libc.so.6
#7  0x00007fa8476f2c97 in ?? () from /lib/libc.so.6
#8  0x00007fa8476fcdd6 in ?? () from /lib/libc.so.6
#9  0x00007fa84770170c in free () from /lib/libc.so.6
#10 0x00007fa83bc74056 in PolkitQt::Context::Private::init() () from /usr/lib/libpolkit-qt-core.so.0
#11 0x00007fa83bc75b2d in PolkitQt::Context::hasError() const () from /usr/lib/libpolkit-qt-core.so.0
#12 0x00007fa83c4bbe2f in PolkitKde::PkKAuthorization::PkKAuthorization(QWidget*) () from /usr/lib/libpolkitkdeprivate.so.4
#13 0x00007fa83c6d7e3a in ?? () from /usr/lib/kde4/kcm_pkk_authorization.so
#14 0x00007fa83c6d8a05 in QObject* KPluginFactory::createInstance<KcmPkKAuthorization, QWidget>(QWidget*, QObject*, QList<QVariant> const&) () from /usr/lib/kde4/kcm_pkk_authorization.so
#15 0x00007fa8485aab1e in KPluginFactory::create(char const*, QWidget*, QObject*, QList<QVariant> const&, QString const&) () from /usr/lib/libkdecore.so.5
#16 0x00007fa849c51e96 in KCModuleLoader::loadModule(KCModuleInfo const&, KCModuleLoader::ErrorReporting, QWidget*, QStringList const&) () from /usr/lib/libkutils.so.4
#17 0x00007fa849c575c7 in ?? () from /usr/lib/libkutils.so.4
#18 0x00007fa849c58635 in KCModuleProxy::realModule() const () from /usr/lib/libkutils.so.4
#19 0x00007fa849c58922 in KCModuleProxy::showEvent(QShowEvent*) () from /usr/lib/libkutils.so.4
#20 0x00007fa848a2a7ee in QWidget::event(QEvent*) () from /usr/lib/libQtGui.so.4
#21 0x00007fa8489dbefc in QApplicationPrivate::notify_helper(QObject*, QEvent*) () from /usr/lib/libQtGui.so.4
#22 0x00007fa8489e31ce in QApplication::notify(QObject*, QEvent*) () from /usr/lib/libQtGui.so.4
#23 0x00007fa849612e56 in KApplication::notify(QObject*, QEvent*) () from /usr/lib/libkdeui.so.5
#24 0x00007fa847e4ac2c in QCoreApplication::notifyInternal(QObject*, QEvent*) () from /usr/lib/libQtCore.so.4
#25 0x00007fa848a2faaa in QWidgetPrivate::show_helper() () from /usr/lib/libQtGui.so.4
#26 0x00007fa848a2fd81 in QWidgetPrivate::showChildren(bool) () from /usr/lib/libQtGui.so.4
#27 0x00007fa848a2f99f in QWidgetPrivate::show_helper() () from /usr/lib/libQtGui.so.4
#28 0x00007fa848a30bba in QWidget::setVisible(bool) () from /usr/lib/libQtGui.so.4
#29 0x00007fa848a2fe16 in QWidgetPrivate::showChildren(bool) () from /usr/lib/libQtGui.so.4
#30 0x00007fa848a2f99f in QWidgetPrivate::show_helper() () from /usr/lib/libQtGui.so.4
#31 0x00007fa848a2fd81 in QWidgetPrivate::showChildren(bool) () from /usr/lib/libQtGui.so.4
#32 0x00007fa848a2f99f in QWidgetPrivate::show_helper() () from /usr/lib/libQtGui.so.4



now I like to know how to go further? 

I have to use the policykit-settings in order to use kpackagekit, 
I have to use kapackagekit for those fancy autoupdate and so forth ...

plz help, 
piedro

---

### Post by piedro on 2009-12-09
Funny thing is: 

If I add a new user - it works for the new user. 
So I think it must be some configuration file within my personal folder. Still I don't understand: 

Which ones are the relevant configuration files for 
- systemsettings - advanced - k3b 
- systemsettings - advanced - policykit 


plz help, 
thx, 
piedro

---

### Post by Zorael on 2009-12-09
I'd try #kubuntu-devel on irc.freenode.net; perhaps they can make sense of it.

---

### Post by piedro on 2010-06-04
A few configuration files left over from prerelease versions have been the problem, new install (well, just a new user account actually) solved it. 

thx for reading, 
piedro

---

