---
title: "How to configure KDE settings without running KDE (i.e. GNOME)"
date: 2011-07-19
forum: Desktop Environments
---

### Post by fermulator on 2011-07-19
This is a little weird, but consider:

 * Running Ubuntu 10.04
 * GNOME (not KDE)
 * Have Amarok2 installed (which uses KDE stuff)
 * Have this problem where the tooltips in Amarok aren't utilizing gnome's configuration - [http://forum.kde.org/viewtopic.php?f=115&t=96029](http://forum.kde.org/viewtopic.php?f=115&t=96029)

Question:
 * How to modify KDE's "settings" in Ubuntu without actually running KDE?  It's weird.
 * Apparently we need to install "*systemsettings*" and/or "*kcmshell4 colors*"

I installed system settings but it crashes...
```
fermulator@fermmy:~$ systemsettings 
systemsettings(31533)/kdecore (trader) KServiceTypeTrader::defaultOffers: KServiceTypeTrader: serviceType  "SystemSettingsCategory"  not found 
systemsettings(31533)/kdecore (trader) KServiceTypeTrader::defaultOffers: KServiceTypeTrader: serviceType  "SystemSettingsExternalApp"  not found 
systemsettings(31533)/kdecore (services) KServicePrivate::property: Request for unknown property ' "X-KDE-System-Settings-Parent-Category-V2" '
systemsettings(31533)/kdecore (services) KServicePrivate::property: Request for unknown property ' "X-KDE-System-Settings-Parent-Category-V2" '
systemsettings(31533)/kdecore (services) KServicePrivate::property: Request for unknown property ' "X-KDE-System-Settings-Parent-Category-V2" '
systemsettings(31533)/kdecore (services) KServicePrivate::property: Request for unknown property ' "X-KDE-System-Settings-Parent-Category-V2" '
systemsettings(31533)/kdecore (services) KServicePrivate::property: Request for unknown property ' "X-KDE-System-Settings-Parent-Category-V2" '
systemsettings(31533)/kdecore (services) KServicePrivate::property: Request for unknown property ' "X-KDE-System-Settings-Parent-Category-V2" '
systemsettings(31533)/kdecore (services) KServicePrivate::property: Request for unknown property ' "X-KDE-System-Settings-Parent-Category-V2" '
systemsettings(31533)/kdecore (services) KServicePrivate::property: Request for unknown property ' "X-KDE-System-Settings-Parent-Category-V2" '
systemsettings(31533)/kdecore (services) KServicePrivate::property: Request for unknown property ' "X-KDE-System-Settings-Parent-Category-V2" '
systemsettings(31533)/kdecore (services) KServicePrivate::property: Request for unknown property ' "X-KDE-System-Settings-Parent-Category-V2" '
systemsettings(31533)/kdecore (services) KServicePrivate::property: Request for unknown property ' "X-KDE-System-Settings-Parent-Category-V2" '
systemsettings(31533)/kdecore (services) KServicePrivate::property: Request for unknown property ' "X-KDE-System-Settings-Parent-Category-V2" '
systemsettings(31533)/kdecore (services) KServicePrivate::property: Request for unknown property ' "X-KDE-System-Settings-Parent-Category-V2" '
systemsettings(31533)/kdecore (services) KServicePrivate::property: Request for unknown property ' "X-KDE-System-Settings-Parent-Category-V2" '
systemsettings(31533)/kdecore (services) KServicePrivate::property: Request for unknown property ' "X-KDE-System-Settings-Parent-Category-V2" '
systemsettings(31533)/kdecore (trader) KServiceTypeTrader::defaultOffers: KServiceTypeTrader: serviceType  "SystemSettingsView"  not found 
fermulator@fermmy:~$ KCrash: Application 'systemsettings' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/fermulator/.kde/socket-fermmy/kdeinit4__0

```


And, kcmshell4 doesn't have the "colors" module
```
fermulator@fermmy:~$ kcmshell4 --list
The following modules are available:
kcm_kdnssd             - Configure service discovery
spellchecking          - Configure the spell checker
kcm_phonon             - Sound and Video Configuration
kcmnotify              - System Notification Configuration
kcmcgi                 - Configure the CGI KIO slave
kcm_attica             - Manage Social Desktop Providers
emoticons              - Emoticons Themes Manager
filetypes              - Configure file associations
kcm_nepomuk            - Nepomuk/Strigi Server Configuration
kcmtrash               - Configure trash settings
audiocd                - Audiocd IO Slave Configuration
kcm_ssl                - SSL Versions and Certificates
componentchooser       - Choose the default components for various services
device_automounter_kcm - Configure automatic handling of removable storage media
kcmkded                - KDE Services Configuration
language               - Language, numeric, and time settings for your particular region
icons                  - Customize KDE Icons
```

---

