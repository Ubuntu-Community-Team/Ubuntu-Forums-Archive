---
title: "Amarok 2 doesnt work.  It loads the program, but nothing works."
date: 2009-06-09
forum: General Help
---

### Post by Mashuteichou on 2009-06-09
Ever since the 9.04 update, Amarok hasn't been working.  And if I remember correctly, this version of Amarok just came out too.  

When I open a file with Amarok, it loads the program and the interface pops up, but nothing place.  Dragging and dropping, double click, open with, etc., doesn't work.  

When I open Amarok from the menu, it says the HDA playback doesn't work and it falls back to pulse audio.  Not sure what that means.  

I cannot add to the playlist, but there is one song that loads each time from my collection which is a random song from Benny Benassi.  I can't play that either.  

Anyone have a suggestion?

---

### Post by Mashuteichou on 2009-06-09
Oh, and if this has any correlation to the problem, VLC is acting weird too.  No matter how much its opened, it takes about 30 seconds for it to start, no matter what.  If I double click something, it opens it in 2 VLCs, yet I have the run in one only option on.  So, once its loaded, it loads over whatever is playing.

---

### Post by RedSingularity on 2009-06-09
Run the programs in Terminal and post the output.

---

### Post by Yellow Pasque on 2009-06-09
Try opening these apps from the terminal and see if they give any additional info.

---

### Post by Mashuteichou on 2009-06-10
amarok
amarok(18953) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
amarok(18953) KToolInvocation::klauncher: klauncher not running... launching kdeinit
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher
kdeinit4: preparing to launch /usr/bin/kded4
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
kbuildsycoca4(18981) KBuildSycoca::checkDirTimestamps: timestamp changed: "/etc/xdg/menus/applications-merged"
"KConfigIni: In file /usr/share/applications/wine-browsedrive.desktop, line 2: " "Invalid escape sequence "\ "." 
"KConfigIni: In file /usr/share/applications/wine-browsedrive.desktop, line 8: " "Invalid escape sequence "\ "." 
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update
kded(18980) KDEDModule::setModuleName: registerObject() successful for  "kdedglobalaccel"
Object::connect: No such slot MainWindow::showStatistics() in /build/buildd/amarok-2.0.2mysql5.1.30/amarok-2.0.2/src/MainWindow.cpp:692
Object::connect:  (receiver name: 'MainWindow')
QLayout: Attempting to add QLayout "" to MainWindow "MainWindow", which already has a layout
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
amarok(18953) Plasma::Applet::save: saving to "1"
amarok(18953) Context::ContextView::setContainment: "" Line:  599
amarok(18953) Plasma::ThemePrivate::config: using theme for app "amarok"
amarok(18953) Plasma::Applet::save: saving to "2"
amarok(18953) Plasma::Applet::save: saving to "3"
amarok(18953) Plasma::Applet::save: saving to "4"
amarok(18953) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(18953) Context::ColumnContainment::insertInGrid: "" Line:  603
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
Object::connect: No such slot FileBrowser::Widget::setDir( const QString& ) in /build/buildd/amarok-2.0.2mysql5.1.30/amarok-2.0.2/src/browsers/filebrowser/FileBrowser.cpp:112
Object::connect:  (sender name:   'KBookmarkHandler')
Object::connect:  (receiver name: 'FileBrowser::Widget')
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
amarok(18953) MagnatuneConfig::load: load
kdeinit4: preparing to launch 
kdeinit4: preparing to launch 
amarok(18953) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(18953) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(18953) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
phantom@phantom-laptop:~$ X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x4200064
amarok(18953) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
kded(18980) KDEDModule::setModuleName: registerObject() successful for  "ktimezoned"
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
amarok(18953) Context::ContextView::clear: "" Line:  165
amarok(18953) Context::ContextView::clear: "" Line:  165
amarok(18953) Context::ContextView::clear: "" Line:  165
amarok(18953) Context::ContextView::clear: "" Line:  165

---

### Post by RedSingularity on 2009-06-10
Have you tried reinstalling Amarok?

---

### Post by Mashuteichou on 2009-06-11
Yeah, I tried that originally when it started acting weird.  Now it just doesn't work at all.

---

### Post by CatKiller on 2009-06-11
You could try installing phonon-backend-xine, and if that doesn't work you could try renaming ~/.kde/share/apps/amarok to amarok.backup to remove your user configuration and create a new one from the defaults.

---

### Post by RedSingularity on 2009-06-11
Did you try deleting the .amarok folder in your /home directory and then try starting the program?

---

### Post by nadeepa on 2009-06-13
See following thread..it solved my problem.

[http://georgia.ubuntuforums.org/showthread.php?p=7449872#post7449872](http://georgia.ubuntuforums.org/showthread.php?p=7449872#post7449872)

---

