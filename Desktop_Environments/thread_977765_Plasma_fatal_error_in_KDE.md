---
title: "Plasma fatal error in KDE"
date: 2008-11-10
forum: Desktop Environments
---

### Post by NNG on 2008-11-10
I recently decided to install KDE on Ubuntu. At first it worked great. However, everytime I log into KDE, plasma gets a fatal error and doesn't start.I already tried reinstalling KDE but didn't have any luck.

Here's the error details.
```
Application: Plasma Workspace (plasma), signal SIGSEGV
(no debugging symbols found)

[Thread debugging using libthread_db enabled]
[New Thread 0xb47326e0 (LWP 9051)]
[New Thread 0xb2a67b90 (LWP 9052)]

[KCrash handler]
#6  0xb715e394 in QGraphicsLinearLayout::setSpacing ()
   from /usr/lib/libQtGui.so.4
#7  0xb2a96368 in ?? () from /usr/lib/kde4/plasma_applet_notes.so
#8  0xb2a96410 in ?? () from /usr/lib/kde4/plasma_applet_notes.so
#9  0xb7d07585 in Plasma::Applet::flushPendingConstraintsEvents ()
   from /usr/lib/libplasma.so.2
#10 0xb7d07bc6 in Plasma::Applet::timerEvent () from /usr/lib/libplasma.so.2
#11 0xb762853f in QObject::event () from /usr/lib/libQtCore.so.4
#12 0xb71613c7 in QGraphicsWidget::event () from /usr/lib/libQtGui.so.4
#13 0xb6ba18ec in QApplicationPrivate::notify_helper ()
   from /usr/lib/libQtGui.so.4
#14 0xb6ba976e in QApplication::notify () from /usr/lib/libQtGui.so.4
#15 0xb7ae772d in KApplication::notify () from /usr/lib/libkdeui.so.5
#16 0xb7618e61 in QCoreApplication::notifyInternal ()
   from /usr/lib/libQtCore.so.4
#17 0xb7646d81 in ?? () from /usr/lib/libQtCore.so.4
#18 0xb7643520 in ?? () from /usr/lib/libQtCore.so.4
#19 0xb59256f8 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#20 0xb5928da3 in ?? () from /usr/lib/libglib-2.0.so.0
#21 0xb5928f61 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#22 0xb7643478 in QEventDispatcherGlib::processEvents ()
   from /usr/lib/libQtCore.so.4
#23 0xb6c3bee5 in ?? () from /usr/lib/libQtGui.so.4
#24 0xb761752a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#25 0xb76176ea in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#26 0xb6856cab in KIO::NetAccess::enter_loop () from /usr/lib/libkio.so.5
#27 0xb6856eac in KIO::NetAccess::statInternal () from /usr/lib/libkio.so.5
#28 0xb6857cbb in KIO::NetAccess::stat () from /usr/lib/libkio.so.5
#29 0xb6857d3b in KIO::NetAccess::mostLocalUrl () from /usr/lib/libkio.so.5
#30 0xb2b86f1e in ?? () from /usr/lib/kde4/plasma_applet_icon.so
#31 0xb2b876ff in ?? () from /usr/lib/kde4/plasma_applet_icon.so
#32 0xb7d37737 in Plasma::Corona::loadLayout () from /usr/lib/libplasma.so.2
#33 0xb7d38531 in Plasma::Corona::initializeLayout ()
   from /usr/lib/libplasma.so.2
#34 0xb7f9d199 in ?? () from /usr/lib/libkdeinit4_plasma.so
#35 0xb7f9e880 in ?? () from /usr/lib/libkdeinit4_plasma.so
#36 0xb7fa0a81 in ?? () from /usr/lib/libkdeinit4_plasma.so
#37 0xb7f9243a in kdemain () from /usr/lib/libkdeinit4_plasma.so
#38 0x080485b2 in _start ()
#0  0xb7fde430 in __kernel_vsyscall ()

```

When I try to restart plasma:
```
will@will-laptop:~$ plasma
<unknown program name>(9257)/ checkComposite: Plasma has an argb visual 0x93cbec8 60817409                                                                
<unknown program name>(9257)/ checkComposite: Plasma can use COMPOSITE for effects on 0x93c3fa8                                                           
QLayout: Attempting to add QLayout "" to Plasma::Dialog "", which already has a layout                                                                    
plasma(9258) NowPlaying::init: Preferred width is 46                         
plasma(9258) NowPlaying::findPlayer: Looking for players.  Possibilities: () 
Plasma crashed, attempting to automatically recover                          
plasma(9257): Communication problem with  "plasma" , it probably crashed.    
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" "                                 

                    KCrash: Application 'plasma' crashing...
sock_file=/home/will/.kde/socket-will-laptop/kdeinit4__0                     
will@will-laptop:~$ <unknown program name>(9261)/ checkComposite: Plasma has an argb visual 0x8192ec8 62914561                                            
<unknown program name>(9261)/ checkComposite: Plasma can use COMPOSITE for effects on 0x818afa8                                                           
QLayout: Attempting to add QLayout "" to Plasma::Dialog "", which already has a layout
will@will-laptop:~$ plasma(9263) NowPlaying::init: Preferred width is 46
plasma(9263) NowPlaying::findPlayer: Looking for players.  Possibilities: ()
plasma(9261): Communication problem with  "plasma" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" "
```

I'm not very experienced with Linux yet so I don't really know what to do to fix it other than trying to reinstall it.

---

### Post by benerivo on 2008-11-10
I might be a kde4/plasma setting in your home folder that it tries to load, but then crashes on. You could rename your ~/.kde folder in then try to log in. It will load the kde defaults rather than any settings you may have made to kde or kde programs```
mv .kde .kdebackup
```This line in a terminal will rename your kde settings folder to kdebackup.

---

### Post by aged hippy on 2008-11-10
Hi. :)

Have you up-dated everything via Adept or Synaptic?

---

### Post by benerivo on 2008-11-10
You could also try a quick reinstall of plasma with```
sudo apt-get update && sudo apt-get --reinstall install kdebase-plasma
```

---

### Post by kernelhaxor on 2008-11-10
what all widgets do you have?  One of the widgets might be causing it too (One of my widgets used to crash Plasma though not at start up)
You can try uninstalling each widget and check if Plasma still crashes

---

### Post by NNG on 2008-11-12
> **benerivo said:**
> I might be a kde4/plasma setting in your home folder that it tries to load, but then crashes on. You could rename your ~/.kde folder in then try to log in. It will load the kde defaults rather than any settings you may have made to kde or kde programs```
mv .kde .kdebackup
```This line in a terminal will rename your kde settings folder to kdebackup. 
This worked eventually. The first time I tried it, it didn't work but then I updated and did the other things that were mentioned on this threat and it worked the second time.

Thanks.

---

### Post by webmonster on 2008-11-30
Try deleting or renaming ~/.kde/share/config/plasma-appletsrc

---

### Post by logan85 on 2010-07-12
Hi, I have ubuntu 9.10 and i installed the kde-desktop, to experience, but after logging in, i got on error message, that plasma is crashed, and i have just a black screen. 
(I can launch programs with alt+f2)

Here is the error message:

Application: Plasma Workspace (kdeinit4), signal: Segmentation fault
[KCrash Handler]
#5  0x00007f8ad4d79de7 in Plasma::Wallpaper::setUsingRenderingCache(bool) () from /usr/lib/libplasma.so.3
#6  0x00007f8ac0f42e07 in ?? () from /usr/lib/kde4/plasma_wallpaper_image.so
#7  0x00007f8ad4d79c7d in Plasma::Wallpaper::restore(KConfigGroup const&) () from /usr/lib/libplasma.so.3
#8  0x00007f8ad4cb26e3 in Plasma::Applet::paint(QPainter*, QStyleOptionGraphicsItem const*, QWidget*) () from /usr/lib/libplasma.so.3
#9  0x00007f8adb82f9da in ?? () from /usr/lib/libQtGui.so.4
#10 0x00007f8adb8426e4 in ?? () from /usr/lib/libQtGui.so.4
#11 0x00007f8adb8447c5 in ?? () from /usr/lib/libQtGui.so.4
#12 0x00007f8adb845422 in ?? () from /usr/lib/libQtGui.so.4
#13 0x00007f8adb845dc4 in ?? () from /usr/lib/libQtGui.so.4
#14 0x00007f8adb8651c5 in QGraphicsView::paintEvent(QPaintEvent*) () from /usr/lib/libQtGui.so.4
#15 0x00007f8adb27a0e2 in QWidget::event(QEvent*) () from /usr/lib/libQtGui.so.4
#16 0x00007f8adb6208b6 in QFrame::event(QEvent*) () from /usr/lib/libQtGui.so.4
#17 0x00007f8adb86053b in QGraphicsView::viewportEvent(QEvent*) () from /usr/lib/libQtGui.so.4
#18 0x00007f8adc085227 in QCoreApplicationPrivate::sendThroughObjectEventFilters(QObject*, QEvent*) () from /usr/lib/libQtCore.so.4
#19 0x00007f8adb2240fc in QApplicationPrivate::notify_helper(QObject*, QEvent*) () from /usr/lib/libQtGui.so.4
#20 0x00007f8adb22a71b in QApplication::notify(QObject*, QEvent*) () from /usr/lib/libQtGui.so.4
#21 0x00007f8adc5ce076 in KApplication::notify(QObject*, QEvent*) () from /usr/lib/libkdeui.so.5
#22 0x00007f8adc085e0c in QCoreApplication::notifyInternal(QObject*, QEvent*) () from /usr/lib/libQtCore.so.4
#23 0x00007f8adb28275d in QWidgetPrivate::drawWidget(QPaintDevice*, QRegion const&, QPoint const&, int, QPainter*, QWidgetBackingStore*) () from /usr/lib/libQtGui.so.4
#24 0x00007f8adb2833f8 in QWidgetPrivate::paintSiblingsRecursive(QPaintDevice*, QList<QObject*> const&, int, QRegion const&, QPoint const&, int, QPainter*, QWidgetBackingStore*) ()
   from /usr/lib/libQtGui.so.4
#25 0x00007f8adb2824ba in QWidgetPrivate::drawWidget(QPaintDevice*, QRegion const&, QPoint const&, int, QPainter*, QWidgetBackingStore*) () from /usr/lib/libQtGui.so.4
#26 0x00007f8adb43bbf5 in ?? () from /usr/lib/libQtGui.so.4
#27 0x00007f8adb43bf49 in ?? () from /usr/lib/libQtGui.so.4
#28 0x00007f8adb29d35a in ?? () from /usr/lib/libQtGui.so.4
#29 0x00007f8adb2a8c3b in QApplication::x11ProcessEvent(_XEvent*) () from /usr/lib/libQtGui.so.4
#30 0x00007f8adb2d4322 in ?? () from /usr/lib/libQtGui.so.4
#31 0x00007f8ad749abce in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#32 0x00007f8ad749e598 in ?? () from /lib/libglib-2.0.so.0
#33 0x00007f8ad749e6c0 in g_main_context_iteration () from /lib/libglib-2.0.so.0
#34 0x00007f8adc0af333 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#35 0x00007f8adb2d3f0e in ?? () from /usr/lib/libQtGui.so.4
#36 0x00007f8adc084732 in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#37 0x00007f8adc084b0c in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#38 0x00007f8adc08884b in QCoreApplication::exec() () from /usr/lib/libQtCore.so.4
#39 0x00007f8ad18754cf in kdemain () from /usr/lib/libkdeinit4_plasma-desktop.so
#40 0x0000000000406fb8 in _start ()


I tried everything described here, i even reinstalled the kde-desktop, but it's not working. 
Anticipated thanks for help.

---

