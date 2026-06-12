---
title: "Applications on 17.10 freeze once in a while"
date: 2018-01-17
forum: Desktop Environments
---

### Post by rajesh.bachani on 2018-01-17
Hi Ubuntu users and experts. 
I have recently started using Ubuntu and made a fresh installation of 17.10 (no upgrades) for work. 
I have a few applications installed, but they are pretty standard for development, like Eclipse, Postgres etc. 
Every now and then, there is something that hangs in the system, once it was Eclipse, then the entire Gnome hanged when I opened a basic text editor, this morning the logic screen froze with black screen (no login text field was being shown and system was not responding). 
I have had a tuff time trying to figure out what the problem is. I have got a new disk on my computer for Ubuntu, it's a Samsung SSD 256 GB disk. Pretty standard I suppose, in case it seems like a disk issue. 
Otherwise, I am doubting the gnome-shell package, maybe there are some bugs there, but other than that pretty clueless why it's happening. 

I have some logs here which can be useful. These are just some few lines that are seen just before the restart logs continue. So these were the problems before I had to force restart the machine. 


> 

Jan 12 17:42:49 domain dbus-daemon[1097]: Activating service name='org.gnome.ControlCenter.SearchProvider'Jan 12 17:42:49 domain dbus-daemon[1097]: Activating service name='org.gnome.Calculator.SearchProvider'
Jan 12 17:42:49 domain dbus-daemon[1097]: Activating service name='org.gnome.Calendar'
Jan 12 17:42:49 domain dbus-daemon[1097]: Activating service name='org.gnome.seahorse.Application'
Jan 12 17:42:49 domain dbus-daemon[1097]: Successfully activated service 'org.gnome.Calculator.SearchProvider'
Jan 12 17:42:49 domain dbus-daemon[1097]: Successfully activated service 'org.gnome.ControlCenter.SearchProvider'
Jan 12 17:42:49 domain dbus-daemon[1097]: Successfully activated service 'org.gnome.Calendar'
Jan 12 17:42:49 domain dbus-daemon[1097]: Successfully activated service 'org.gnome.seahorse.Application'
Jan 12 17:42:49 domain nautilus[4461]: g_key_file_load_from_file: assertion 'file != NULL' failed
Jan 12 17:42:49 domain nautilus[4461]: Could not establish a connection to Tracker: Failed to load SPARQL backend: Key file does not have group “DomainOntology”
Jan 12 17:42:51 domain gnome-software[1416]: running search with refine-flags=require-icon with timeout=60 with max-results=20 with search=text on plugin=snap on apps system/package/ubuntu-artful-univer
se/desktop/unity-region-panel.desktop/*,system/package/ubuntu-artful-universe/desktop/SciTE.desktop/*,system/package/ubuntu-artful-universe/desktop/tea.desktop/*,system/package/ubuntu-artful-universe/desk
top/pyprompter.desktop/*,system/package/ubuntu-artful-universe/desktop/pluma.desktop/*,system/package/ubuntu-artful-universe/desktop/me.mitya57.ReText.desktop/*,system/package/ubuntu-artful-universe/deskt
op/mcedit.desktop/*,system/package/ubuntu-artful-universe/desktop/leafpad.desktop/*,system/package/ubuntu-artful-universe/desktop/gprompter.desktop/*,system/package/ubuntu-artful-universe/desktop/emacs25-
lucid.desktop/*,system/package/ubuntu-artful-universe/desktop/sudoku.desktop/*,system/package/ubuntu-artful-universe/desktop/robotfindskitten.desktop/*,system/package/ubuntu-artful-universe/desktop/petris
.desktop/*,system/package/ubuntu-artful-universe/desktop/matanza.desktop/*,system/package/ubuntu-artful-universe/desktop/freesweep.desktop/*,system/package/ubuntu-artful-universe/desktop/blender.desktop/*
,system/package/ubuntu-artful-universe/desktop/webservice-office-zoho-sheet.desktop/*,system/package/ubuntu-artful-universe/desktop/gnumeric.desktop/*,system/package/ubuntu-artful-universe/desktop/gnome-g
enius.desktop/*,system/snap/Snap Store/desktop/xi-tui/* took 1292ms
Jan 12 17:42:51 domain gnome-shell[1142]: error: Failed to launch “Text Editor”: Failed to fork (Cannot allocate memory)
Jan 12 17:43:13 domain hipchat4.desktop[24130]: [16:43:13][virtual bool OnlineStatus::platformSpecificHasInternetConnectivity():38] org.freedesktop.NetworkManager interface is valid
Jan 12 17:43:14 domain hipchat4.desktop[24130]: [16:43:13][void AbstractOnlineStatus::checkOnlineStatus():196] platform online state =  true
Jan 12 17:43:14 domain hipchat4.desktop[24130]: [16:43:14][void AbstractOnlineStatus::doSecondaryCheck(bool):205] Do secondary online check
Jan 12 17:43:14 domain hipchat4.desktop[24130]: [16:43:14][void AbstractOnlineStatus::doSecondaryCheck(bool):218] cloud path
Jan 12 17:43:14 domain hipchat4.desktop[24130]: [16:43:14][void AbstractOnlineStatus::doSecondaryCheck(bool):264] onlineStatusUrl check:  "https://api.hipchat.com/v2/health-check"
Jan 12 17:43:16 domain hipchat4.desktop[24130]: [16:43:15][void AbstractOnlineStatus::handleReplyFinished(QNetworkReply*):126] no errors from onlineStatusCheck
Jan 12 17:43:16 domain hipchat4.desktop[24130]: [16:43:16][void AbstractOnlineStatus::handleOnlineStatusResult(bool):179] handleOnlineStatusResult no change :  true
Jan 12 17:44:31 domain rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="640" x-info="http://www.rsyslog.com"] start


Jan 17 10:26:54 domain gsd-power[29834]: Error setting property 'PowerSaveMode' on interface org.gnome.Mutter.DisplayConfig: Timeout was reached (g-io-error-quark, 24)
Jan 17 10:26:54 domain gsd-power[29834]: Failed to acquire idle monitor proxy: Timeout was reached
Jan 17 10:26:54 domain gsd-power[29834]: Error setting property 'PowerSaveMode' on interface org.gnome.Mutter.DisplayConfig: Timeout was reached (g-io-error-quark, 24)
Jan 17 10:27:04 domain hipchat4.desktop[8518]: [09:27:04][void AbstractOnlineStatus::handleReplyFinished(QNetworkReply*):126] no errors from onlineStatusCheck
Jan 17 10:27:04 domain hipchat4.desktop[8518]: [09:27:04][void AbstractOnlineStatus::handleOnlineStatusResult(bool):179] handleOnlineStatusResult no change :  true
Jan 17 10:29:09 domain rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="612" x-info="http://www.rsyslog.com"] start

Can someone help me with this from the information given, I don't know where to look for more information, but if you need more information just tell me how to get it. Really looking forward to solve this issue. 

Thanks in advance! 
Rajesh.

---

