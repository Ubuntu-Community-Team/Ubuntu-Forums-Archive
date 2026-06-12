---
title: "kopete crashing"
date: 2006-05-16
forum: Desktop Environments
---

### Post by Zaventh on 2006-05-16
Kubuntu Breezy
KDE 3.5.2

Any time I try to "Configure" Kopete, via right click on the sys tray icon or from the main window, kopete crashes. I've reinstalled it and deleted the app configs in ~/.kde but still it persists. What else can I try?

Here's a backtrace...

```

[KCrash handler]
#6  0xb5b5ecc8 in Kopete::AV::VideoDevice::getBrightness ()
   from /usr/lib/libkopete_videodevice.so.0
#7  0xb5b63ec6 in Kopete::AV::VideoDevicePool::getBrightness ()
   from /usr/lib/libkopete_videodevice.so.0
#8  0xb5b4c8a8 in AVDeviceConfig::setVideoInputParameters ()
   from /usr/lib/kde3/kcm_kopete_avdeviceconfig.so
#9  0xb5b4f259 in AVDeviceConfig::AVDeviceConfig ()
   from /usr/lib/kde3/kcm_kopete_avdeviceconfig.so
#10 0xb5b5154e in KGenericFactory<AVDeviceConfig, QWidget>::createObject ()
   from /usr/lib/kde3/kcm_kopete_avdeviceconfig.so
#11 0xb6fc79ce in KLibFactory::create () from /usr/lib/libkdecore.so.4
#12 0xb7781d5d in KCModuleLoader::load () from /usr/lib/libkutils.so.1
#13 0xb7782522 in KCModuleLoader::loadModule () from /usr/lib/libkutils.so.1
#14 0xb7782c84 in KCModuleProxy::realModule () from /usr/lib/libkutils.so.1
#15 0xb7783aad in KCModuleProxy::buttons () from /usr/lib/libkutils.so.1
#16 0xb7783b3e in KCMultiDialog::slotAboutToShow ()
   from /usr/lib/libkutils.so.1
#17 0xb7783d23 in KCMultiDialog::qt_invoke () from /usr/lib/libkutils.so.1
#18 0xb6988929 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#19 0xb72b7c2d in KDialogBase::aboutToShowPage () from /usr/lib/libkdeui.so.4
#20 0xb7785ad3 in KCMultiDialog::addModule () from /usr/lib/libkutils.so.1
#21 0xb7798431 in KSettings::PageNode::addToDialog ()
   from /usr/lib/libkutils.so.1
#22 0xb7798302 in KSettings::PageNode::addToDialog ()
   from /usr/lib/libkutils.so.1
#23 0xb7793b36 in KSettings::Dialog::createDialogFromServices ()
   from /usr/lib/libkutils.so.1
#24 0xb7793d19 in KSettings::Dialog::show () from /usr/lib/libkutils.so.1
#25 0xb7e8ba2c in KopetePreferencesAction::slotShowPreferences ()
   from /usr/lib/libkopete.so.1
#26 0xb7e8fd4e in KopetePreferencesAction::qt_invoke ()
   from /usr/lib/libkopete.so.1
#27 0xb6988929 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#28 0xb69893c4 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#29 0xb727ba26 in KAction::activated () from /usr/lib/libkdeui.so.4
#30 0xb72b222b in KAction::slotActivated () from /usr/lib/libkdeui.so.4
#31 0xb72cdf4b in KAction::slotPopupActivated () from /usr/lib/libkdeui.so.4
#32 0xb72ce282 in KAction::qt_invoke () from /usr/lib/libkdeui.so.4
#33 0xb7e8fd6c in KopetePreferencesAction::qt_invoke ()
   from /usr/lib/libkopete.so.1
#34 0xb6988929 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#35 0xb6ce7e92 in QSignal::signal () from /usr/lib/libqt-mt.so.3
#36 0xb69a6344 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#37 0xb6aab963 in QPopupMenu::mouseReleaseEvent () from /usr/lib/libqt-mt.so.3
#38 0xb7287e80 in KPopupMenu::mouseReleaseEvent () from /usr/lib/libkdeui.so.4
#39 0xb69c3356 in QWidget::event () from /usr/lib/libqt-mt.so.3
#40 0xb691ff80 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#41 0xb6920500 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#42 0xb706c17c in KApplication::notify () from /usr/lib/libkdecore.so.4
#43 0xb68b0e25 in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#44 0xb68ac072 in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#45 0xb68aa66f in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#46 0xb68c3fff in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#47 0xb6937cfb in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#48 0xb6937c1e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#49 0xb691ec13 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#50 0x0807848e in ?? ()
#51 0xbfd282c0 in ?? ()
#52 0xbfd283f4 in ?? ()
#53 0xbfd28408 in ?? ()
#54 0x0807846e in ?? ()
#55 0x0000000f in ?? ()
#56 0x03df6174 in ?? ()
#57 0xbfd28358 in ?? ()
#58 0xb7f1e2c8 in _dl_rtld_di_serinfo () from /lib/ld-linux.so.2
#59 0xb6096ec2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#60 0x0806d2d1 in ?? ()
```

---

### Post by GeneralZod on 2006-05-16
Do you have a webcam?

---

### Post by Zaventh on 2006-05-16
Nope. Have never even connected one to this machine before.

---

### Post by silentb on 2006-05-16
The crash is caused by the audio/video configuration plugin.
These commands might help:

sudo mv /usr/lib/kde3/kcm_kopete_avdeviceconfig.so /usr/lib/kde3/kcm_kopete_avdeviceconfig.so.bak
sudo mv /usr/lib/kde3/kcm_kopete_avdeviceconfig.la /usr/lib/kde3/kcm_kopete_avdeviceconfig.la.bak

---

### Post by GeneralZod on 2006-05-16
This is a very silly bug where the Audio/ Visual configuration tab (which was *highly* experimental at the time of Breezy's release) is the first tab you see when you click Configure.  The version here in Dapper is much more sane.  Hopefully silentb's workaround will fix things for you in the meantime :)

---

### Post by Zaventh on 2006-05-16
Yep silentb that worked, but of course disabled the webcam or whatnot features. I can live without it though! Thanks.

---

### Post by vidak on 2006-05-16
I had the same problem with kopete, I downloaded the last version of the program, compiled it, and works out of box...

---

