---
title: "KDE -&gt; System Settings -&gt; Desktop -&gt; Segmentation fault"
date: 2006-11-11
forum: Desktop Environments
---

### Post by Manzabar on 2006-11-11
Running Kubuntu 6.06 with KDE 3.5.5 (updated using [instructions from Kubuntu.org]("http://kubuntu.org/announcements/kde-355.php")) and EasyUbuntu (for Nvidia's drivers & various multimedia codecs).  The initial install and update to KDE 3.5.5 worked fine. However I leave my PC running 24/7 to download various torrents (mostly fansubbed anime) and a couple of weeks back I turned the monitor on to find my background image plain black (it's set to rotate through a large collection of images) and the drive icons previously showning up on my desktop disappeared.  I tried right-clicking on my desktop, but nothing happens.  I tried doing Alt-F2 to bring up the KDE Run Command window, but that also didn't work (neither does selecting that option off the K menu).  I tried going into System Settings to resetup my background options but it crashes after I click on the Desktop option.  I found I can temporarily "fix" the problem by deleting my ~/.kde/ directory, but that's a major pain and the problem came back.  I've done a fair amount of googling but haven't found any permanent solutions, so I'm hoping somebody here can help me out.

I also tried launching systemsettings from Konsole and below is the output I captured doing this:
```
$ systemsettings
kio (KSycoca): Trying to open ksycoca from /var/tmp/kdecache-manzabar/ksycoca
adding Background /usr/share/applications/kde/background.desktop
kutils (KCModuleProxy): [void KCModuleProxy::init(const KCModuleInfo&)]
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
kutils (KCModuleProxy): Module not already loaded, loading module
systemsettings: [void BGMonitorLabel::updateMonitorGeometry()]  Setting geometry to [23,13 - 151x112]
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
adding Screen Saver /usr/share/applications/kde/screensaver.desktop
kutils (KCModuleProxy): [void KCModuleProxy::init(const KCModuleInfo&)]
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
kutils (KCModuleProxy): Module not already loaded, loading module
systemsettings: relPath=System/ScreenSavers/
ScimInputContextPlugin()
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
adding Behavior /usr/share/applications/kde/desktopbehavior.desktop
kutils (KCModuleProxy): [void KCModuleProxy::init(const KCModuleInfo&)]
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
kutils (KCModuleProxy): Module not already loaded, loading module
kio (KTrader): query for ThumbCreator : returning 13 offers
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
adding Multiple Desktops /usr/share/applications/kde/desktop.desktop
kutils (KCModuleProxy): [void KCModuleProxy::init(const KCModuleInfo&)]
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
kutils (KCModuleProxy): Module not already loaded, loading module
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
adding Splash Screen /usr/share/applications/kde/ksplashthememgr.desktop
kutils (KCModuleProxy): [void KCModuleProxy::init(const KCModuleInfo&)]
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
kutils (KCModuleProxy): Module not already loaded, loading module
kio (KTrader): query for KSplash/Plugin : returning 1 offers
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
adding Window Behavior /usr/share/applications/kde/kwinoptions.desktop
kutils (KCModuleProxy): [void KCModuleProxy::init(const KCModuleInfo&)]
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
kutils (KCModuleProxy): Module not already loaded, loading module
systemsettings: the message for i18n should contain a '%n'!  pixels
systemsettings: the message for i18n should contain a '%n'!  pixels
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
adding Window-Specific Settings /usr/share/applications/kde/kwinrules.desktop
kutils (KCModuleProxy): [void KCModuleProxy::init(const KCModuleInfo&)]
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
kutils (KCModuleProxy): Module not already loaded, loading module
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
systemsettings: [void BGMonitorLabel::updateMonitorGeometry()]  Setting geometry to [23,13 - 151x112]
systemsettings: [void BGMonitorLabel::updateMonitorGeometry()]  Setting geometry to [23,13 - 151x112]
kutils (KCModuleProxy): [virtual void KCModuleProxy::showEvent(QShowEvent*)]
kutils (KCModuleProxy): [KCModule* KCModuleProxy::realModule() const]
kio (KTrader): query for KFilePlugin, KFilePlugin : returning 0 offers
kio (KTrader): query for image/jpeg, KFilePlugin : returning 1 offers
KFileMetainfo (plugins): jpeg plugin
Segmentation fault
```

When I sign into my PC as another user, I don't have this problem...  Well, at least when I'm having this problem as my "normal" user and I sign in as another user; the other user's desktop works fine.

If it's any help, here's the hardware I'm running this on:
CPU: AMD AthlonXP 1800+
RAM: 1GB
Mobo: Gigabyte GA-7N400 Pro (NForce 2 Ultra 400 chipset)
Video: NVidia GeForce 5600 with 256MB of Video RAM
Drives: 100GB HDD | Lite-On Combo LTC-4816H | Lite-On DVDRW LDW-411S
NIC: D-Link DWL-AG530 (Wireless PCI)

Any suggestions?

---

