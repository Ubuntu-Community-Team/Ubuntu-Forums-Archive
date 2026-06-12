---
title: "GNOME desktop hangs at login screen background (can't find gnome-wm/panel provider)"
date: 2010-06-28
forum: Desktop Environments
---

### Post by JBDynamics on 2010-06-28
I am running the latest version of Lucid Lynx 10.04 LTS AMD64 on a VMware workstation 7.1 in Windows 7 x64 Ultimate. I have a 2.6.32-23-generic kernel. I have all updates available in the lucid and lucid-updates US repositories. I only have the lucid and lucid-updates US main restricted multiverse universe repositories in my sources.list (no lucid-proposed or lucid-backports). So there is no beta packages installed.

Basically, I installed a bunch of applications (almost the same list as I use on 3 other non-virtual Ubuntu 10.04 machines) and they all work fine. I just can't determine what application or setting has caused the GNOME desktop to fail to start. Kubuntu (KDE) desktop works just fine (I can even use a composition engine unlike Ubuntu in which Visual Effects do not work in VMware 7.1). Basically, GNOME hangs at the login background screen and does nothing. It is similar to this problem: [http://ubuntuforums.org/archive/index.php/t-1502665.html](http://ubuntuforums.org/archive/index.php/t-1502665.html). Although no-one solved that problem.

I have the latest VMware tools installed and I have the lastest release of VMware workstation 7.1. 

Here is a gnome-session --debug log. Let me know if I should supply any other logs.

gnome-session[4033]: DEBUG(+): Enabling debugging
gnome-session[4033]: DEBUG(+): GsmXsmpServer: SESSION_MANAGER=local/ubuntu:@/tmp/.ICE-unix/4033,unix/ubuntu:/tmp/.ICE-unix/4033

gnome-session[4033]: DEBUG(+): GsmManager: setting client store 0x6b9860
gnome-session[4033]: DEBUG(+): GdmSignalHandler: Adding handler 1: signum=4 (nil)
gnome-session[4033]: DEBUG(+): GdmSignalHandler: Registering for 4 signals
gnome-session[4033]: DEBUG(+): GdmSignalHandler: Adding handler 2: signum=7 (nil)
gnome-session[4033]: DEBUG(+): GdmSignalHandler: Registering for 7 signals
gnome-session[4033]: DEBUG(+): GdmSignalHandler: Adding handler 3: signum=6 (nil)
gnome-session[4033]: DEBUG(+): GdmSignalHandler: Registering for 6 signals
gnome-session[4033]: DEBUG(+): GdmSignalHandler: Adding handler 4: signum=5 (nil)
gnome-session[4033]: DEBUG(+): GdmSignalHandler: Registering for 5 signals
gnome-session[4033]: DEBUG(+): GdmSignalHandler: Adding handler 5: signum=8 0x41b360
gnome-session[4033]: DEBUG(+): GdmSignalHandler: Registering for 8 signals
gnome-session[4033]: DEBUG(+): GdmSignalHandler: Adding handler 6: signum=1 0x41b360
gnome-session[4033]: DEBUG(+): GdmSignalHandler: Registering for 1 signals
gnome-session[4033]: DEBUG(+): GdmSignalHandler: Adding handler 7: signum=10 0x41b360
gnome-session[4033]: DEBUG(+): GdmSignalHandler: Registering for 10 signals
gnome-session[4033]: DEBUG(+): GdmSignalHandler: Adding handler 8: signum=15 0x41b360
gnome-session[4033]: DEBUG(+): GdmSignalHandler: Registering for 15 signals
gnome-session[4033]: DEBUG(+): GdmSignalHandler: Adding handler 9: signum=2 0x41b360
gnome-session[4033]: DEBUG(+): GdmSignalHandler: Registering for 2 signals
gnome-session[4033]: DEBUG(+): GsmManager: *** Adding autostart apps for /home/admin/.config/gnome-session/saved-session
gnome-session[4033]: DEBUG(+): GsmManager: *** Adding autostart apps for /home/admin/.config/autostart
gnome-session[4033]: DEBUG(+): GsmManager: *** Adding autostart apps for gnome/autostart
gnome-session[4033]: DEBUG(+): GsmManager: *** Adding autostart apps for gnome/autostart
gnome-session[4033]: DEBUG(+): GsmManager: *** Adding autostart apps for /etc/xdg/xdg-xterm/autostart
gnome-session[4033]: DEBUG(+): GsmManager: *** Adding autostart apps for autostart
gnome-session[4033]: DEBUG(+): GsmManager: *** Adding autostart apps for autostart
gnome-session[4033]: DEBUG(+): main: *** Adding default apps
gnome-session[4033]: DEBUG(+): GsmUtil: Looking for file 'gnome-settings-daemon.desktop'
gnome-session[4033]: DEBUG(+): GsmUtil: Looking in '/home/admin/.local/share/applications'
gnome-session[4033]: DEBUG(+): GsmUtil: Looking in 'applications'
gnome-session[4033]: DEBUG(+): GsmUtil: Looking in 'applications'
gnome-session[4033]: DEBUG(+): main: *** Adding required apps
gnome-session[4033]: DEBUG(+): main: /desktop/gnome/session/required_components/windowmanager looking for component: 'gnome-wm'
gnome-session[4033]: DEBUG(+): GsmUtil: Looking for file 'gnome-wm.desktop'
gnome-session[4033]: DEBUG(+): GsmUtil: Looking in '/home/admin/.local/share/applications'
gnome-session[4033]: DEBUG(+): GsmUtil: Looking in 'applications'
gnome-session[4033]: DEBUG(+): GsmUtil: Looking in 'applications'
gnome-session[4033]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager'
gnome-session[4033]: DEBUG(+): main: /desktop/gnome/session/required_components/panel looking for component: 'gnome-panel'
gnome-session[4033]: DEBUG(+): GsmUtil: Looking for file 'gnome-panel.desktop'
gnome-session[4033]: DEBUG(+): GsmUtil: Looking in '/home/admin/.local/share/applications'
gnome-session[4033]: DEBUG(+): GsmUtil: Looking in 'applications'
gnome-session[4033]: DEBUG(+): GsmUtil: Looking in 'applications'
gnome-session[4033]: WARNING: Unable to find provider 'gnome-panel' of required component 'panel'
gnome-session[4033]: DEBUG(+): main: /desktop/gnome/session/required_components/filemanager looking for component: 'nautilus'
gnome-session[4033]: DEBUG(+): GsmUtil: Looking for file 'nautilus.desktop'
gnome-session[4033]: DEBUG(+): GsmUtil: Looking in '/home/admin/.local/share/applications'
gnome-session[4033]: DEBUG(+): GsmUtil: Looking in 'applications'
gnome-session[4033]: DEBUG(+): GsmUtil: Looking in 'applications'
gnome-session[4033]: WARNING: Unable to find provider 'nautilus' of required component 'filemanager'
gnome-session[4033]: DEBUG(+): main: *** Done adding required apps
gnome-session[4033]: DEBUG(+): GsmManager: GSM starting to manage
gnome-session[4033]: DEBUG(+): GsmManager: App startup summary
gnome-session[4033]: DEBUG(+): GsmManager: Phase INITIALIZATION
gnome-session[4033]: DEBUG(+): GsmManager: Phase WINDOW_MANAGER
gnome-session[4033]: DEBUG(+): GsmManager: Phase PANEL
gnome-session[4033]: DEBUG(+): GsmManager: Phase DESKTOP
gnome-session[4033]: DEBUG(+): GsmManager: Phase APPLICATION
gnome-session[4033]: DEBUG(+): GsmManager: starting phase INITIALIZATION

gnome-session[4033]: DEBUG(+): GsmManager: ending phase INITIALIZATION

gnome-session[4033]: DEBUG(+): GsmManager: starting phase WINDOW_MANAGER

gnome-session[4033]: DEBUG(+): GsmManager: ending phase WINDOW_MANAGER

gnome-session[4033]: DEBUG(+): GsmManager: starting phase PANEL

gnome-session[4033]: DEBUG(+): GsmManager: ending phase PANEL

gnome-session[4033]: DEBUG(+): GsmManager: starting phase DESKTOP

gnome-session[4033]: DEBUG(+): GsmManager: ending phase DESKTOP

gnome-session[4033]: DEBUG(+): GsmManager: starting phase APPLICATION

gnome-session[4033]: DEBUG(+): GsmManager: ending phase APPLICATION

gnome-session[4033]: DEBUG(+): GsmManager: starting phase RUNNING

gnome-session[4033]: DEBUG(+): GsmPresence: adding idle watch
gnome-session[4033]: DEBUG(+): GSIdleMonitor: creating new alarm for positive transition wait=300000
gnome-session[4033]: DEBUG(+): GSIdleMonitor: creating new alarm for negative transition wait=300000

---

