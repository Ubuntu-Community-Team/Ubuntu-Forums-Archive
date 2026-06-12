---
title: "Long list of messages from KDE applications"
date: 2006-09-12
forum: Desktop Environments
---

### Post by lucascr on 2006-09-12
Dear all,
after I have updated to the last KDE version my kubuntu linux box, when I run from konsole any KDE program (konqueror, kpdf, etc.) I get a neverending list of diagnostic messages. :( 
For example:

```

~/> konqueror &
[1] 8878
~/> kio (KSycoca): Trying to open ksycoca from /var/tmp/kdecache-luca/ksycoca
konqueror: void KonqMisc::createBrowserWindowFromProfile()
konqueror: path=/home/luca/.kde/share/apps/konqueror/profiles/webbrowsing,filename=webbrowsing,url=
kio (KTrader): query for Browser/View : returning 30 offers
libkonq: ## loaded: 731 entries.
kdecore (KConfigSkeleton): Creating KConfigSkeleton (0x815b858)
kdecore (KConfigSkeleton): KConfigSkeleton::readConfig()
ScimInputContextPlugin()
konqueror: KonqMainWindow::enableAllActions false
kparts: found KParts Plugin : /usr/share/apps/konqueror/kpartplugins/googlebar.rc
kparts: found KParts Plugin : /home/luca/.kde/share/apps/konqueror/kpartplugins/searchbar.rc
kparts: load plugin googlebar
kio (KTrader): query for KURIFilter/Plugin : returning 4 offers
kurifilter (plugins): (8878) Keywords Engine: Loading config...
kurifilter (plugins): (8878) Keyword Delimiter: :
kurifilter (plugins): (8878) Default Search Engine: locate
kurifilter (plugins): (8878) Web Shortcuts Enabled: true
kurifilter (plugins): (8878) Verbose: false
kio (KTrader): query for SearchProvider : returning 1 offers
kurifilter (plugins): (8878) user query = 'some keyword'
kurifilter (plugins): (8878) query definition = 'http://www.google.com/search?q=\{@}&ie=UTF-8&oe=UTF-8'
kurifilter (plugins): (8878) Generating substitution map:
kurifilter (plugins): (8878)   map['0'] = 'some keyword'
kurifilter (plugins): (8878)   map['1'] = 'some'
kurifilter (plugins): (8878)   map['2'] = 'keyword'
kurifilter (plugins): (8878) Substitute references:
kurifilter (plugins): (8878)   reference list = '@'
kurifilter (plugins): (8878)   newurl = 'http://www.google.com/search?q=\@&ie=UTF-8&oe=UTF-8'
kurifilter (plugins): (8878)     rest = 'some keyword'
kurifilter (plugins): (8878) substituted query = 'http://www.google.com/search?q=some+keyword&ie=UTF-8&oe=UTF-8'
kparts: MainWindow::createGUI, part=(nil)
kparts: found KParts Plugin : /usr/share/apps/konqueror/kpartplugins/googlebar.rc
kparts: found KParts Plugin : /home/luca/.kde/share/apps/konqueror/kpartplugins/searchbar.rc
konqueror: KonqViewManager::clear
konqueror: Trying to create view for "text/html"
kio (KTrader): query for text/html, Application : returning 4 offers
kio (KTrader): query for text/html, KParts/ReadOnlyPart : returning 2 offers
konqueror: Found requested service khtml
konqueror: Trying to open lib for requested service khtml
konqueror: KonqViewManager::setupView passiveMode=false
konqueror: KonqView::switchView
kparts: found KParts Plugin : /usr/share/apps/khtml/kpartplugins/akregator_konqfeedicon.rc
kparts: found KParts Plugin : /usr/share/apps/khtml/kpartplugins/autorefresh.rc
kparts: found KParts Plugin : /usr/share/apps/khtml/kpartplugins/crashesplugin.rc
kparts: found KParts Plugin : /usr/share/apps/khtml/kpartplugins/kget_plug_in.rc
kparts: found KParts Plugin : /usr/share/apps/khtml/kpartplugins/khtmlkttsd.rc
kparts: found KParts Plugin : /usr/share/apps/khtml/kpartplugins/khtmlsettingsplugin.rc
kparts: found KParts Plugin : /usr/share/apps/khtml/kpartplugins/mf_konqmficon.rc
kparts: found KParts Plugin : /usr/share/apps/khtml/kpartplugins/minitoolsplugin.rc
kparts: found KParts Plugin : /usr/share/apps/khtml/kpartplugins/plugin_babelfish.rc
kparts: found KParts Plugin : /usr/share/apps/khtml/kpartplugins/plugin_domtreeviewer.rc
kparts: found KParts Plugin : /usr/share/apps/khtml/kpartplugins/plugin_rellinks.rc
kparts: found KParts Plugin : /usr/share/apps/khtml/kpartplugins/plugin_validators.rc
kparts: found KParts Plugin : /usr/share/apps/khtml/kpartplugins/plugin_webarchiver.rc
kparts: found KParts Plugin : /usr/share/apps/khtml/kpartplugins/uachangerplugin.rc
kparts: load plugin konqfeedicon
kparts: load plugin khtml_kget
kparts: load plugin khtmlkttsdplugin
konqueror: KHTMLPLuginKTTSD::KHTMLPluginKTTSD: KTrader did not find KTTSD.
kparts: load plugin khtmlsettingsplugin
kparts: load plugin Minitools
kparts: load plugin babelfish
kparts: load plugin webarchiver
kparts: load plugin UserAgentChanger
konqueror: KonqMainWindow::insertChildView 0x831ab00
konqueror: KonqMainWindow::enableAllActions true
konqueror: KonqMainWindow::viewCountChanged
kparts: 0x8130ba8 emitting activePartChanged 0x831b148
konqueror: KonqMainWindow::slotPartActivated 0x831b148 khtml
konqueror: New current view 0x831ab00
kparts: MainWindow::createGUI, part=0x831b148 KHTMLPart
konqueror: KonqMainWindow::setLocationBarURL: url =
konqueror: Part is already active!
konqueror: main() -> no args
konqueror: KonqMainWindow::slotPartActivated 0x831b148 khtml
konqueror: New current view 0x831ab00
kparts: MainWindow::createGUI, part=0x831b148 KHTMLPart
kparts: deactivating GUI for 0x831b148 KHTMLPart
konqueror: KonqMainWindow::setLocationBarURL: url =
konqueror: url /home/luca filtered into file:///home/luca
konqueror: KonqMainWindow::openURL : url = 'file:///home/luca'  serviceType=' req=[typedURL=/home/luca newTabInFront]' view=(nil)
konqueror: trying openView for file:///home/luca (serviceType inode/directory)
konqueror: KonqMainWindow::openView inode/directory file:///home/luca 0x831ab00 req:[typedURL=/home/luca newTabInFront forceAutoEmbed]
konqueror: changeViewMode: serviceType is inode/directory serviceName is konq_detailedlistview current service name is khtml
konqueror: Switching view modes...
konqueror: Trying to create view for "inode/directory"
kio (KTrader): query for inode/directory, Application : returning 1 offers
kio (KTrader): query for inode/directory, KParts/ReadOnlyPart : returning 12 offers
konqueror: Found requested service konq_detailedlistview
konqueror: Trying to open lib for requested service konq_detailedlistview
konqueror: KonqView::switchView
libkonq: The icon theme handles the sizes:(16,32,48,64,128)
libkonq: Using 6 icon sizes.
konqueror: Creating KonqDetailedListViewWidget
kio (KDirLister): +KDirLister
kio (KDirListerCache): +KDirListerCache
kio (KDirWatch): Available methods: Stat, DNotify
konqueror: +KonqBaseListViewWidget
kparts: found KParts Plugin : /home/luca/.kde/share/apps/konqlistview/kpartplugins/dirfilterplugin.rc
kparts: found KParts Plugin : /home/luca/.kde/share/apps/konqlistview/kpartplugins/kimgalleryplugin.rc
kparts: found KParts Plugin : /home/luca/.kde/share/apps/konqlistview/kpartplugins/kremoteencodingplugin.rc
kparts: found KParts Plugin : /home/luca/.kde/share/apps/konqlistview/kpartplugins/kshellcmdplugin.rc
kparts: load plugin DirFilter
kparts: load plugin
kparts: load plugin
kparts: load plugin
konqueror: KonqMainWindow::slotPartChanged
konqueror: KonqMainWindow::setLocationBarURL: url =
kparts: 0x8130ba8 emitting activePartChanged 0x841da10
konqueror: KonqMainWindow::slotPartActivated 0x841da10 konqlistview
konqueror: New current view 0x831ab00
kparts: MainWindow::createGUI, part=0x841da10 KonqListView
kparts: deactivating GUI for 0x831b148 KHTMLPart
konqueror: KonqMainWindow::setLocationBarURL: url =
kparts: Part::~Part 0x831b148
kparts: deleting widget [KHTMLView pointer (0x83606b0) to widget view widget, geometry=819x606+0+0] view widget
konqueror: KonqView::openURL url=file:///home/luca locationBarURL=/home/luca
konqueror: KonqMainWindow::setLocationBarURL: url = /home/luca
konqueror: KonqMainWindow::setCaption(/home/luca)
konqueror: [virtual bool KonqBaseListViewWidget::openURL(const KURL&)] protocol: file url: /home/luca
kdecore (KConfigSkeleton): Creating KConfigSkeleton (0xbfd495a0)
kdecore (KConfigSkeleton): KConfigSkeleton::readConfig()
konqueror: [void KonqBaseListViewWidget::readProtocolConfig(const KURL&)] protocol: file
kio (KDirLister): [virtual bool KDirLister::openURL(const KURL&, bool, bool)] file:///home/luca keep=false reload=false
kio (KDirListerCache): [bool KDirListerCache::listDir(KDirLister*, const KURL&, bool, bool)] 0x8422ee8 url=file:///home/luca keep=false reload=false
kio (KDirListerCache): [void KDirListerCache::stop(KDirLister*)] lister: 0x8422ee8
kio (KDirListerCache): [void KDirListerCache::forgetDirs(KDirLister*)] 0x8422ee8
kio (KDirListerCache): listDir: Entry not in cache or reloaded: file:///home/luca
kio (KDirWatch): Added Dir /home/luca [KDirWatch-1]
kio (KDirWatch):  Setup DNotify (fd 128) for /home/luca
libkonq: ## addToHistory: file:///home/luca Typed URL: /home/luca, Title:
konqueror: KonqMainWindow::openView ok=true bOthersFollowed=false returning true
kio (KDirListerCache): [void KDirListerCache::slotEntries(KIO::Job*, const KIO::UDSEntryList&)] new entries for file:///home/luca
kio: KSambaShare::readSmbConf /etc/samba/smb.conf
kio: KSambaShare: Found path: /tmp/
kio: KSambaShare: Found path: /var/lib/samba/printers/
kio (KDirWatch): Added File /etc/samba/smb.conf [KDirWatch-1]
kio (KDirWatch): Added Dir /etc/samba for /etc/samba/smb.conf
kio (KDirWatch):  Setup DNotify (fd 129) for /etc/samba
kio (KDirWatch): Added File /etc/security/fileshare.conf NotExisting [KDirWatch-1]
kio (KDirWatch): Added Dir /etc/security for /etc/security/fileshare.conf
kio (KDirWatch):  Setup DNotify (fd 130) for /etc/security
kio: KNFSShare: Could not found exports file!
kio (KDirListerCache): [void KDirListerCache::slotResult(KIO::Job*)] finished listing file:///home/luca
konqueror: [virtual void KonqBaseListViewWidget::setComplete()] Update Contents Pos: true
libkonq: ## addToHistory: file:///home/luca Typed URL: /home/luca, Title: luca

```

They are not errors but quite annoying messages from a user perspective, and prevent any further use of the konsole.
How can I solve this? 
Many thanks in advance.

Luca

---

### Post by chavo on 2006-09-12
Run 'kdebugdialog' either in konsole or the Run Command box. Now hit the Deslect All button. You shouldn't have anymore kde debug messages after this. There will be some from xorg, but they don't constantly scroll like the kde ones.

---

### Post by lucascr on 2006-09-12
> **chavo said:**
> Run 'kdebugdialog' either in konsole or the Run Command box. Now hit the Deslect All button. You shouldn't have anymore kde debug messages after this. There will be some from xorg, but they don't constantly scroll like the kde ones.

Many thanks, it perfectly solve the problem.
Ciao,

Luca

---

### Post by chavo on 2006-09-12
No problem. I've been using KDE for over a year now and this one bugged me for quite some time. Maybe I'll file a bug to have them shut off by default.

---

