---
title: "KDE 4.2 messed almost everything up"
date: 2009-02-22
forum: Desktop Environments
---

### Post by spacegypsy on 2009-02-22
After today's update of Kubuntu 8.10, not only it changed desktop and widgets won't work anymore but I could not move or close any open application, my keyboard is also not working anymore (only in the login window and firefox it works) also I could not write anything in the terminal window anymore.................:(:(:(:(:(

How could I possibly fix it?

should I go back to KDE 4.1?

And how can I do this without terminal?

---

### Post by myrddinemrys on 2009-02-23
A similar thing happened to me with this update. I've got mine back running fine, but some are still working on it in [this thread]("http://ubuntuforums.org/showthread.php?t=1076702").  Apparently the KDE 4.2 update removed some packages it was supposed to update.

Can you do a CTRL-ALT-F1 to get a terminal?  It also sounds like you lost your window decorations.  

If your update stopped with an error partway thru, be sure to do a ```
sudo apt-get -f install
```to finish it up (if you can type anything).

Also do as many 'sudo aptitude update && sudo aptitude safe-upgrade' as it takes to install all pending updates.

If your keyboard is totally not working though, you may have to go to Applications | System | Adept Manager, and sift thru the packages there to install whatever KDE 4.2 packages may be missing.

I'd especially check for missing 'libkdecorations4' and 'kdeplasma-addons' packages in your case.

Also, there is the virtual keyboard, 'kbkvd' (under Applications | Utilities) you might want to try.

If you can get a working terminal & keyboard, head over to the above listed thread for info on how to figure out what other KDE 4.2 packages are still missing.

---

### Post by myrddinemrys on 2009-02-23
As a test, I upgraded another machine to 4.2 and ended up in the exact situation as you: no window decorations, no keyboard, no widgets, etc.  I got it all working though, by doing the following:


Type CTRL-ALT-F1 (log in)

then type the following lines in order:```
sudo aptitude update
sudo aptitude dist-upgrade
  (it will ask you if its solution is OK) -- type 'Y'
sudo shutdown -r 0
```
The last command reboots your machine.

After the reboot, all was peachy and in KDE 4.2.

Hope this works as well for you.

---

### Post by spacegypsy on 2009-02-23
> **myrddinemrys said:**
> As a test, I upgraded another machine to 4.2 and ended up in the exact situation as you: no window decorations, no keyboard, no widgets, etc.  I got it all working though, by doing the following:


Type CTRL-ALT-F1 (log in)

then type the following lines in order:```
sudo aptitude update
sudo aptitude dist-upgrade
  (it will ask you if its solution is OK) -- type 'Y'
sudo shutdown -r 0
```
The last command reboots your machine.

After the reboot, all was peachy and in KDE 4.2.

Hope this works as well for you.

Thanks myrddinemrys, but it's a no go for me.

After doing the update as you told, I restarted my machine, logged in and then it stopped at the third icon (the blue globe) when KDE 4 is loading.

After a while a got this message; "The following installation problem was detected while trying to start KDE: No write access to '/home/spacegypsy/.ICEauthority
KDE unable to start."

---

### Post by lykwydchykyn on 2009-02-23
Check freespace on your hard drive; go to a VT and type in:
```

df -h

```

Chances are you may have a partition full from the big download.  If so, just "apt-get clean" should fix.

If that's not it, try removing ~/.ICEauthority (KDE recreates it on login, it doesn't store any meaningful data).

---

### Post by spacegypsy on 2009-02-23
Kubuntu is on the sda3 patition, looks like I got stille place enough.
[ATTACH]104431[/ATTACH]

I'll try to remove the file

Ctrl-Alt-F1 at login

```
sudo rm /home/spacegypsy/.ICEauthority
```

if I'm wright?

---

### Post by lykwydchykyn on 2009-02-23
Yep, that's it.

---

### Post by spacegypsy on 2009-02-23
Ok, I managed to log in.

But the problems still persist, no window decorations, no keyboard, no widgets, etc.

---

### Post by lykwydchykyn on 2009-02-23
Were you using kwin as the window manager in 4.1, or something else like compiz?

You might try renaming the .kde folder to .kde-old to default your settings.  Don't delete it.  Or you could try to create a new user account just to test if it's a setting in your config that's messing it up.

If you can, post the contents of ~/.xsession-errors too.

---

### Post by spacegypsy on 2009-02-25
Indeed compiz is installed.

I'll try your solutions later (probably in the weekend).

Lack of time for the moment :neutral:

---

### Post by spacegypsy on 2009-03-01
> **lykwydchykyn said:**
> Were you using kwin as the window manager in 4.1, or something else like compiz?

You might try renaming the .kde folder to .kde-old to default your settings.  Don't delete it.  Or you could try to create a new user account just to test if it's a setting in your config that's messing it up.

If you can, post the contents of ~/.xsession-errors too.

Wher do I find the .KDE folder?

Also ~/.xsession-errors seems not to exist.
Is it possible?

---

### Post by spacegypsy on 2009-03-01
Found the .kde folder, and renamed it like you said to .kde-old

---

### Post by spacegypsy on 2009-03-01
content of the .xsession-errors file:
```

Xsession: X session started for spacegypsy at Sun Mar  1 21:36:20 CET 2009
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
kdostartupconfig4(6391) main: Running kdostartupconfig.
startkde: Starting up...
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher
kdeinit4: preparing to launch /usr/bin/kded4
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update
kded(6416) Solid::Control::ManagerBasePrivate::loadBackend: Backend loaded:  "HAL-Power"
kded(6416) XSyncBasedPoller::XSyncBasedPoller: 3 0
kded(6416) XSyncBasedPoller::XSyncBasedPoller: XSync seems available and ready
kded(6416) XSyncBasedPoller::setUpPoller: XSync Inited
kded(6416) XSyncBasedPoller::setUpPoller: Supported, init completed
kded(6416) PowerDevilDaemon::profileFirstLoad: Profile initialization
kded(6416) PowerDevilDaemon::poll: Polling started, idle time is 4 seconds
kded(6416) PowerDevilDaemon::poll: Stopping timer
X Error: XSyncBadAlarm 129
  Extension:    131 (Uknown extension)
  Minor opcode: 11 (Unknown request)
  Resource id:  0x0
kded(6416) PowerDevilDaemon::poll: Polling started, idle time is 4 seconds
kded(6416) PowerDevilDaemon::poll: Stopping timer
kded(6416) KDEDModule::setModuleName: registerObject() successful for  "powerdevil"
X Error: XSyncBadAlarm 129
  Extension:    131 (Uknown extension)
  Minor opcode: 11 (Unknown request)
  Resource id:  0x0
kdeinit4: preparing to launch /usr/bin/kcminit_startup
kdeinit4: preparing to launch /usr/bin/ksmserver
<unknown program name>(6413)/ KStartupInfo::createNewStartupId: creating:  "spacegypsy-desktop;1235939784;991242;6413_TIME0" : "unnamed app"
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update
kdeinit4: preparing to launch /usr/bin/plasma
<unknown program name>(6471)/ checkComposite: Plasma has an argb visual 0x1550190 20971521
<unknown program name>(6471)/ checkComposite: Plasma is COMPOSITE-less on 0x15490f0
kephald starting up 
XRANDR error base:  171 
RRInput mask is set!! 
RandRScreen::loadSettings - adding mode:  63 1680 x 1050 
RandRScreen::loadSettings - adding mode:  64 1680 x 1050 
RandRScreen::loadSettings - adding mode:  65 1600 x 1024 
RandRScreen::loadSettings - adding mode:  66 1400 x 1050 
RandRScreen::loadSettings - adding mode:  67 1400 x 1050 
RandRScreen::loadSettings - adding mode:  68 1400 x 1050 
RandRScreen::loadSettings - adding mode:  69 1280 x 1024 
RandRScreen::loadSettings - adding mode:  70 1280 x 1024 
RandRScreen::loadSettings - adding mode:  71 1280 x 1024 
RandRScreen::loadSettings - adding mode:  72 1440 x 900 
RandRScreen::loadSettings - adding mode:  73 1280 x 960 
RandRScreen::loadSettings - adding mode:  74 1152 x 864 
RandRScreen::loadSettings - adding mode:  75 1152 x 864 
RandRScreen::loadSettings - adding mode:  76 1152 x 864 
RandRScreen::loadSettings - adding mode:  77 1024 x 768 
RandRScreen::loadSettings - adding mode:  78 1024 x 768 
RandRScreen::loadSettings - adding mode:  79 1024 x 768 
RandRScreen::loadSettings - adding mode:  80 1024 x 768 
RandRScreen::loadSettings - adding mode:  81 896 x 672 
RandRScreen::loadSettings - adding mode:  82 960 x 600 
RandRScreen::loadSettings - adding mode:  83 960 x 540 
RandRScreen::loadSettings - adding mode:  84 800 x 600 
RandRScreen::loadSettings - adding mode:  85 800 x 600 
RandRScreen::loadSettings - adding mode:  86 800 x 600 
RandRScreen::loadSettings - adding mode:  87 800 x 600 
RandRScreen::loadSettings - adding mode:  88 840 x 525 
RandRScreen::loadSettings - adding mode:  89 840 x 525 
RandRScreen::loadSettings - adding mode:  90 840 x 525 
RandRScreen::loadSettings - adding mode:  91 840 x 525 
RandRScreen::loadSettings - adding mode:  92 800 x 512 
RandRScreen::loadSettings - adding mode:  93 700 x 525 
RandRScreen::loadSettings - adding mode:  94 700 x 525 
RandRScreen::loadSettings - adding mode:  95 700 x 525 
RandRScreen::loadSettings - adding mode:  96 640 x 512 
RandRScreen::loadSettings - adding mode:  97 640 x 512 
RandRScreen::loadSettings - adding mode:  98 640 x 480 
RandRScreen::loadSettings - adding mode:  99 640 x 480 
RandRScreen::loadSettings - adding mode:  100 640 x 480 
RandRScreen::loadSettings - adding mode:  101 720 x 400 
RandRScreen::loadSettings - adding mode:  102 576 x 432 
RandRScreen::loadSettings - adding mode:  103 576 x 432 
RandRScreen::loadSettings - adding mode:  104 576 x 432 
RandRScreen::loadSettings - adding mode:  105 512 x 384 
RandRScreen::loadSettings - adding mode:  106 512 x 384 
RandRScreen::loadSettings - adding crtc:  57 
RandRScreen::loadSettings - adding crtc:  58 
RandRScreen::loadSettings - adding output:  59 
Setting CRTC 0 on output "VGA1" (previous 0 ) 
RandRScreen::loadSettings - adding output:  60 
Setting CRTC 57 on output "DVI0" (previous 0 ) 
CRTC outputs: (60) 
Output name: "DVI0" 
Output refresh rate: 59.9543 
Output rect: QRect(0,0 1680x1050) 
Output rotation: 1 
RandRScreen::loadSettings - adding output:  61 
Setting CRTC 0 on output "VGA2" (previous 0 ) 
RandRScreen::loadSettings - adding output:  62 
Setting CRTC 0 on output "DVI1" (previous 0 ) 
XRandROutputs::init 
  added output  59 
got a valid edid block... 
vendor code: "MED" 
product id: 34551 
serial number: 16843009 
  added output  60 
  added output  61 
  added output  62 
output: "DVI0" QRect(0,0 1680x1050) 0 false false 
output: "DVI1" QRect(0,0 0x0) 0 false false 
output: "VGA1" QRect(0,0 0x0) 0 false false 
output: "VGA2" QRect(0,0 0x0) 0 false false 
load xml 
connected: 1 
looking for current "DVI0" 
known "*" has score: 0.125 
screen: 0 QRect(0,0 1680x1050) 
looking for a matching configuration... 
connected: 1 
looking for current "DVI0" 
known "*" has score: 0.125 
found outputs, known: false 
connected: 1 
looking for current "DVI0" 
known "*" has score: 0.125 
activate external configuration!! 
registered the service: true 
screens registered on the bus: true 
outputs registered on the bus: true 
configurations registered on the bus: true 
kded(6416) KDEDModule::setModuleName: Registration of kded module  "kded_kephal" without dbus interface.
kded(6416) KDEDModule::setModuleName: registerObject() successful for  "kded_kephal"
kded(6416) KDEDModule::setModuleName: registerObject() successful for  "kdedglobalaccel"
QLayout: Attempting to add QLayout "" to QWidget "", which already has a layout
plasma(6472) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: /home/spacegypsy/.kde/share/apps/RecentDocuments/chien.desktop not found"
plasma(6472) Solid::Control::ManagerBasePrivate::loadBackend: Backend loaded:  "HAL-Power"
Object::connect: Attempt to bind non-signal TaskManager::TaskGroup::editRequest()
QCoreApplication::postEvent: Unexpected null receiver
kded(6416) KDEDModule::setModuleName: registerObject() successful for  "ktimezoned"
kded(6416) Solid::Control::ManagerBasePrivate::loadBackend: Backend loaded:  "NetworkManager 0.7"
kded(6416) KDEDModule::setModuleName: registerObject() successful for  "networkstatus"
QGraphicsLayout::addChildLayout: layout already has a parent
QGraphicsLayout::addChildLayout: layout already has a parent
kdeinit4: preparing to launch 
kdeinit4: preparing to launch 
QPainter::begin: Cannot paint on a null pixmap
kded(6416) KDEDModule::setModuleName: Registration of kded module  "desktopnotifier" without dbus interface.
kded(6416) KDEDModule::setModuleName: registerObject() successful for  "desktopnotifier"
QPainter::begin: Cannot paint on a null pixmap
kio_desktop(6475) KIO::ForwardingSlaveBase::listDir: KUrl("desktop:/")
kdeinit4: preparing to launch 
kdeinit4: preparing to launch /usr/bin/kwrited
kio_desktop(6475) KIO::ForwardingSlaveBase::prepareUDSEntry: New Mimetype =  "audio/mpeg"
kdeinit4: preparing to launch /usr/bin/nepomukserver
kio_desktop(6475) KIO::ForwardingSlaveBase::prepareUDSEntry: New Mimetype =  "text/plain"
kio_desktop(6475) KIO::ForwardingSlaveBase::prepareUDSEntry: New Mimetype =  "image/png"
kio_desktop(6475) KIO::ForwardingSlaveBase::prepareUDSEntry: New Mimetype =  "image/jpeg"
kio_desktop(6475) KIO::ForwardingSlaveBase::prepareUDSEntry: New Mimetype =  "application/x-desktop"
kio_desktop(6475) KIO::ForwardingSlaveBase::prepareUDSEntry: New Mimetype =  "inode/directory"
kio_desktop(6475) KIO::ForwardingSlaveBase::prepareUDSEntry: New Mimetype =  "inode/directory"
kwrited(6478) KWrited::KWrited: listening on device /dev/pts/0
kio_desktop(6475) KIO::ForwardingSlaveBase::stat: KUrl("desktop:/distro-timeline.png")
kio_desktop(6475) KIO::ForwardingSlaveBase::prepareUDSEntry: New Mimetype =  "image/png"
kio_desktop(6475) KIO::ForwardingSlaveBase::stat: KUrl("desktop:/weird.jpg")
kio_desktop(6475) KIO::ForwardingSlaveBase::prepareUDSEntry: New Mimetype =  "image/jpeg"
kcminit(6465) KxkbConfig::load: Use kxkb false
kdeinit4: preparing to launch /usr/bin/kaccess
kdeinit4: preparing to launch /usr/bin/kmixctrl
<unknown program name>(6488)/ kdemain: Xlib XKB extension major= 1  minor= 0
kdeinit4: preparing to launch /usr/bin/krunner
kaccess(6488) kdemain: X server XKB extension major= 1  minor= 0
NepomukServer(6480) Nepomuk::ServiceManager::Private::startService: Queueing "nepomukontologyloader" due to dependency "nepomukstorage"
NepomukServer(6480) Nepomuk::ServiceManager::Private::startService: Queueing "nepomukqueryservice" due to dependency "nepomukstorage"
NepomukServer(6480) Nepomuk::ServiceManager::Private::startService: Queueing "nepomukstrigiservice" due to dependency "nepomukstorage"
NepomukServer(6480) Nepomuk::ServiceManager::Private::startService: Queueing "nepomukfilewatch" due to dependency "nepomukstorage"
Nepomuk server already running.
kmixctrl(6489) Mixer::openIfValid: Mixer::open() detected master:  "PCM:0"
(Soprano::PluginManager) loading all plugins 
(Soprano::PluginManager) searching plugin file from  "/usr/share/soprano/plugins" 
kmixctrl(6489) Mixer::getGlobalMasterMD: Mixer::masterCardDevice() returns 0 (no globalMaster)
kmixctrl(6489) Mixer::setGlobalMaster: Mixer::setGlobalMaster() card= "ALSA::HDA_Intel:1"  control= "PCM:0"
QObject: Do not delete object, 'unnamed', during its event handler!
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/nquadparser.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found parser plugin  "nquadparser" 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/nquadserializer.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found serializer plugin  "nquadserializer" 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/raptorparser.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found parser plugin  "raptorparser" 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/raptorserializer.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found serializer plugin  "raptorserializer" 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/redlandbackend.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found backend plugin  "redland" 
(Soprano::PluginManager) searching plugin file from  "/usr/share/soprano/plugins" 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/nquadparser.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/nquadserializer.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/raptorparser.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/raptorserializer.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/redlandbackend.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) searching plugin file from  "/usr/share/soprano/plugins" 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/nquadparser.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/nquadserializer.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/raptorparser.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/raptorserializer.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/redlandbackend.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) searching plugin file from  "/usr/local/share/soprano/plugins" 
(Soprano::PluginManager) loaded plugin from "/usr/lib/soprano/libsoprano_redlandbackend.so" 
[/usr/bin/nepomukservicestub] (Soprano::PluginManager) loading all plugins 
(Soprano::PluginManager) searching plugin file from  "/usr/share/soprano/plugins" 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/nquadparser.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found parser plugin  "nquadparser" 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/nquadserializer.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found serializer plugin  "nquadserializer" 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/raptorparser.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found parser plugin  "raptorparser" 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/raptorserializer.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found serializer plugin  "raptorserializer" 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/redlandbackend.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found backend plugin  "redland" 
(Soprano::PluginManager) searching plugin file from  "/usr/share/soprano/plugins" 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/nquadparser.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/nquadserializer.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/raptorparser.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/raptorserializer.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/redlandbackend.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) searching plugin file from  "/usr/share/soprano/plugins" 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/nquadparser.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/nquadserializer.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/raptorparser.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/raptorserializer.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) found plugin file "/usr/share/soprano/plugins/redlandbackend.desktop" 
(Soprano::PluginManager) plugin has proper version. 
(Soprano::PluginManager) searching plugin file from  "/usr/local/share/soprano/plugins" 
(Soprano::PluginManager) loaded plugin from "/usr/lib/soprano/libsoprano_redlandbackend.so"
NepomukServer(6480) Nepomuk::ServiceController::slotServiceInitialized: Service "nepomukstorage" initialized
NepomukServer(6480) Nepomuk::ServiceManager::Private::_k_serviceInitialized: Service initialized: "nepomukstorage"
[/usr/bin/nepomukservicestub] (Soprano::Redland::BackendPlugin) creating model of type "hashes" with options "hash-type='bdb',contexts='yes',dir='/home/spacegypsy/.kde/share/apps/nepomuk/repository/main/data/redland'" 
CLuceneIndex::open in thread  140431486600944 
CLuceneIndex::close in thread  140431486600944 
CLuceneIndex::close done in thread  140431486600944 
CLuceneIndex::open done in thread  140431486600944 
nepomukstorage(6493) Nepomuk::Repository::open: no need to convert "main"
nepomukstorage(6493) Nepomuk::Storage::slotNepomukCoreInitialized: Successfully initialized nepomuk core
NepomukServer(6480) Nepomuk::ServiceController::slotServiceInitialized: Service "nepomukqueryservice" initialized
NepomukServer(6480) Nepomuk::ServiceManager::Private::_k_serviceInitialized: Service initialized: "nepomukqueryservice"
[/usr/bin/nepomukservicestub] (ServerCore) new socket connection. 
(ServerCore) new socket connection. 
(ServerCore) new socket connection.
NepomukServer(6480) Nepomuk::ServiceController::slotServiceInitialized: Service "nepomukontologyloader" initialized
NepomukServer(6480) Nepomuk::ServiceManager::Private::_k_serviceInitialized: Service initialized: "nepomukontologyloader"
NepomukServer(6480) Nepomuk::ServiceController::slotServiceInitialized: Service "nepomukfilewatch" initialized
NepomukServer(6480) Nepomuk::ServiceManager::Private::_k_serviceInitialized: Service initialized: "nepomukfilewatch"
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyLoader::OntologyLoader: watching "/home/spacegypsy/.kde/share/apps/nepomuk/ontologies/"
nepomukontologyloader(6497) Nepomuk::OntologyLoader::OntologyLoader: watching "/usr/share/kubuntu-default-settings/kde4-profile/default/share/apps/nepomuk/ontologies/"
nepomukontologyloader(6497) Nepomuk::OntologyLoader::OntologyLoader: watching "/usr/share/kde4/apps/nepomuk/ontologies/"
nepomukontologyloader(6497) Nepomuk::OntologyManagerModel::ontoModificationDate: Found modification date for  QUrl( "http://www.semanticdesktop.org/ontologies/2007/01/19/nie#" )  QDateTime("Sun Mar 1 20:32:15 2009")
nepomukontologyloader(6497) Nepomuk::OntologyLoader::Private::updateOntology: Ontology "http://www.semanticdesktop.org/ontologies/2007/01/19/nie#" up to date.
[/usr/bin/nepomukservicestub] nepomukstrigiservice(6499) Nepomuk::StrigiService::StrigiService: Will not start when using redland Soprano backend due to horrible performance.
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyManagerModel::ontoModificationDate: Found modification date for  QUrl( "http://www.semanticdesktop.org/ontologies/2007/03/22/nmo#" )  QDateTime("Sun Mar 1 20:32:17 2009")
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyLoader::Private::updateOntology: Ontology "http://www.semanticdesktop.org/ontologies/2007/03/22/nmo#" up to date.
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyManagerModel::ontoModificationDate: Found modification date for  QUrl( "http://www.w3.org/2000/01/rdf-schema#" )  QDateTime("Sun Mar 1 20:32:18 2009")
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyLoader::Private::updateOntology: Ontology "http://www.w3.org/2000/01/rdf-schema#" up to date.
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyManagerModel::ontoModificationDate: Found modification date for  QUrl( "http://purl.org/dc/terms/" )  QDateTime("Sun Mar 1 20:32:19 2009")
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyLoader::Private::updateOntology: Ontology "http://purl.org/dc/terms/" up to date.
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyManagerModel::ontoModificationDate: Found modification date for  QUrl( "http://www.semanticdesktop.org/ontologies/2007/03/22/nco#" )  QDateTime("Sun Mar 1 20:32:26 2009")
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyLoader::Private::updateOntology: Ontology "http://www.semanticdesktop.org/ontologies/2007/03/22/nco#" up to date.
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyManagerModel::ontoModificationDate: Found modification date for  QUrl( "http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#" )  QDateTime("Sun Mar 1 20:32:30 2009")
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyLoader::Private::updateOntology: Ontology "http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#" up to date.
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyManagerModel::ontoModificationDate: Found modification date for  QUrl( "http://www.semanticdesktop.org/ontologies/2007/08/15/nrl#" )  QDateTime("Sun Mar 1 20:32:35 2009")
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyLoader::Private::updateOntology: Ontology "http://www.semanticdesktop.org/ontologies/2007/08/15/nrl#" up to date.
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyManagerModel::ontoModificationDate: Found modification date for  QUrl( "http://purl.org/dc/dcmitype/" )  QDateTime("Sun Mar 1 20:32:36 2009")
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyLoader::Private::updateOntology: Ontology "http://purl.org/dc/dcmitype/" up to date.
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyManagerModel::ontoModificationDate: Found modification date for  QUrl( "http://www.semanticdesktop.org/ontologies/2007/11/01/pimo#" )  QDateTime("Sun Mar 1 20:32:37 2009")
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyLoader::Private::updateOntology: Ontology "http://www.semanticdesktop.org/ontologies/2007/11/01/pimo#" up to date.
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyManagerModel::ontoModificationDate: Found modification date for  QUrl( "http://www.w3.org/1999/02/22-rdf-syntax-ns#" )  QDateTime("Sun Mar 1 20:32:42 2009")
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyLoader::Private::updateOntology: Ontology "http://www.w3.org/1999/02/22-rdf-syntax-ns#" up to date.
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyManagerModel::ontoModificationDate: Found modification date for  QUrl( "http://freedesktop.org/standards/xesam/1.0/core#" )  QDateTime("Sun Mar 1 20:32:43 2009")
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyLoader::Private::updateOntology: Ontology "http://freedesktop.org/standards/xesam/1.0/core#" up to date.
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyManagerModel::ontoModificationDate: Found modification date for  QUrl( "http://purl.org/dc/elements/1.1/" )  QDateTime("Sun Mar 1 20:33:02 2009")
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyLoader::Private::updateOntology: Ontology "http://purl.org/dc/elements/1.1/" up to date.
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyManagerModel::ontoModificationDate: Found modification date for  QUrl( "http://www.semanticdesktop.org/ontologies/2007/08/15/nao#" )  QDateTime("Sun Mar 1 20:33:03 2009")
[/usr/bin/nepomukservicestub] nepomukontologyloader(6497) Nepomuk::OntologyLoader::Private::updateOntology: Ontology "http://www.semanticdesktop.org/ontologies/2007/08/15/nao#" up to date.
krunner(6494) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"
krunner(6494) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"
[/usr/bin/nepomukservicestub] (ServerCore) new socket connection.
kdeinit4: preparing to launch 
Unknown service name: 1021f2331721ab000123593952500000064290005_1235939574_287682
QObject: Do not delete object, 'unnamed', during its event handler!
kmix(6503) Mixer::setGlobalMaster: Mixer::setGlobalMaster() card= "ALSA::HDA_Intel:1"  control= "PCM:0"
kmix(6503) Mixer::openIfValid: Mixer::open() detected master:  "PCM:0"
QCoreApplication::postEvent: Unexpected null receiver
QObject: Do not delete object, 'unnamed', during its event handler!
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
QObject: Do not delete object, 'unnamed', during its event handler!
Unknown service name: 1021f2331721ab000123593953500000064290016_1235939582_862198
QObject: Do not delete object, 'unnamed', during its event handler!
Unknown service name: 1021f2331721ab000123593953500000064290017_1235939574_277450
QObject: Do not delete object, 'unnamed', during its event handler!
Unknown service name: 1021f2331721ab000123593953500000064290018_1235939574_277699
QObject: Do not delete object, 'unnamed', during its event handler!
Unknown service name: 1021f2331721ab000123593953500000064290019_1235939574_277580
QObject: Do not delete object, 'unnamed', during its event handler!
Unknown service name: 1021f2331721ab000123593953500000064290020_1235939574_277824
kdeinit4: preparing to launch /usr/bin/hp-systray
kded(6416) KDEDModule::setModuleName: Registration of kded module  "susefreespacenotifier" without dbus interface.
kded(6416) KDEDModule::setModuleName: registerObject() successful for  "susefreespacenotifier"
kdeinit4: preparing to launch /usr/bin/jockey-kde
kdeinit4: preparing to launch /usr/bin/guidance-power-manager
kdeinit4: preparing to launch /usr/bin/printer-applet
kdeinit4: preparing to launch /usr/bin/update-notifier-kde
kdeinit4: preparing to launch /usr/bin/knetworkmanager
kdeinit4: preparing to launch /usr/bin/kblueplugd
kdeinit4: preparing to launch /usr/bin/kmix
kdeinit4: preparing to launch /usr/bin/klipper
kded(6416) KDEDModule::setModuleName: Registration of kded module  "dnssdwatcher" without dbus interface.
kded(6416) KDEDModule::setModuleName: registerObject() successful for  "dnssdwatcher"
kded(6416) KDEDModule::setModuleName: Registration of kded module  "remotedirnotify" without dbus interface.
kded(6416) KDEDModule::setModuleName: registerObject() successful for  "remotedirnotify"
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
kded(6416) KDEDModule::setModuleName: registerObject() successful for  "khotkeys"
kded(6416) KDEDModule::setModuleName: registerObject() returned false for  "khotkeys"
kdeinit4: preparing to launch /usr/bin/knotify4
QObject: Do not delete object, 'unnamed', during its event handler!
QCoreApplication::postEvent: Unexpected null receiver
[35;01mwarning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.[0m

[01mHP Linux Imaging and Printing System (ver. 2.8.7)[0m
[01mSystem Tray Status Service ver. 0.1[0m

Copyright (c) 2001-8 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

No battery found.
This is not a laptop, quitting ... 
QObject: Do not delete object, 'unnamed', during its event handler!
guidance-power-manager(6513): Communication problem with  "guidance-power-manager" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" " 

QCoreApplication::postEvent: Unexpected null receiver

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

DCOPClient::attachInternal. Attach failed Could not open network socket
kded(6416) KDEDModule::setModuleName: registerObject() successful for  "phononserver"
knotify(6523) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
knotify(6523) NotifyByPopup::closeNotificationDBus: not found dbus id to close
DCOPClient::attachInternal. Attach failed Could not open network socket
kbuildsycoca running...
Reusing existing ksycoca
QObject: Do not delete object, 'unnamed', during its event handler!
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update
QObject: Do not delete object, 'unnamed', during its event handler!
kdeinit4: preparing to launch /usr/bin/kvkbd
QCoreApplication::postEvent: Unexpected null receiver
QObject: Do not delete object, 'unnamed', during its event handler!
QObject: Do not delete object, 'unnamed', during its event handler!
QObject: Do not delete object, 'unnamed', during its event handler!

kdeinit4: preparing to launch /usr/bin/desktop-effects-kde4
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
QObject: Do not delete object, 'unnamed', during its event handler!
signalled
QObject: Do not delete object, 'unnamed', during its event handler!
kdeinit4: preparing to launch /usr/bin/desktop-effects-kde4
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
signalled
QObject: Do not delete object, 'unnamed', during its event handler!
kdeinit4: preparing to launch /usr/bin/ccsm
QObject: Do not delete object, 'unnamed', during its event handler!
klauncher(6414) KRunMX2::expandEscapedMacro: No URLs supplied to single-URL service "firefox %u"
kdeinit4: preparing to launch /usr/bin/firefox
QClipboard::setData: Cannot set X11 selection owner for PRIMARY
firefox: Fatal IO error 11 (Resource temporarily unavailable) on X server ÐB&#376;.
QObject: Do not delete object, 'unnamed', during its event handler!
QObject: Do not delete object, 'unnamed', during its event handler!
ksmserver(6467) Solid::Control::ManagerBasePrivate::loadBackend: Backend loaded:  "HAL-Power"
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 55 (X_CreateGC)
  Resource id:  0x0
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 56 (X_ChangeGC)
  Resource id:  0x1200104
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 56 (X_ChangeGC)
  Resource id:  0x1200105
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 56 (X_ChangeGC)
  Resource id:  0x1200104
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 56 (X_ChangeGC)
  Resource id:  0x1200105
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x1200105
X Error: BadGC (invalid GC parameter) 13
  Major opcode: 60 (X_FreeGC)
  Resource id:  0x1200104
knotify(6523) NotifyByPopup::closeNotificationDBus: not found dbus id to close
QObject: Do not delete object, 'unnamed', during its event handler!
QObject: Do not delete object, 'unnamed', during its event handler!
QObject: Do not delete object, 'unnamed', during its event handler!
QObject: Do not delete object, 'unnamed', during its event handler!
QObject: Do not delete object, 'unnamed', during its event handler!
Application '/usr/bin/nepomukservicestub' exited normally...
NepomukServer(6480) Nepomuk::ServiceController::slotProcessFinished: Service "nepomukontologyloader" went down
QObject: Do not delete object, 'unnamed', during its event handler!
QObject: Do not delete object, 'unnamed', during its event handler!
QObject: Do not delete object, 'unnamed', during its event handler!
QObject: Do not delete object, 'unnamed', during its event handler!
QObject: Do not delete object, 'unnamed', during its event handler!
Application '/usr/bin/nepomukservicestub' exited normally...
NepomukServer(6480) Nepomuk::ServiceController::slotProcessFinished: Service "nepomukqueryservice" went down
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  2 (X_ChangeWindowAttributes)
  Resource id in failed request:  0x14000ce
  Serial number of failed request:  1364
  Current serial number in output stream:  1406
QObject: Do not delete object, 'unnamed', during its event handler!
NMSettings::NMSettings
Storage::saveConnections
QObject: Do not delete object, 'unnamed', during its event handler!
QObject: Do not delete object, 'unnamed', during its event handler!
QObject: Do not delete object, 'unnamed', during its event handler!
ProcessControl: Application '/usr/bin/nepomukservicestub' stopped unexpected (Process crashed)
Application '/usr/bin/nepomukservicestub' exited normally...
NepomukServer(6480) Nepomuk::ServiceController::slotProcessFinished: Service "nepomukfilewatch" went down
[/usr/bin/nepomukservicestub] Removing connection 
Removing connection 
Removing connection 
Removing connection 
CLuceneIndex::close in thread  140431486600944 
CLuceneIndex::close done in thread  140431486600944
Application '/usr/bin/nepomukservicestub' exited normally...
NepomukServer(6480) Nepomuk::ServiceController::slotProcessFinished: Service "nepomukstorage" went down
QObject: Do not delete object, 'unnamed', during its event handler!
Unrecognized character: /
Unrecognized character: /
ERROR: syntax error
Unrecognized character: /
Unrecognized character: /
ERROR: syntax error
Unrecognized character: /
Unrecognized character: /
ERROR: syntax error
startkde: Shutting down...
klauncher: Exiting on signal 1
kwrited(6478) sigterm_handler: Caught signal 1 , exiting...
startkde: Running shutdown scripts...
startkde: Done.
kdeinit: Fatal IO error: client killed
klauncher: Exiting on signal 15
kded: Fatal IO error: client killed
```

when I'm logged in I got now a fresh KDE4.2 desktop, but still no window decoration and no keyboard.

---

### Post by Aries-Belgium on 2009-03-09
@spacegypsy: have you managed to find the problem?

I had similar problems when I tried upgrading KDE4.1 to 4.2: no window decoration, no keyboard, ...

I've ended up reinstalling Kubuntu completely because I couldn't find a good way to downgrade KDE back to 4.1.

If you have found the problem I would maybe consider upgrading again to 4.2 otherwise I'm just going to wait for Kubuntu 9.04 when Kubuntu officially supports KDE4.2

---

### Post by spacegypsy on 2009-03-11
Nope, no solution yet.

I'll probably wait till 9.4 is out.

I'm using Ubuntu Studio 8.4 as my main distro for the moment.

---

### Post by wankel on 2009-04-29
Kubuntu 9.04 is out now, but I still got the symptoms you describe.

I think I upgraded from 8.04. 

At first there was a window decoration, namely my messed-up kwin-with-a-bit-of-broken-compiz, that I tried to avoid but actually was my KDE3 reality.

Of course, that changed when I renamed my ~/.kde to ~/.kde3 and the ~/.kde4 to ~/.kde

After that, like you describe: 
- no window decoration
- no keyboard

I can start programs, but they'll pile on top of each other in the top left corner.

I also can "kwin --replace" in a "run"-dialog, by selecting-middle-mousing-pasting it letter for letter from different files into the run-dialog.

kwin does not start though.

There's a nvidia-binary driver on my system. Using vesa driver removes the larger part of my screen estate (twinview), but does not give window decoration in place.

Any tips?

---

### Post by wankel on 2009-04-29
Not all that helpful, but if I quickly start konqueror before the desktop is set up, I can use my keyboard (previous post was from another computer).

If I do that, there is a taskbar entry for konqueror. It remains until the desktop is fully build (notification area, plasmoids, session, whatever); than the taskbar is empty again no matter how many applications are running stacked on top of each other in this upper left corner.

To me it seems that something in the startup of KDE breaks the whole thing. I also tried an account that had not before been used yet, to no avail.

---

### Post by Zorael on 2009-04-29
Ouch.

If you create a new user in a recovery session (**useradd** command), does this happen for him as well?

You could try letting **aptitude** reinstall the kubuntu-desktop metapackage, too.
```
$ sudo aptitude _reinstall_ kubuntu-desktop
```

edit:
> **wankel said:**
> To me it seems that something in the startup of KDE breaks the whole thing. I also tried an account that had not before been used yet, to no avail.
Missed that. Hmm.

Have a look at /etc/xdg/autostart, /usr/share/autostart, ~/.kde/Autostart and ~/.local/autostart (or is it ~/.config/autostart?); see if there's anything there that could mess things up.

---

### Post by wankel on 2009-04-30
At the moment I get a usable desktop by starting another window decorator. After trying out a few, I now manually start metacity after getting to my desktop.

Though it is less than a patchy work around, you could try and find out which of the following works:
```

emerald --replace
kwin --replace
compiz --replace
metacity --replace

``` 

Compiz does not run anymore in my case since I broke something in it over a year ago and did not look into it.
Kwin comes back with those hints that I still have to figure out:
```

wankel@local:~$ kwin --replace
kwin(24791) KDecorationPlugins::loadPlugin: kwin : path  "/usr/lib/kde4/kwin3_oxygen.so"  for  "kwin3_oxygen"
kwin(24791) KDecorationPlugins::loadPlugin:  could not load library, try default plugin again
KWin: The default decoration plugin is corrupt and could not be loaded.
KWin will now exit...

```

If I replace metacity with kwin afterwards, my cursor also changes behaviour: focus follows the mouse, though I do not have that configured in any desktop environment (save perhaps matchbox)


> **Zorael said:**
> Ouch.
If you create a new user in a recovery session (**useradd** command), does this happen for him as well?

I actually did not create the user after upgrading; it was a user created to facilitate a "will perhaps login on SSH", but not used so far.

```
$ sudo aptitude _reinstall_ kubuntu-desktop
```

I haven't reinstalled kubuntu-desktop yet, will try right after posting. Yesterday I did try the following, amongst others (according to [http://kubuntuforums.net/forums/index.php?topic=3101481.15](http://kubuntuforums.net/forums/index.php?topic=3101481.15), " KDE 4.1 -> 4.2 upgrade broke my window manager "):

```

wankel@local:~$ sudo apt-get --reinstall install libkdecorations4
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 52.3kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]?
Get:1 http://nl.archive.ubuntu.com jaunty/main libkdecorations4 4:4.2.2-0ubuntu2 [52.3kB]
Fetched 52.3kB in 0s (93.4kB/s)
(Reading database ... 314366 files and directories currently installed.)
Preparing to replace libkdecorations4 4:4.2.2-0ubuntu2 (using .../libkdecorations4_4%3a4.2.2-0ubuntu2_i386.deb) ...
Unpacking replacement libkdecorations4 ...
Setting up libkdecorations4 (4:4.2.2-0ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
wankel@local:~$ sudo apt-get --reinstall install kdebase-workspace
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  kdebase-workspace
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 43.0kB of archives.
After this operation, 324kB of additional disk space will be used.
Get:1 http://nl.archive.ubuntu.com jaunty/main kdebase-workspace 4:4.2.2-0ubuntu2 [43.0kB]
Fetched 43.0kB in 0s (76.0kB/s)
Selecting previously deselected package kdebase-workspace.
(Reading database ... 314366 files and directories currently installed.)
Unpacking kdebase-workspace (from .../kdebase-workspace_4%3a4.2.2-0ubuntu2_all.deb) ...
Setting up kdebase-workspace (4:4.2.2-0ubuntu2) ...
wankel@local:~$


```

> 
Have a look at /etc/xdg/autostart, /usr/share/autostart, ~/.kde/Autostart and ~/.local/autostart (or is it ~/.config/autostart?); see if there's anything there that could mess things up.
I will, due to lack of time now probably tomorrow. Thanks for the suggestions!

---

### Post by squelsh on 2009-05-07
Hey guys!

Same prob here. No windows decoration (same error from kDecorationPlugins) and no keyboard.

First I found a wrong path to the kdm configfile "kdmrc" in /etc/init.d/kdm
Correcting it made no changes :(

It got a bit better, when I deleted .kde from my home-folder, now the widgets work again but still no window decoration nor keyboard.

I also reinstalled kubuntu-desktop. No Changes :(
Same problems also with a new created user.

Do you think, the plugins are really corrupt? Or is it more likely a incompatible gfx driver? I also have an gForce Card...

Greetz,
Squelsh

---

### Post by squelsh on 2009-05-07
Well, finally the hint from [http://kubuntuforums.net/forums/index.php?topic=3101481.msg169013#msg169013]("http://kubuntuforums.net/forums/index.php?topic=3101481.msg169013#msg169013") helped!

I removed kdelibs5 and reinstalled kubuntu-desktop and now everything works again!

Keep an eye on the apps that will be removed with kdelibs5. I had to reinstall some of them manually.

---

### Post by spacegypsy on 2009-05-13
> **squelsh said:**
> Well, finally the hint from [http://kubuntuforums.net/forums/index.php?topic=3101481.msg169013#msg169013]("http://kubuntuforums.net/forums/index.php?topic=3101481.msg169013#msg169013") helped!

I removed kdelibs5 and reinstalled kubuntu-desktop and now everything works again!

Keep an eye on the apps that will be removed with kdelibs5. I had to reinstall some of them manually.

Glad to see that you found a solution that worked.

I went for the radical solution; fresh install of Kubuntu 9.04 and no more Compiz (KD4.2 has all the effects i want).

---

