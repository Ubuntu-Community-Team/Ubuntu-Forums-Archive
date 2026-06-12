---
title: "Amarok 1.4.1 freezes"
date: 2006-07-11
forum: Desktop Environments
---

### Post by Wr8EYilK8Y on 2006-07-11
I did a complete removal, upgrade, you name it. Amarok 1.4.1 just freezes. I know this because XGL turns it gray, and I can't do anything with it. No log or anything. Help!!!

---

### Post by Wr8EYilK8Y on 2006-07-11
Bump

---

### Post by andrebtoda on 2006-10-01
> 
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amarok: BEGIN: App::App()
kbuildsycoca running...
amarok: BEGIN: void App::fixHyperThreading()
amarok:     Workaround not enabled
amarok: END__: void App::fixHyperThreading() - Took 0.0012s
amarok: END__: App::App() - Took 0.93s
amarok: BEGIN: void App::continueInit()
amarok: BEGIN: EngineBase* EngineController::loadEngine(const QString&)
amarok:     [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 27 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] != 'void-engine' and [X-KDE-Amarok-rank] > 0
amarok:     [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 27 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] == 'void-engine' and [X-KDE-Amarok-rank] > 0
amarok:     [PluginManager] Trying to load: libamarok_void-engine_plugin
amarok:
amarok:     PluginManager Service Info:
amarok:     ---------------------------
amarok:     name                          : <no engine>
amarok:     library                       : libamarok_void-engine_plugin
amarok:     desktopEntryPath              : amarok_void-engine_plugin.desktop
amarok:     X-KDE-Amarok-plugintype       : engine
amarok:     X-KDE-Amarok-name             : void-engine
amarok:     X-KDE-Amarok-authors          : (Max Howell,Mark Kretschmann)
amarok:     X-KDE-Amarok-rank             : 1
amarok:     X-KDE-Amarok-version          : 1
amarok:     X-KDE-Amarok-framework-version: 27
amarok:
amarok: END__: EngineBase* EngineController::loadEngine(const QString&) - Took 0.0079s
amarok: BEGIN: CollectionDB::CollectionDB()
amarok: BEGIN: void CollectionDB::initialize()
amarok:       [ThreadWeaver] Creating pthread key, exit value is 0
amarok: BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok: END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.00073s
amarok: END__: void CollectionDB::initialize() - Took 0.04s
amarok:     [CollectionDB] INotify not available, using QTimer!
amarok: END__: CollectionDB::CollectionDB() - Took 0.045s
amarok: BEGIN: void CollectionDB::checkDatabase()
amarok:     [CollectionDB] INotify not available, using QTimer!
amarok: END__: void CollectionDB::checkDatabase() - Took 0.078s
amarok: BEGIN: MediaDeviceManager::MediaDeviceManager()
amarok: BEGIN: DeviceManager::DeviceManager()
amarok:       During DeviceManager init, error during DCOP call
amarok: BEGIN: Medium* DeviceManager::getDevice(QString)
amarok:         DeviceManager: getDevice called with name argument = init
amarok: BEGIN: QStringList DeviceManager::getDeviceStringList()
amarok:           Error during DCOP call
amarok: END__: QStringList DeviceManager::getDeviceStringList() - Took 0.00032s
amarok: END__: Medium* DeviceManager::getDevice(QString) - Took 0.00049s
amarok:       DeviceManager:  connectDCOPSignal returned successfully!
amarok: END__: DeviceManager::DeviceManager() - Took 0.0019s
amarok: BEGIN: QStringList DeviceManager::getDeviceStringList()
amarok:       Error during DCOP call
amarok: END__: QStringList DeviceManager::getDeviceStringList() - Took 0.0003s
amarok:     DeviceManager didn't return any devices, we are probably running on a non-KDE system. Trying to reinit media devices later
amarok: END__: MediaDeviceManager::MediaDeviceManager() - Took 0.0026s
amarok: BEGIN: void PlaylistWindow::init()
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
amarok: BEGIN: void MountPointManager::init()
amarok:       [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 27 and [X-KDE-Amarok-plugintype] == 'device' and [X-KDE-Amarok-rank] > 0
amarok:       [MountPointManager] Received [3] device plugin offers
amarok:       [PluginManager] Trying to load: libamarok_massstorage-device
amarok:
amarok:       PluginManager Service Info:
amarok:       ---------------------------
amarok:       name                          : Mass Storage Device
amarok:       library                       : libamarok_massstorage-device
amarok:       desktopEntryPath              : amarok_massstorage-device.desktop
amarok:       X-KDE-Amarok-plugintype       : device
amarok:       X-KDE-Amarok-name             : massstorage-device
amarok:       X-KDE-Amarok-authors          : (Maximilian Kossick)
amarok:       X-KDE-Amarok-rank             : 100
amarok:       X-KDE-Amarok-version          : 1
amarok:       X-KDE-Amarok-framework-version: 27
amarok:
amarok:       [PluginManager] Trying to load: libamarok_smb-device
amarok:
amarok:       PluginManager Service Info:
amarok:       ---------------------------
amarok:       name                          : SMB Device
amarok:       library                       : libamarok_smb-device
amarok:       desktopEntryPath              : amarok_smb-device.desktop
amarok:       X-KDE-Amarok-plugintype       : device
amarok:       X-KDE-Amarok-name             : smb-device
amarok:       X-KDE-Amarok-authors          : (Maximilian Kossick)
amarok:       X-KDE-Amarok-rank             : 100
amarok:       X-KDE-Amarok-version          : 1
amarok:       X-KDE-Amarok-framework-version: 27
amarok:
amarok:       [PluginManager] Trying to load: libamarok_nfs-device
amarok:
amarok:       PluginManager Service Info:
amarok:       ---------------------------
amarok:       name                          : NFS Device
amarok:       library                       : libamarok_nfs-device
amarok:       desktopEntryPath              : amarok_nfs-device.desktop
amarok:       X-KDE-Amarok-plugintype       : device
amarok:       X-KDE-Amarok-name             : nfs-device
amarok:       X-KDE-Amarok-authors          : (Maximilian Kossick)
amarok:       X-KDE-Amarok-rank             : 100
amarok:       X-KDE-Amarok-version          : 1
amarok:       X-KDE-Amarok-framework-version: 27
amarok:
amarok: BEGIN: QStringList DeviceManager::getDeviceStringList()
amarok:         Error during DCOP call
amarok: END__: QStringList DeviceManager::getDeviceStringList() - Took 0.00032s
amarok: END__: void MountPointManager::init() - Took 0.0087s
amarok:     [Moodbar] Resetting moodbar:
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
amarok: BEGIN: Creating browsers. Please report long start times!
amarok: BEGIN: ContextBrowser
amarok: END__: ContextBrowser - Took 0.27s
amarok: BEGIN: CollectionBrowser
amarok:         [CollectionView::CollectionView(CollectionBrowser*)]
amarok:         current browser is not collection, aborting renderView()
amarok: END__: CollectionBrowser - Took 0.029s
amarok: BEGIN: PlaylistBrowser
amarok: BEGIN: PlaylistCategory* PlaylistBrowser::loadPodcasts()
amarok: END__: PlaylistCategory* PlaylistBrowser::loadPodcasts() - Took 0.0013s
amarok: END__: PlaylistBrowser - Took 0.077s
amarok: BEGIN: FileBrowser
amarok: END__: FileBrowser - Took 0.21s
amarok:       [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 27 and [X-KDE-Amarok-plugintype] == 'mediadevice' and [X-KDE-Amarok-rank] > 0
amarok: BEGIN: MediaBrowser
amarok: END__: MediaBrowser - Took 0.046s
amarok: END__: Creating browsers. Please report long start times! - Took 0.67s
amarok: END__: void PlaylistWindow::init() - Took 0.87s
amarok:   | Stamp: 1
amarok: BEGIN: void App::applySettings(bool)
amarok:     [Moodbar] Resetting moodbar:
amarok:     [virtual void BrowserBar::polish()]
amarok:     [void ContextBrowser::tabChanged(QWidget*)]
amarok:     current browser is not collection, aborting renderView()
amarok: BEGIN: virtual void ThreadWeaver::Thread::run()
amarok: BEGIN: virtual bool StatisticsUpdateJob::doJob()
amarok: BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok: END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.0003s
amarok:         [MountPointManager] Trying to update 0 statistics rows
amarok: END__: virtual bool StatisticsUpdateJob::doJob() - Took 0.0017s
amarok: END__: virtual void ThreadWeaver::Thread::run() - Took 0.002s
amarok: BEGIN: EngineBase* EngineController::loadEngine()
amarok: BEGIN: EngineBase* EngineController::loadEngine(const QString&)
amarok:         [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 27 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] != '' and [X-KDE-Amarok-rank] > 0
amarok:         [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 27 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] == '' and [X-KDE-Amarok-rank] > 0
amarok:         [PluginManager] Trying to load: libamarok_xine-engine
amarok:         [xine-engine] hello
amarok:
amarok:         PluginManager Service Info:
amarok:         ---------------------------
amarok:         name                          : xine Engine
amarok:         library                       : libamarok_xine-engine
amarok:         desktopEntryPath              : amarok_xine-engine.desktop
amarok:         X-KDE-Amarok-plugintype       : engine
amarok:         X-KDE-Amarok-name             : xine-engine
amarok:         X-KDE-Amarok-authors          : (Max Howell)
amarok:         X-KDE-Amarok-rank             : 255
amarok:         X-KDE-Amarok-version          : 1
amarok:         X-KDE-Amarok-framework-version: 27
amarok:
amarok: BEGIN: virtual bool XineEngine::init()
amarok:           [xine-engine] 'Bringing joy to small mexican gerbils, a few weeks at a time.'
amarok:           [xine-engine] w00t/home/andre/.kde/share/apps/amarok/xine-config
amarok:           [xine-engine] gapless playback enabled.
amarok: END__: virtual bool XineEngine::init() - Took 0.29s
amarok: END__: EngineBase* EngineController::loadEngine(const QString&) - Took 0.3s
amarok: END__: EngineBase* EngineController::loadEngine() - Took 0.3s
amarok:     current browser is not collection, aborting renderView()
amarok: END__: void App::applySettings(bool) - Took 1.1s
amarok:   | Stamp: 2
amarok: BEGIN: ScriptManager::ScriptManager(QWidget*, const char*)
amarok: END__: ScriptManager::ScriptManager(QWidget*, const char*) - Took 0.11s
amarok:   | Stamp: 3
amarok:   [Moodbar] Resetting moodbar:
[email]andre@andre-linux:~/.kde[/email]/share/apps/amarok$ amarok:   current browser is not collection, aborting renderView()
amarok: END__: void App::continueInit() - Took 2.5s
amarok: [ThreadWeaver] Job completed: StatisticsUpdateJob. Jobs pending: 0
amarok: [ScriptManager] Loaded: playlist2html.py
amarok: [ScriptManager] Loaded: PlaylistServer.py
amarok: [ScriptManager] Loaded: Lyrc
amarok: [ScriptManager] Loaded: Default
amarok: [ScriptManager] Loaded: Impulsive
amarok: [ScriptManager] Loaded: Web Control
amarok: BEGIN: QStringList DeviceManager::getDeviceStringList()

I Have the same problem

Amarok freeze at this time...what i should do???
HELP US PLEASE

---

