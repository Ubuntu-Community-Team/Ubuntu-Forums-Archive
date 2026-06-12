---
title: "Suppress Amarok Terminal Output"
date: 2006-10-05
forum: Desktop Environments
---

### Post by liquidsunshine@gmail.com on 2006-10-05
I am currently trying to write a script to easily control amaroK from terminal (so I can ssh into it from another computer) and in the script I want to have the option to start and stop amaroK.  Stopping is easy (killall amarokapp) but when I start it in terminal, it gives me a lot of debugging information that clogs up the terminal.  

I have tried to suppress it using:
*amarokapp &*
*amarokapp > /dev/null *

but neither of those work.  I am not sure how else I could suppress the terminal output.  Any ideas?  It'd be nice to be able to do it a "right way" if there is one, but hacks would be appreciated as well.

---

### Post by liquidsunshine@gmail.com on 2006-10-05
No ideas?  Anyone know why amaroK doesn't like going to the background?

Well maybe posting my exact script and output will give someone an idea...

```
export DISPLAY=:0.0;
while :
 do
    clear
    echo "-------------------------------------"
    echo "Now playing:"
    echo |dcop --user liquidsunshine amarok player nowPlaying
    echo "-------------------------------------"
    echo " Main Menu "
    echo "-------------------------------------"
    echo "[0] Run amaroK"
    echo "[1] Play"
    echo "[2] Pause"
    echo "[3] Stop"
    echo "[4] Next"
    echo "[5] Previous"
    echo "[6] Mute"
    echo "[7] Volume Down 10"
    echo "[8] Volume Up 10"
    echo "[9] Full Volume"
    echo "[10] Close amaroK"
    echo "======================="
    echo -n "Enter your menu choice [0-10]: "
    read yourch
    case $yourch in
      0) amarokapp & > /dev/null; read ;;
      1) dcop --user liquidsunshine amarok player play ; read ;;
      2) dcop --user liquidsunshine amarok player pause; read;;
      3) dcop --user liquidsunshine amarok player stop; read;;
      4) dcop --user liquidsunshine amarok player next; read;;
      5) dcop --user liquidsunshine amarok player prev; read;;
      6) dcop --user liquidsunshine amarok player mute; read;;
      7) dcop --user liquidsunshine amarok player setVolumeRelative -10; read;;
      8) dcop --user liquidsunshine amarok player setVolumeRelative 10; read;;
      9) dcop --user liquidsunshine amarok player setVolume 100; read;;
      10) killall amarokapp; read ;;
      *) echo "Opps!!! Please select a valid choice";
         echo "Press a key. . ." ; read ;;
 esac
done
```

and 

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
amarok: BEGIN: App::App()
Link points to "/tmp/ksocket-liquidsunshine"
Link points to "/tmp/kde-liquidsunshine"
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
amarok: BEGIN: void App::fixHyperThreading()
amarok:     Workaround not enabled
amarok: END__: void App::fixHyperThreading() - Took 0.00044s
amarok: END__: App::App() - Took 1.3s
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
amarok: END__: EngineBase* EngineController::loadEngine(const QString&) - Took 0.035s
amarok: BEGIN: CollectionDB::CollectionDB()
amarok: BEGIN: void CollectionDB::initialize()
amarok:       [ThreadWeaver] Creating pthread key, exit value is 0
amarok: BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok: END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.039s
amarok: END__: void CollectionDB::initialize() - Took 0.31s
amarok:     [CollectionDB] INotify not available, using QTimer!
amarok: END__: CollectionDB::CollectionDB() - Took 0.38s
amarok: BEGIN: void CollectionDB::checkDatabase()
amarok:     [CollectionDB] INotify not available, using QTimer!
amarok: END__: void CollectionDB::checkDatabase() - Took 0.075s
amarok: BEGIN: MediaDeviceManager::MediaDeviceManager()
amarok: BEGIN: DeviceManager::DeviceManager()
amarok:       During DeviceManager init, error during DCOP call
amarok: BEGIN: Medium* DeviceManager::getDevice(QString)
amarok:         DeviceManager: getDevice called with name argument = init
amarok: BEGIN: QStringList DeviceManager::getDeviceStringList()
amarok:           Error during DCOP call
amarok: END__: QStringList DeviceManager::getDeviceStringList() - Took 0.00025s
amarok: END__: Medium* DeviceManager::getDevice(QString) - Took 0.00042s
amarok:       DeviceManager:  connectDCOPSignal returned successfully!
amarok: END__: DeviceManager::DeviceManager() - Took 0.0015s
amarok: BEGIN: QStringList DeviceManager::getDeviceStringList()
amarok:       Error during DCOP call
amarok: END__: QStringList DeviceManager::getDeviceStringList() - Took 0.00022s
amarok:     DeviceManager didn't return any devices, we are probably running on a non-KDE system. Trying to reinit media devices later
amarok: END__: MediaDeviceManager::MediaDeviceManager() - Took 0.0021s
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
amarok: END__: QStringList DeviceManager::getDeviceStringList() - Took 0.0004s
amarok: END__: void MountPointManager::init() - Took 0.05s
amarok:     [Moodbar] Resetting moodbar:
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
amarok: BEGIN: Creating browsers. Please report long start times!
amarok: BEGIN: ContextBrowser
amarok: BEGIN: virtual void ThreadWeaver::Thread::run()
amarok: END__: ContextBrowser - Took 0.18s
amarok: BEGIN: CollectionBrowser
amarok:           [CollectionView::CollectionView(CollectionBrowser*)]
amarok: BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok: END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.0026s
amarok:           current browser is not collection, aborting renderView()
amarok: END__: CollectionBrowser - Took 0.087s
amarok: BEGIN: PlaylistBrowser
amarok: BEGIN: PlaylistCategory* PlaylistBrowser::loadPodcasts()
amarok: END__: PlaylistCategory* PlaylistBrowser::loadPodcasts() - Took 0.065s
amarok: END__: PlaylistBrowser - Took 0.083s
amarok: BEGIN: FileBrowser
amarok: END__: FileBrowser - Took 0.37s
amarok: END__: virtual void ThreadWeaver::Thread::run() - Took 0.6s
amarok:       [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 27 and [X-KDE-Amarok-plugintype] == 'mediadevice' and [X-KDE-Amarok-rank] > 0
amarok: BEGIN: MediaBrowser
amarok: END__: MediaBrowser - Took 0.016s
amarok: END__: Creating browsers. Please report long start times! - Took 0.86s
amarok: END__: void PlaylistWindow::init() - Took 1.5s
amarok: BEGIN: UrlLoader
amarok:     [KDE::ProgressBar::ProgressBar(QWidget*, QLabel*)]
amarok:     | Stamp: 1
amarok: BEGIN: void App::applySettings(bool)
amarok:       [Moodbar] Resetting moodbar:
amarok: BEGIN: virtual void ThreadWeaver::Thread::run()
amarok: BEGIN: EngineBase* EngineController::loadEngine()
amarok: BEGIN: EngineBase* EngineController::loadEngine(const QString&)
amarok:             [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 27 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] != 'xine-engine' and [X-KDE-Amarok-rank] > 0
amarok:             [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 27 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] == 'xine-engine' and [X-KDE-Amarok-rank] > 0
amarok:             [PluginManager] Trying to load: libamarok_xine-engine
amarok: BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok: END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.00043s
amarok:             [xine-engine] hello
amarok:
amarok:             PluginManager Service Info:
amarok:             ---------------------------
amarok:             name                          : xine Engine
amarok:             library                       : libamarok_xine-engine
amarok:             desktopEntryPath              : amarok_xine-engine.desktop
amarok:             X-KDE-Amarok-plugintype       : engine
amarok:             X-KDE-Amarok-name             : xine-engine
amarok:             X-KDE-Amarok-authors          : (Max Howell)
amarok:             X-KDE-Amarok-rank             : 255
amarok:             X-KDE-Amarok-version          : 1
amarok:             X-KDE-Amarok-framework-version: 27
amarok:
amarok: BEGIN: virtual bool XineEngine::init()
amarok:               [xine-engine] 'Bringing joy to small mexican gerbils, a few weeks at a time.'
amarok:               [xine-engine] w00t/home/liquidsunshine/.kde/share/apps/amarok/xine-config
amarok: END__: virtual void ThreadWeaver::Thread::run() - Took 0.34s
amarok:             [xine-engine] gapless playback enabled.
amarok: END__: virtual bool XineEngine::init() - Took 0.13s
amarok: END__: EngineBase* EngineController::loadEngine(const QString&) - Took 0.35s
amarok: END__: EngineBase* EngineController::loadEngine() - Took 0.35s
amarok:       current browser is not collection, aborting renderView()
amarok: END__: void App::applySettings(bool) - Took 0.43s
amarok:     | Stamp: 2
amarok: BEGIN: ScriptManager::ScriptManager(QWidget*, const char*)
amarok: END__: ScriptManager::ScriptManager(QWidget*, const char*) - Took 0.0032s
amarok:     | Stamp: 3
STARTUP
amarok:     [Moodbar] Resetting moodbar:
amarok: BEGIN: ScanController::ScanController(CollectionDB*, bool, const QStringList&)
amarok: BEGIN: void ScanController::initIncremental()
amarok:         [ThreadWeaver] Job aborted: CurrentTrackJob. Jobs pending: 1
amarok: BEGIN: virtual void ThreadWeaver::Thread::run()
amarok: BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok: END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.00029s
amarok: END__: virtual void ThreadWeaver::Thread::run() - Took 0.065s
amarok: BEGIN: virtual void UrlLoader::completeJob()
amarok: END__: virtual void UrlLoader::completeJob() - Took 0.00016s
amarok:         [ThreadWeaver] Job completed: UrlLoader. Jobs pending: 0
amarok: END__: UrlLoader - Took 0.73s
amarok:       [virtual KDE::ProgressBar::~ProgressBar()]
amarok:       [ThreadWeaver] Job completed: CurrentTrackJob. Jobs pending: 0
amarok: BEGIN: virtual void ThreadWeaver::Thread::run()
amarok: BEGIN: virtual bool StatisticsUpdateJob::doJob()
amarok: BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok: END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.00033s
amarok:           [MountPointManager] Trying to update 2 statistics rows
amarok: END__: virtual bool StatisticsUpdateJob::doJob() - Took 0.0037s
amarok: END__: virtual void ThreadWeaver::Thread::run() - Took 0.01s
amarok:       [ScriptManager] Loaded: playlist2html.py
amarok:       [ScriptManager] Loaded: PlaylistServer.py
amarok:       [ScriptManager] Loaded: Web Control
amarok:       [ScriptManager] Loaded: Lyrc
amarok:       [ScriptManager] Loaded: Default
amarok:       [ScriptManager] Loaded: Impulsive
amarok:       [ThreadWeaver] Job completed: StatisticsUpdateJob. Jobs pending: 0amarok: BEGIN: QStringList DeviceManager::getDeviceStringList()
amarok:         Error during DCOP call
amarok: END__: QStringList DeviceManager::getDeviceStringList() - Took 0.00047s
amarok: END__: void ScanController::initIncremental() - Took 1.2s
amarok: END__: ScanController::ScanController(CollectionDB*, bool, const QStringList&) - Took 1.2s
amarok: END__: void App::continueInit() - Took 4.7s
amarok: BEGIN: virtual void ThreadWeaver::Thread::run()
amarok: BEGIN: virtual bool ScanController::doJob()
amarok: BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok: END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.00069s
amarok: END__: virtual bool ScanController::doJob() - Took 0.00083s
amarok:   [CollectionDB] JobFinishedEvent from Incremental ScanController received.
amarok:   [ThreadWeaver] Job completed: CollectionScanner. Jobs pending: 0
amarok: BEGIN: virtual ScanController::~ScanController()
amarok: END__: virtual ScanController::~ScanController() - Took 0.00076s
amarok: END__: virtual void ThreadWeaver::Thread::run() - Took 0.014s

Does the "amarok: ...." form mean it's sending it as a kernel message or something?  I'm just looking for any way to hide that stuff so I can run my script in peace... :rolleyes:

---

### Post by liquidsunshine@gmail.com on 2006-10-05
Is there no way I can suppress terminal output from this program?  Should I file this as a bug with amaroK's developers? Is there nothing I can do in the meantime?

---

### Post by Capricori on 2007-10-14
Hey, nice script. I tried running it, but got an error about multiple sessions?

You probably already know, but you can control Amarok with the GUI over SSH as well? 
```
ssh -XC name/IP amarokapp
```

and replacing name/IP with the name or IP of the machine you're SSH-ing into.
The X flag enables X forwarding, and the C flag compresses everything, which I find reduces the lag.

---

