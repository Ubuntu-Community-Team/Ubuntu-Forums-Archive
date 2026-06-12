---
title: "Amarok 2.02 Ubuntu 9.04rc"
date: 2009-04-20
forum: General Help
---

### Post by favadi on 2009-04-20
It's terrible, so many problem when upgrade to 9.04. 
I install Amarok, but I can't play music. The time bar doesn't move and it has no sound.
Help me, plz!

---

### Post by collinp on 2009-04-20
Well, we need more details other than "it dosent work". Try running amarok in Terminal, then pasting the output here (remember CODE tags).

---

### Post by favadi on 2009-04-20
> **Hellow said:**
> Well, we need more details other than "it dosent work". Try running amarok in Terminal, then pasting the output here (remember CODE tags).

Thanks. It's here.
> favadi@favadi-desktop:~$ amarok
amarok(4545) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
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
amarok(4545) Plasma::Applet::save: saving to "1"
amarok(4545) Context::ContextView::setContainment: "" Line:  599
amarok(4545) Plasma::ThemePrivate::config: using theme for app "amarok"
amarok(4545) Plasma::Applet::save: saving to "2"
amarok(4545) Plasma::Applet::save: saving to "3"
amarok(4545) Plasma::Applet::save: saving to "4"
amarok(4545) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(4545) Context::ColumnContainment::insertInGrid: "" Line:  603
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
amarok(4545) MagnatuneConfig::load: load
favadi@favadi-desktop:~$ amarok(4545) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(4545) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(4545) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x2c00064
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
QPainter::begin: Cannot paint on a null pixmap
amarok(4545) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated


---

### Post by ayllu on 2009-04-20
install phonon-backend-xine, and will work

---

### Post by favadi on 2009-04-20
> **ayllu said:**
> install phonon-backend-xine, and will work

I've tried it. But it's still not work. :(

---

### Post by favadi on 2009-04-21
Need help!!!!

---

### Post by favadi on 2009-04-21
So strange, when I choose a mp3 file and click open with amarok, it play normaly.

---

### Post by Old Old Duffers on 2009-04-21
Very same problems with 2.2 Amarok....when I upgraded to 9.01

---

### Post by geekity2 on 2009-04-24
Just had the same problem, went through the steps here and got same results. Just reloading the current playlist (as in clear it and then select it again) seemed to fix it. Sorry if I completely missed the boat on this problem :)

---

### Post by Wim De Winter on 2009-04-24
> **ayllu said:**
> install phonon-backend-xine, and will work

worked for me! THANKS!!

---

### Post by Crank-N-Jam on 2009-04-25
> **ayllu said:**
> install phonon-backend-xine, and will work

That worked for me as well.  Thanks!!

Jason

---

### Post by visionaire on 2009-04-26
Well i told u what i did to work my mp3, first i read that installing phonon-backend-xine will do it, it was already installed, so not the problem

Then i read that i have to install ubuntu-restricted-extras, installed, but still doesn't work

then i look that is an kubuntu-restricted-extras, so since amarok is kde, i said WTH, and download it, and now IT WORKS!!!

maybe luck or maybe the actual solution for those who can't use amarok 2.02 in jaunty yet

sudo aptitude install kubuntu-restricted-extras will do it probably

PD: I use Ubuntu, not Kubuntu

Cheers from Asuncion, Paraguay

---

### Post by Dug. on 2009-04-26
Thank you visionaire.  Neither phonon-backend-xine nor ubuntu restricted extras worked for me, but installing kubuntu restricted extras via applications > add/remove did.

---

### Post by jeroach on 2009-04-26
And it worked for me too. Thank you!

---

### Post by favadi on 2009-04-29
Back to Amarok 14. :(

---

### Post by Nidding on 2009-04-29
> **Crank-N-Jam said:**
> That worked for me as well.  Thanks!!

Jason

Anf for me as well :)

---

### Post by tatapcku on 2009-07-15
If for some reason you don't want to install java6 package (which comes as part of kubuntu resricted package), install all mp3\mpeg related stuff listed in the following link: [http://packages.ubunut.com/intrepid/kubuntu-restricted-extras](http://packages.ubunut.com/intrepid/kubuntu-restricted-extras)

worked for me :)

---

