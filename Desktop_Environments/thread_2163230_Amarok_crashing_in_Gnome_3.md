---
title: "Amarok crashing in Gnome 3"
date: 2013-07-17
forum: Desktop Environments
---

### Post by MightyTrollzor on 2013-07-17
I have always been using Amarok in in Gnome 3 without Problems but now it won't start anymore when run in Gnome.
It still works fine in KDE 4.X but when i run it in ubuntu the splashscreen appears but plain grey and the player window appears to but also grey.
I tried purging Amarok in Synaptic and reinstalling it but that didn't change anything :(

Running amarok in the terminal with "amarok -d" gives out following:

```
amarok:             [APG::ConstraintNode] new constraint node at 0x396bd50 with parent at 0x3968a70 
amarok:           END__: static APG::PresetPtr APG::Preset::createFromXml(QDomElement&) [Took: 0s] 
amarok:           [APG::PresetModel] creating a new generator preset 
amarok:           BEGIN: static APG::PresetPtr APG::Preset::createFromXml(QDomElement&) 
amarok:             [APG::ConstraintNode] new constraint node at 0x396ea60 with parent at 0x0 
amarok:             BEGIN: ConstraintGroup::ConstraintGroup(QDomElement&, ConstraintNode*) 
amarok:               [APG::ConstraintGroup] "Alle müssen übereinstimmen" 
amarok:             END__: ConstraintGroup::ConstraintGroup(QDomElement&, ConstraintNode*) [Took: 0s] 
amarok:             [APG::ConstraintNode] new constraint node at 0x396ecc0 with parent at 0x396ea60 
amarok:             BEGIN: ConstraintGroup::ConstraintGroup(QDomElement&, ConstraintNode*) 
amarok:               [APG::ConstraintGroup] "Beliebige Übereinstimmung" 
amarok:             END__: ConstraintGroup::ConstraintGroup(QDomElement&, ConstraintNode*) [Took: 0s] 
amarok:             [APG::ConstraintNode] new constraint node at 0x396f520 with parent at 0x396ecc0 
amarok:             [APG::ConstraintNode] new constraint node at 0x3971970 with parent at 0x396ecc0 
amarok:           END__: static APG::PresetPtr APG::Preset::createFromXml(QDomElement&) [Took: 0s] 
amarok:           [APG::PresetModel] creating a new generator preset 
amarok:           BEGIN: static APG::PresetPtr APG::Preset::createFromXml(QDomElement&) 
amarok:             [APG::ConstraintNode] new constraint node at 0x39736a0 with parent at 0x0 
amarok:             BEGIN: ConstraintGroup::ConstraintGroup(QDomElement&, ConstraintNode*) 
amarok:               [APG::ConstraintGroup] "Alle müssen übereinstimmen" 
amarok:             END__: ConstraintGroup::ConstraintGroup(QDomElement&, ConstraintNode*) [Took: 0s] 
amarok:             [APG::ConstraintNode] new constraint node at 0x3974820 with parent at 0x39736a0 
amarok:             BEGIN: ConstraintGroup::ConstraintGroup(QDomElement&, ConstraintNode*) 
amarok:               [APG::ConstraintGroup] "Alle müssen übereinstimmen" 
amarok:             END__: ConstraintGroup::ConstraintGroup(QDomElement&, ConstraintNode*) [Took: 0s] 
amarok:             [APG::ConstraintNode] new constraint node at 0x3974b10 with parent at 0x3974820 
amarok:             [APG::ConstraintNode] new constraint node at 0x3974a50 with parent at 0x3974820 
amarok:           END__: static APG::PresetPtr APG::Preset::createFromXml(QDomElement&) [Took: 0s] 
amarok:           [APG::PresetModel] creating a new generator preset 
amarok:           BEGIN: static APG::PresetPtr APG::Preset::createFromXml(QDomElement&) 
amarok:             [APG::ConstraintNode] new constraint node at 0x3974b80 with parent at 0x0 
amarok:             BEGIN: ConstraintGroup::ConstraintGroup(QDomElement&, ConstraintNode*) 
amarok:               [APG::ConstraintGroup] "Alle müssen übereinstimmen" 
amarok:             END__: ConstraintGroup::ConstraintGroup(QDomElement&, ConstraintNode*) [Took: 0s] 
amarok:             [APG::ConstraintNode] new constraint node at 0x3975330 with parent at 0x3974b80 
amarok:             BEGIN: ConstraintGroup::ConstraintGroup(QDomElement&, ConstraintNode*) 
amarok:               [APG::ConstraintGroup] "Alle müssen übereinstimmen" 
amarok:             END__: ConstraintGroup::ConstraintGroup(QDomElement&, ConstraintNode*) [Took: 0s] 
amarok:             [APG::ConstraintNode] new constraint node at 0x3974a10 with parent at 0x3975330 
amarok:             [APG::ConstraintNode] new constraint node at 0x3974850 with parent at 0x3975330 
amarok:             [APG::ConstraintNode] new constraint node at 0x3977b30 with parent at 0x3975330 
amarok:             [APG::ConstraintNode] new constraint node at 0x39797b0 with parent at 0x3975330 
amarok:           END__: static APG::PresetPtr APG::Preset::createFromXml(QDomElement&) [Took: 0s] 
amarok:           [APG::PresetModel] creating a new generator preset 
amarok:           BEGIN: static APG::PresetPtr APG::Preset::createFromXml(QDomElement&) 
amarok:             [APG::ConstraintNode] new constraint node at 0x397a870 with parent at 0x0 
amarok:             BEGIN: ConstraintGroup::ConstraintGroup(QDomElement&, ConstraintNode*) 
amarok:               [APG::ConstraintGroup] "Alle müssen übereinstimmen" 
amarok:             END__: ConstraintGroup::ConstraintGroup(QDomElement&, ConstraintNode*) [Took: 0s] 
amarok:             [APG::ConstraintNode] new constraint node at 0x397a800 with parent at 0x397a870 
amarok:             BEGIN: ConstraintGroup::ConstraintGroup(QDomElement&, ConstraintNode*) 
amarok:               [APG::ConstraintGroup] "Alle müssen übereinstimmen" 
amarok:             END__: ConstraintGroup::ConstraintGroup(QDomElement&, ConstraintNode*) [Took: 0s] 
amarok:             [APG::ConstraintNode] new constraint node at 0x397ad60 with parent at 0x397a800 
amarok:             BEGIN: ConstraintGroup::ConstraintGroup(QDomElement&, ConstraintNode*) 
amarok:               [APG::ConstraintGroup] "Beliebige Übereinstimmung" 
amarok:             END__: ConstraintGroup::ConstraintGroup(QDomElement&, ConstraintNode*) [Took: 0s] 
amarok:             [APG::ConstraintNode] new constraint node at 0x397ad90 with parent at 0x397ad60 
amarok:             [APG::ConstraintNode] new constraint node at 0x397d800 with parent at 0x397ad60 
amarok:             [APG::ConstraintNode] new constraint node at 0x397f490 with parent at 0x397ad60 
amarok:             [APG::ConstraintNode] new constraint node at 0x3982e70 with parent at 0x397a800 
amarok:             BEGIN: ConstraintGroup::ConstraintGroup(QDomElement&, ConstraintNode*) 
amarok:               [APG::ConstraintGroup] "Alle müssen übereinstimmen" 
amarok:             END__: ConstraintGroup::ConstraintGroup(QDomElement&, ConstraintNode*) [Took: 0s] 
amarok:             [APG::ConstraintNode] new constraint node at 0x3983230 with parent at 0x3982e70 
amarok:             [APG::ConstraintNode] new constraint node at 0x3983090 with parent at 0x3982e70 
amarok:           END__: static APG::PresetPtr APG::Preset::createFromXml(QDomElement&) [Took: 0.001s] 
amarok:           [PlaylistBrowserModel] 0  playlists for category  2 
amarok:           BEGIN: void PlaylistsByProviderProxy::slotProviderAdded(Playlists::PlaylistProvider*, int) 
amarok:           END__: void PlaylistsByProviderProxy::slotProviderAdded(Playlists::PlaylistProvider*, int) [Took: 0s] 
amarok:           BEGIN: PlaylistBrowserNS::PlaylistBrowserView::PlaylistBrowserView(QAbstractItemModel*, QWidget*) 
amarok:           END__: PlaylistBrowserNS::PlaylistBrowserView::PlaylistBrowserView(QAbstractItemModel*, QWidget*) [Took: 0s] 
amarok:           BEGIN: PlaylistTreeItemDelegate::PlaylistTreeItemDelegate(QTreeView*) 
amarok:           END__: PlaylistTreeItemDelegate::PlaylistTreeItemDelegate(QTreeView*) [Took: 0s] 
amarok:         END__: Creating browsers. Please report long start times! [Took: 0.05s] 
amarok:         BEGIN: CoverFetcher::CoverFetcher() 
amarok:         END__: CoverFetcher::CoverFetcher() [Took: 0s] 
amarok:         BEGIN: void MainWindow::restoreLayout() 
amarok:         END__: void MainWindow::restoreLayout() [Took: 0s] 
amarok:       END__: void MainWindow::init() [Took: 0.19s] 
amarok:       BEGIN: QString BrowserCategoryList::navigate(const QString&) 
amarok:         [BrowserCategoryList] target:  "root list/collections" 
amarok:         [BrowserCategoryList] removing own name ( "root list" ) from path 
amarok:         [BrowserCategoryList] looking for child category  "collections" 
amarok:         [BrowserCategoryList] got it! 
amarok:         BEGIN: void BrowserCategoryList::setActiveCategory(BrowserCategory*) 
amarok:         END__: void BrowserCategoryList::setActiveCategory(BrowserCategory*) [Took: 0.001s] 
amarok:         [BrowserCategoryList] child is not a list... 
amarok:       END__: QString BrowserCategoryList::navigate(const QString&) [Took: 0.001s] 
amarok:     END__: MainWindow::MainWindow() [Took: 0.55s] 
QSystemTrayIcon::setVisible: No Icon set
"sni-qt/5957" WARN  20:01:59.438 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 
amarok:     Register object:  true 
amarok:     BEGIN: void App::applySettings(bool) 
amarok:     END__: void App::applySettings(bool) [Took: 0s] 
amarok:     BEGIN: ScriptManager::ScriptManager(QObject*) 
amarok:     END__: ScriptManager::ScriptManager(QObject*) [Took: 0s] 
amarok:     BEGIN: void Amarok::MediaPlayer2Player::volumeChanged(int) 
amarok:       MPRIS2: Queueing up a PropertiesChanged signal 
amarok:     END__: void Amarok::MediaPlayer2Player::volumeChanged(int) [Took: 0s] 
amarok:     MPRIS2: Queueing up a PropertiesChanged signal 
amarok:     BEGIN: void Amarok::OSD::applySettings() 
amarok:     END__: void Amarok::OSD::applySettings() [Took: 0s] 
amarok:   END__: void App::continueInit() [Took: 0.65s] 
amarok: END__: App::App() [Took: 0.65s] 
amarok: BEGIN: virtual int App::newInstance() 
amarok:   BEGIN: static void App::handleCliArgs() 
amarok:   END__: static void App::handleCliArgs() [Took: 0s] 
amarok: END__: virtual int App::newInstance() [Took: 0s] 
amarok: BEGIN: Playlists::PlaylistFilePtr Playlists::loadPlaylistFile(const KUrl&) 
amarok: END__: Playlists::PlaylistFilePtr Playlists::loadPlaylistFile(const KUrl&) [Took: 0s] 
amarok: BEGIN: virtual SyncedPlaylistPtr KConfigSyncRelStore::asSyncedPlaylist(Playlists::PlaylistPtr) 
amarok:   "UIDurl: file:///home/sebi/Musik/Donots%20(2008)%20Coma%20Chameleon/Donots%20-%20Coma%20Chameleon%20(mp3).m3u" 
amarok: END__: virtual SyncedPlaylistPtr KConfigSyncRelStore::asSyncedPlaylist(Playlists::PlaylistPtr) [Took: 0s] 
amarok: BEGIN: void MagnatuneDatabaseWorker::completeJob() 
amarok: END__: void MagnatuneDatabaseWorker::completeJob() [Took: 0s] 
amarok: BEGIN: virtual void Playlist::Model::metadataChanged(Meta::TrackPtr) 
amarok:   [Playlist::Model] Metadata updated for track "French Kiss" 
amarok: END__: virtual void Playlist::Model::metadataChanged(Meta::TrackPtr) [Took: 0s] 
amarok: BEGIN: virtual void Playlist::Model::metadataChanged(Meta::TrackPtr) 
amarok:   [Playlist::Model] Metadata updated for track "Courtesy" 
amarok: END__: virtual void Playlist::Model::metadataChanged(Meta::TrackPtr) [Took: 0s] 
amarok: BEGIN: virtual void Playlist::Model::metadataChanged(Meta::TrackPtr) 
amarok:   [Playlist::Model] Metadata updated for track "Inspire" 
amarok: END__: virtual void Playlist::Model::metadataChanged(Meta::TrackPtr) [Took: 0s] 
amarok: BEGIN: virtual void Playlist::Model::metadataChanged(Meta::TrackPtr) 
amarok:   [Playlist::Model] Metadata updated for track "Focus" 
amarok: END__: virtual void Playlist::Model::metadataChanged(Meta::TrackPtr) [Took: 0s] 
amarok: BEGIN: virtual void Playlist::Model::metadataChanged(Meta::TrackPtr) 
amarok:   [Playlist::Model] Metadata updated for track "Don't you Worry Child" 
amarok: END__: virtual void Playlist::Model::metadataChanged(Meta::TrackPtr) [Took: 0s] 
amarok: BEGIN: virtual void Playlist::Model::metadataChanged(Meta::TrackPtr) 
amarok:   [Playlist::Model] Metadata updated for track "Get Lucky (feat. Pharrell Williams)" 
amarok: END__: virtual void Playlist::Model::metadataChanged(Meta::TrackPtr) [Took: 0s] 
amarok: BEGIN: virtual void Playlist::Model::metadataChanged(Meta::TrackPtr) 
amarok:   [Playlist::Model] Metadata updated for track "Otis" 
amarok: END__: virtual void Playlist::Model::metadataChanged(Meta::TrackPtr) [Took: 0s] 
amarok: BEGIN: void RecentlyPlayedListWidget::startQuery() 
amarok: END__: void RecentlyPlayedListWidget::startQuery() [Took: 0s] 
amarok: [LyricsEngine] no current track 
sebi@Sebi-PC:~$ amarok: BEGIN: void ScriptManager::updateAllScripts() 
amarok:   [ScriptManager] ScriptUpdater: Skipping update check 
amarok:   [ScriptManager] found script: "Generic" "Gnome Multimedia Keys 2" "2.0" ("Amarok2", "python", "python-dbus", "python-gobject") 
amarok:   [ScriptManager] found script: "Generic" "NotifyAmarok" "1.0" ("Amarok2.x", " libnotify-bin", " imagemagick") 
amarok:   [ScriptManager] found script: "Scriptable Service" "Cool Streams" "1.0" ("Amarok2.0") 
amarok:   [ScriptManager] found script: "Lyrics" "LyricWiki" ".2" ("Amarok2.0") 
amarok:   [ScriptManager] found script: "Scriptable Service" "Librivox.org" "1.0" ("Amarok2.0") 
amarok:   [ScriptManager] found script: "Generic" "Amarok Script Console" "1.0" ("Amarok2.0") 
amarok:   [ScriptManager] found script: "Scriptable Service" "Free Music Charts" "1.6.0" ("Amarok2.5") 
amarok:   BEGIN: void ScriptManager::configChanged(bool) 
amarok:     BEGIN: bool ScriptManager::slotRunScript(const QString&, bool) 
amarok:       BEGIN: void ScriptManager::startScriptEngine(const QString&) 
amarok:         [ScriptManager] start script engine: "Free Music Charts" 
amarok:         BEGIN: ScriptableServiceScript::ScriptableServiceScript(QScriptEngine*) 
amarok:         END__: ScriptableServiceScript::ScriptableServiceScript(QScriptEngine*) [Took: 0s] 
amarok:       END__: void ScriptManager::startScriptEngine(const QString&) [Took: 0s] 
amarok:       SCRIPT "Free Music Charts" :  "creating fmc service..." 
amarok:       BEGIN: static QScriptValue ScriptableServiceScript::ScriptableServiceScript_prototype_ctor(QScriptContext*, QScriptEngine*) 
amarok:         BEGIN: bool ScriptableServiceManager::initService(const QString&, int, const QString&, const QString&, bool) 
amarok:           initializing scripted service:  "Free Music Charts" 
amarok:           BEGIN: ServiceBase::ServiceBase(const QString&, ServiceFactory*, bool, const QString&) 
amarok:           END__: ServiceBase::ServiceBase(const QString&, ServiceFactory*, bool, const QString&) [Took: 0.001s] 
amarok:           BEGIN: ScriptableService::ScriptableService(const QString&) 
amarok:             creating ScriptableService  "Free Music Charts" 
amarok:           END__: ScriptableService::ScriptableService(const QString&) [Took: 0s] 
amarok:           BEGIN: void ScriptableService::init(int, const QString&, bool) 
amarok:             BEGIN: Collections::ScriptableServiceCollection::ScriptableServiceCollection(const QString&) 
amarok:             END__: Collections::ScriptableServiceCollection::ScriptableServiceCollection(const QString&) [Took: 0s] 
amarok:           END__: void ScriptableService::init(int, const QString&, bool) [Took: 0s] 
amarok:           emitting scripted service  "Free Music Charts" 
amarok:           BEGIN: void ServiceBrowser::addService(ServiceBase*) 
amarok:             BEGIN: void BrowserCategoryList::childViewChanged() 
amarok:             END__: void BrowserCategoryList::childViewChanged() [Took: 0s] 
amarok:           END__: void ServiceBrowser::addService(ServiceBase*) [Took: 0s] 
amarok:         END__: bool ScriptableServiceManager::initService(const QString&, int, const QString&, const QString&, bool) [Took: 0.002s] 
amarok:       END__: static QScriptValue ScriptableServiceScript::ScriptableServiceScript_prototype_ctor(QScriptContext*, QScriptEngine*) [Took: 0.002s] 
amarok:       SCRIPT "Free Music Charts" :  "done creating fmc service!" 
amarok:       BEGIN: bool AmarokScript::AmarokWindowScript::addMenuAction(QWeakPointer<KMenu>, QString, QString, QString, QString) 
amarok:       END__: bool AmarokScript::AmarokWindowScript::addMenuAction(QWeakPointer<KMenu>, QString, QString, QString, QString) [Took: 0s] 
amarok:       BEGIN: void ScriptableServiceScript::slotCustomize(const QString&) 
amarok:         SCRIPT "Free Music Charts" :  "customizing fmc service" 
amarok:         SCRIPT "Free Music Charts" :  "loading icon: /usr/share/kde4/apps/amarok/scripts/free_music_charts_service/FMCIcon.png" 
amarok:         BEGIN: void ScriptableServiceManager::setIcon(const QString&, const QPixmap&) 
amarok:           service:  "Free Music Charts" 
amarok:         END__: void ScriptableServiceManager::setIcon(const QString&, const QPixmap&) [Took: 0s] 
amarok:       END__: void ScriptableServiceScript::slotCustomize(const QString&) [Took: 0s] 
amarok:     END__: bool ScriptManager::slotRunScript(const QString&, bool) [Took: 0.065s] 
amarok:     BEGIN: bool ScriptManager::slotRunScript(const QString&, bool) 
amarok:       BEGIN: void ScriptManager::startScriptEngine(const QString&) 
amarok:         [ScriptManager] start script engine: "Librivox.org" 
amarok:         BEGIN: ScriptableServiceScript::ScriptableServiceScript(QScriptEngine*) 
amarok:         END__: ScriptableServiceScript::ScriptableServiceScript(QScriptEngine*) [Took: 0s] 
amarok:       END__: void ScriptManager::startScriptEngine(const QString&) [Took: 0s] 
amarok:       SCRIPT "Librivox.org" :  "creating service..." 
amarok:       BEGIN: static QScriptValue ScriptableServiceScript::ScriptableServiceScript_prototype_ctor(QScriptContext*, QScriptEngine*) 
amarok:         BEGIN: bool ScriptableServiceManager::initService(const QString&, int, const QString&, const QString&, bool) 
amarok:           initializing scripted service:  "Librivox.org" 
amarok:           BEGIN: ServiceBase::ServiceBase(const QString&, ServiceFactory*, bool, const QString&) 
amarok:           END__: ServiceBase::ServiceBase(const QString&, ServiceFactory*, bool, const QString&) [Took: 0.001s] 
amarok:           BEGIN: ScriptableService::ScriptableService(const QString&) 
amarok:             creating ScriptableService  "Librivox.org" 
amarok:           END__: ScriptableService::ScriptableService(const QString&) [Took: 0s] 
amarok:           BEGIN: void ScriptableService::init(int, const QString&, bool) 
amarok:             BEGIN: Collections::ScriptableServiceCollection::ScriptableServiceCollection(const QString&) 
amarok:             END__: Collections::ScriptableServiceCollection::ScriptableServiceCollection(const QString&) [Took: 0s] 
amarok:           END__: void ScriptableService::init(int, const QString&, bool) [Took: 0s] 
amarok:           emitting scripted service  "Librivox.org" 
amarok:           BEGIN: void ServiceBrowser::addService(ServiceBase*) 
amarok:             BEGIN: void BrowserCategoryList::childViewChanged() 
amarok:             END__: void BrowserCategoryList::childViewChanged() [Took: 0s] 
amarok:           END__: void ServiceBrowser::addService(ServiceBase*) [Took: 0s] 
amarok:         END__: bool ScriptableServiceManager::initService(const QString&, int, const QString&, const QString&, bool) [Took: 0.002s] 
amarok:       END__: static QScriptValue ScriptableServiceScript::ScriptableServiceScript_prototype_ctor(QScriptContext*, QScriptEngine*) [Took: 0.002s] 
amarok:       SCRIPT "Librivox.org" :  "done creating service!" 
amarok:       BEGIN: void ScriptableServiceScript::slotCustomize(const QString&) 
amarok:         SCRIPT "Librivox.org" :  "customizing Librivox service" 
amarok:         SCRIPT "Librivox.org" :  "loading icon: /usr/share/kde4/apps/amarok/scripts/librivox_service/LibrivoxIcon.png" 
amarok:         BEGIN: void ScriptableServiceManager::setIcon(const QString&, const QPixmap&) 
amarok:           service:  "Librivox.org" 
amarok:         END__: void ScriptableServiceManager::setIcon(const QString&, const QPixmap&) [Took: 0s] 
amarok:       END__: void ScriptableServiceScript::slotCustomize(const QString&) [Took: 0s] 
amarok:     END__: bool ScriptManager::slotRunScript(const QString&, bool) [Took: 0.025s] 
amarok:     BEGIN: bool ScriptManager::slotRunScript(const QString&, bool) 
amarok:       BEGIN: void ScriptManager::startScriptEngine(const QString&) 
amarok:         [ScriptManager] start script engine: "Cool Streams" 
amarok:         BEGIN: ScriptableServiceScript::ScriptableServiceScript(QScriptEngine*) 
amarok:         END__: ScriptableServiceScript::ScriptableServiceScript(QScriptEngine*) [Took: 0s] 
amarok:       END__: void ScriptManager::startScriptEngine(const QString&) [Took: 0s] 
amarok:       BEGIN: static QScriptValue ScriptableServiceScript::ScriptableServiceScript_prototype_ctor(QScriptContext*, QScriptEngine*) 
amarok:         BEGIN: bool ScriptableServiceManager::initService(const QString&, int, const QString&, const QString&, bool) 
amarok:           initializing scripted service:  "Cool Streams" 
amarok:           BEGIN: ServiceBase::ServiceBase(const QString&, ServiceFactory*, bool, const QString&) 
amarok:           END__: ServiceBase::ServiceBase(const QString&, ServiceFactory*, bool, const QString&) [Took: 0s] 
amarok:           BEGIN: ScriptableService::ScriptableService(const QString&) 
amarok:             creating ScriptableService  "Cool Streams" 
amarok:           END__: ScriptableService::ScriptableService(const QString&) [Took: 0s] 
amarok:           BEGIN: void ScriptableService::init(int, const QString&, bool) 
amarok:             BEGIN: Collections::ScriptableServiceCollection::ScriptableServiceCollection(const QString&) 
amarok:             END__: Collections::ScriptableServiceCollection::ScriptableServiceCollection(const QString&) [Took: 0s] 
amarok:           END__: void ScriptableService::init(int, const QString&, bool) [Took: 0s] 
amarok:           emitting scripted service  "Cool Streams" 
amarok:           BEGIN: void ServiceBrowser::addService(ServiceBase*) 
amarok:             BEGIN: void BrowserCategoryList::childViewChanged() 
amarok:             END__: void BrowserCategoryList::childViewChanged() [Took: 0s] 
amarok:           END__: void ServiceBrowser::addService(ServiceBase*) [Took: 0s] 
amarok:         END__: bool ScriptableServiceManager::initService(const QString&, int, const QString&, const QString&, bool) [Took: 0.001s] 
amarok:       END__: static QScriptValue ScriptableServiceScript::ScriptableServiceScript_prototype_ctor(QScriptContext*, QScriptEngine*) [Took: 0.001s] 
amarok:       BEGIN: void ScriptableServiceScript::slotCustomize(const QString&) 
amarok:       END__: void ScriptableServiceScript::slotCustomize(const QString&) [Took: 0s] 
amarok:     END__: bool ScriptManager::slotRunScript(const QString&, bool) [Took: 0.002s] 
amarok:     BEGIN: bool ScriptManager::slotRunScript(const QString&, bool) 
amarok:       BEGIN: void ScriptManager::startScriptEngine(const QString&) 
amarok:         [ScriptManager] start script engine: "LyricWiki" 
amarok:       END__: void ScriptManager::startScriptEngine(const QString&) [Took: 0s] 
amarok:       [ScriptManager] lyrics script started: "LyricWiki" 
amarok:     END__: bool ScriptManager::slotRunScript(const QString&, bool) [Took: 0.006s] 
amarok:     BEGIN: bool ScriptManager::slotRunScript(const QString&, bool) 
amarok:       BEGIN: void ScriptManager::startScriptEngine(const QString&) 
amarok:         [ScriptManager] start script engine: "Gnome Multimedia Keys 2" 
amarok:       END__: void ScriptManager::startScriptEngine(const QString&) [Took: 0s] 
amarok:     END__: bool ScriptManager::slotRunScript(const QString&, bool) [Took: 0.006s] 
amarok:   END__: void ScriptManager::configChanged(bool) [Took: 0.11s] 
amarok: END__: void ScriptManager::updateAllScripts() [Took: 0.11s] 
amarok: BEGIN: void DBusAbstractAdaptor::_m_emitPropertiesChanged() 
amarok: END__: void DBusAbstractAdaptor::_m_emitPropertiesChanged() [Took: 0s] 
amarok: BEGIN: void DBusAbstractAdaptor::_m_emitPropertiesChanged() 
amarok: END__: void DBusAbstractAdaptor::_m_emitPropertiesChanged() [Took: 0s] 
amarok: BEGIN: Playlists::PlaylistFilePtr Playlists::loadPlaylistFile(const KUrl&) 
amarok: END__: Playlists::PlaylistFilePtr Playlists::loadPlaylistFile(const KUrl&) [Took: 0s] 
amarok: BEGIN: virtual SyncedPlaylistPtr KConfigSyncRelStore::asSyncedPlaylist(Playlists::PlaylistPtr) 
amarok:   "UIDurl: file:///home/sebi/Musik/Donots%20(2010)%20The%20Long%20Way%20Home/Donots%20-%20The%20Long%20Way%20Home%20(mp3).m3u" 
amarok: END__: virtual SyncedPlaylistPtr KConfigSyncRelStore::asSyncedPlaylist(Playlists::PlaylistPtr) [Took: 0s] 
amarok: BEGIN: void RecentlyPlayedListWidget::setupTracksData() 
amarok:   BEGIN: void RecentlyPlayedListWidget::updateWidget() 
amarok:   END__: void RecentlyPlayedListWidget::updateWidget() [Took: 0.014s] 
amarok: END__: void RecentlyPlayedListWidget::setupTracksData() [Took: 0.014s] 
amarok: BEGIN: void CollectionTreeItemModelBase::handleSpecialQueryResult(CollectionTreeItem::Type, Collections::QueryMaker*, const DataList&) 
amarok:   [CollectionTreeItemModelBase] Received special data:  0 
amarok: END__: void CollectionTreeItemModelBase::handleSpecialQueryResult(CollectionTreeItem::Type, Collections::QueryMaker*, const DataList&) [Took: 0s] 
amarok: BEGIN: void CollectionTreeItemModelBase::handleSpecialQueryResult(CollectionTreeItem::Type, Collections::QueryMaker*, const DataList&) 
amarok:   [CollectionTreeItemModelBase] Received special data:  24 
amarok:   BEGIN: CollectionTreeItem::CollectionTreeItem(CollectionTreeItem::Type, const DataList&, CollectionTreeItem*, CollectionTreeItemModelBase*) 
amarok:   END__: CollectionTreeItem::CollectionTreeItem(CollectionTreeItem::Type, const DataList&, CollectionTreeItem*, CollectionTreeItemModelBase*) [Took: 0s] 
amarok: END__: void CollectionTreeItemModelBase::handleSpecialQueryResult(CollectionTreeItem::Type, Collections::QueryMaker*, const DataList&) [Took: 0s] 
amarok: [ERROR__] [MySqlStorage] "GREPME MySQLe query failed! (1146) Table 'amarok.jamendo_genre' doesn't exist on SELECT DISTINCT jamendo_genre.id, jamendo_genre.name  FROM  jamendo_genre WHERE 1  GROUP BY jamendo_genre.name;" 
amarok: QModelIndex(-1,-1,0x0,QObject(0x0) ) 
amarok: QModelIndex(-1,-1,0x0,QObject(0x0) ) 
amarok: BEGIN: bool OpmlParser::read(const KUrl&) 
amarok:   BEGIN: bool OpmlParser::read() 
amarok:     BEGIN: bool OpmlParser::continueRead() 
amarok:       BEGIN: void OpmlParser::beginOutline() 
amarok:       END__: void OpmlParser::beginOutline() [Took: 0s] 
amarok:       BEGIN: void OpmlParser::beginOutline() 
amarok:       END__: void OpmlParser::beginOutline() [Took: 0s] 
amarok:       successfuly parsed OPML 
amarok:     END__: bool OpmlParser::continueRead() [Took: 0s] 
amarok:   END__: bool OpmlParser::read() [Took: 0s] 
amarok: END__: bool OpmlParser::read(const KUrl&) [Took: 0s] 
amarok: BEGIN: void WikipediaEnginePrivate::_dataContainerUpdated(const QString&, const Data&) 
amarok:   [WikipediaEngine] "updated preferred wikipedia languages:" ("en") 
amarok: END__: void WikipediaEnginePrivate::_dataContainerUpdated(const QString&, const Data&) [Took: 0s] 
amarok: BEGIN: void WikipediaApplet::dataUpdated(const QString&, const Data&) 
amarok: END__: void WikipediaApplet::dataUpdated(const QString&, const Data&) [Took: 0s] 
amarok: BEGIN: virtual Collections::QueryMaker* Collections::ScriptableServiceQueryMaker::setQueryType(Collections::QueryMaker::QueryType) 
amarok: END__: virtual Collections::QueryMaker* Collections::ScriptableServiceQueryMaker::setQueryType(Collections::QueryMaker::QueryType) [Took: 0s] 
amarok: BEGIN: virtual void Collections::ScriptableServiceQueryMaker::run() 
amarok: END__: virtual void Collections::ScriptableServiceQueryMaker::run() [Took: 0s] 
amarok: BEGIN: virtual Collections::QueryMaker* Collections::ScriptableServiceQueryMaker::setQueryType(Collections::QueryMaker::QueryType) 
amarok: END__: virtual Collections::QueryMaker* Collections::ScriptableServiceQueryMaker::setQueryType(Collections::QueryMaker::QueryType) [Took: 0s] 
amarok: BEGIN: virtual Collections::QueryMaker* Collections::ScriptableServiceQueryMaker::setQueryType(Collections::QueryMaker::QueryType) 
amarok: END__: virtual Collections::QueryMaker* Collections::ScriptableServiceQueryMaker::setQueryType(Collections::QueryMaker::QueryType) [Took: 0s] 
amarok: BEGIN: virtual void Collections::ScriptableServiceQueryMaker::run() 
amarok: END__: virtual void Collections::ScriptableServiceQueryMaker::run() [Took: 0s] 
amarok: BEGIN: virtual void Collections::ScriptableServiceQueryMaker::run() 
amarok: END__: virtual void Collections::ScriptableServiceQueryMaker::run() [Took: 0s] 
amarok: BEGIN: virtual Collections::QueryMaker* Collections::ScriptableServiceQueryMaker::setQueryType(Collections::QueryMaker::QueryType) 
amarok: END__: virtual Collections::QueryMaker* Collections::ScriptableServiceQueryMaker::setQueryType(Collections::QueryMaker::QueryType) [Took: 0s] 
amarok: BEGIN: virtual void Collections::ScriptableServiceQueryMaker::run() 
amarok: END__: virtual void Collections::ScriptableServiceQueryMaker::run() [Took: 0s] 
The program 'amarok' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 2367 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.) 
```

---

### Post by Mamarok on 2013-07-18
FWIW: this only happens if one doesn't run Amarok in KDE, and the error is not in Amarok, but in Qt.

I presume you use 13.04, don't you? You should make sure you have the latest updates, they (Ubuntu devs) screwed up with a bad Qt package, AFAIK this should be fixed by now.

---

### Post by MightyTrollzor on 2013-07-30
I thought it was a problem with Qt but even though i update everytime i start the PC the problem is still there

---

