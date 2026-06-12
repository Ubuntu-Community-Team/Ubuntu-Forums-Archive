---
title: "AbiWord opens on boot"
date: 2015-07-10
forum: Desktop Environments
---

### Post by Jonners59 on 2015-07-10
For some reason AbiWord opens on boot.  It is NOT in the session start up.  Any ideas, please how to stop it.

---

### Post by Vladlenin5000 on 2015-07-10
[https://forum.xfce.org/viewtopic.php?id=9006](https://forum.xfce.org/viewtopic.php?id=9006)

---

### Post by Bucky Ball on 2015-07-10
You have, or had, 'Save Session' ticked probably.

Easy to boot the computer> Close Abiword> go for a restart> on the selection of 'Logout' 'Reboot' 'Shutdown' etc, make sure you have the 'Save Sessions' ticked, with no apps open on machine.

Hit restart.

Once at the desktop, open the logout GUI again and untick the 'Save Sessions' box. If you don't restart immediately, make sure that box is still unticked when you restart next time else it will save whatever you have open on the desktop, and that might be more than just Abiword. 

Let us know if that worked. :)

---

### Post by Jonners59 on 2015-07-11
> **Vladlenin5000 said:**
> [https://forum.xfce.org/viewtopic.php?id=9006](https://forum.xfce.org/viewtopic.php?id=9006)
Thank you for this.  Didn't realise that this is a known bug/issue for so long, 2012!!!  Followed the links on the fxce forum.
[https://forum.xfce.org/viewtopic.php?id=8082](https://forum.xfce.org/viewtopic.php?id=8082)
[https://forum.xfce.org/viewtopic.php?id=9006](https://forum.xfce.org/viewtopic.php?id=9006)

I shall try the suggestion:
- Shutdown the computer
- Boot up but do not log in, instead go to the first tty (Ctrl+Alt+F1) and run:
```
cd .cache rm -rf sessions
```

- Go back to the gui (Ctrl+Alt+F7) and log in
- Leave a few windows/applictions open.
- Click on the log out button, make sure "Save sessions for future logins" is unchecked, and shut down.
- Start up the computer and login.

Do the applications re-appear?

And  if the applications still autostart, please post back the contents of  your ~/.cache/upstart/startxfce4.log.gz log file. Its compressed. so to  view it, you'll need to:

```
zcat ~/.cache/upstart/startxfce4.log.1.gz
```

> **Bucky Ball said:**
> You have, or had, 'Save Session' ticked probably.

Easy to boot the computer> Close Abiword> go for a restart> on  the selection of 'Logout' 'Reboot' 'Shutdown' etc, make sure you have  the 'Save Sessions' ticked, with no apps open on machine.

Hit restart.

Once at the desktop, open the logout GUI again and untick the 'Save  Sessions' box. If you don't restart immediately, make sure that box is  still unticked when you restart next time else it will save whatever you  have open on the desktop, and that might be more than just Abiword. 

Let us know if that worked. [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

Thank you, but, done all that and more.  This is a bigger issue as above.

---

### Post by coffeecat on 2015-07-11
I saw this when I installed the Lubuntu desktop to an Ubuntu installation. #10 in this Launchpad bug worked for me:

[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1432271](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1432271)

---

### Post by Jonners59 on 2015-07-13
> **Bucky Ball said:**
> You have, or had, 'Save Session' ticked probably.

Easy to boot the computer> Close Abiword> go for a restart> on the selection of 'Logout' 'Reboot' 'Shutdown' etc, make sure you have the 'Save Sessions' ticked, with no apps open on machine.

Hit restart.

Once at the desktop, open the logout GUI again and untick the 'Save Sessions' box. If you don't restart immediately, make sure that box is still unticked when you restart next time else it will save whatever you have open on the desktop, and that might be more than just Abiword. 

Let us know if that worked. :)

OK, tried this.  Didn't work.

> **coffeecat said:**
> I saw this when I installed the Lubuntu  desktop to an Ubuntu installation. #10 in this Launchpad bug worked for  me:

[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1432271](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1432271)

I also tried the bug link, and that didn't work either.

```
sudo rm -f /usr/share/dbus-1/services/org.freedesktop.Telepathy.Client.AbiCollab.service
```

Log attached.
[PHP]failed: Connection timed out. 
wget: unable to resolve host address &#8216;clients2.google.com&#8217; 
  
Failed to get crash dump id. 
Report Id:  
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
 
(xfsettingsd:1647): GLib-GObject-WARNING **: g_object_notify: object class 'UpClient' has no property named 'g-name-owner' 
kded4: Fatal IO error: client killed 
klauncher: Exiting on signal 15 
klauncher: Exiting on signal 1 
[1655:2293:0713/073615:ERROR:channel.cc(300)] RawChannel read error (connection broken) 
wineserver crashed, please enable coredumps (ulimit -c unlimited) and restart. 
xfwm4: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0. 
xfdesktop: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0. 
[1655:1655:0713/073615:ERROR:chrome_browser_main_extra_parts_x11.cc(56)] X IO error received (X server probably went away) 
[1655:2293:0713/073615:ERROR:channel.cc(300)] RawChannel read error (connection broken) 
[1655:2293:0713/073615:ERROR:channel.cc(300)] RawChannel read error (connection broken) 
[1655:1655:0713/073615:ERROR:zygote_host_impl_linux.cc(541)] Failed to send GetTerminationStatus message to zygote 
[1655:2293:0713/073615:ERROR:channel.cc(300)] RawChannel read error (connection broken) 
[1655:1655:0713/073615:ERROR:zygote_host_impl_linux.cc(541)] Failed to send GetTerminationStatus message to zygote 
[1655:1655:0713/073615:ERROR:zygote_host_impl_linux.cc(541)] Failed to send GetTerminationStatus message to zygote 
[1655:1655:0713/073615:ERROR:zygote_host_impl_linux.cc(541)] Failed to send GetTerminationStatus message to zygote 
[1655:1655:0713/073615:ERROR:zygote_host_impl_linux.cc(541)] Failed to send GetTerminationStatus message to zygote 
[1655:1655:0713/073615:ERROR:zygote_host_impl_linux.cc(541)] Failed to send GetTerminationStatus message to zygote 
[1655:1655:0713/073615:ERROR:zygote_host_impl_linux.cc(541)] Failed to send GetTerminationStatus message to zygote 
[1655:1655:0713/073615:ERROR:zygote_host_impl_linux.cc(541)] Failed to send GetTerminationStatus message to zygote 
[1655:1655:0713/073615:ERROR:zygote_host_impl_linux.cc(541)] Failed to send GetTerminationStatus message to zygote 
[1655:1655:0713/073615:ERROR:zygote_host_impl_linux.cc(541)] Failed to send GetTerminationStatus message to zygote 
[1655:1655:0713/073615:ERROR:zygote_host_impl_linux.cc(541)] Failed to send GetTerminationStatus message to zygote 
/usr/bin/startxfce4: X server already running on display :0 
xfce4-session: GNOME compatibility is enabled and gnome-keyring-daemon is found on the system. Skipping gpg/ssh-agent startup. 
 
(xfce4-session:1508): xfce4-session-WARNING **: xfsm_manager_load_session: Something wrong with /home/baronipc/.cache/sessions/xfce4-session-Baroni-PC:0, Does it exist? Permissions issue? 
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString) 
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave. 
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave. 
kbuildsycoca4 running... 
kbuildsycoca4(1662) KBuildSycoca::checkTimestamps: checking file timestamps 
kbuildsycoca4(1662) KBuildSycoca::checkTimestamps: timestamps check ok 
kbuildsycoca4(1662) kdemain: Emitting notifyDatabaseChanged () 
 
 
(evolution:1682): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files 
Starting Dropbox...Loading configuration plugins 
 
(xfsettingsd:1676): xfsettingsd-CRITICAL **: Stored Xfconf properties disable all outputs, aborting. 
blueman-applet version 1.99.alpha1 starting 
Warning - SolarTZ module not found 
CachingBackend: Loading instances from cache 
CachingBackend: Loading <Clock1> 
theme_name='vintage' 
show_date='True' 
is_widget='True' 
is_dragged='False' 
timezone='Europe/London' 
face_text='BERLIN' 
scale='2.0' 
is_sticky='True' 
face_text_y='59' 
face_text_x='38' 
skip_pager='False' 
keep_above='False' 
lock_position='True' 
hour_format='12' 
draw_buttons='False' 
opacity='1.0' 
face_text_color='0.10140,0.09215,0.09215,0.29999' 
keep_below='True' 
longitude='0.0' 
y='26' 
x='1594' 
skip_taskbar='False' 
time_offset='0.0' 
xfsettingsd: Another clipboard manager is already running. 
daemon already started 
Using GConf config backend 
Using GConf config backend 
Traceback (most recent call last): 
  File "/usr/bin/blueman-applet", line 110, in <module> 
    BluemanApplet() 
  File "/usr/bin/blueman-applet", line 53, in __init__ 
    self.Plugins.Load() 
  File "/usr/lib/python2.7/dist-packages/blueman/main/PluginManager.py", line 84, in Load 
    __import__(self.module_path.__name__ + ".%s" % plugin, None, None, []) 
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/applet/AuthAgent.py", line 3, in <module> 
    import blueman.main.applet.BluezAgent as BluezAgent 
  File "/usr/lib/python2.7/dist-packages/blueman/main/applet/BluezAgent.py", line 15, in <module> 
    from blueman.bluez.Agent import Agent, AgentMethod 
  File "/usr/lib/python2.7/dist-packages/blueman/bluez/Agent.py", line 42, in <module> 
    class Agent(dbus.service.Object): 
  File "/usr/lib/python2.7/dist-packages/blueman/bluez/Agent.py", line 50, in Agent 
    @AgentMethod 
  File "/usr/lib/python2.7/dist-packages/blueman/bluez/Agent.py", line 32, in AgentMethod 
    if BlueZInterface.get_interface_version()[0] < 5: 
  File "/usr/lib/python2.7/dist-packages/blueman/bluez/BlueZInterface.py", line 11, in get_interface_version 
    object = dbus.SystemBus().get_object('org.bluez', '/') 
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 241, in get_object 
    follow_name_owner_changes=follow_name_owner_changes) 
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 248, in __init__ 
    self._named_service = conn.activate_name_owner(bus_name) 
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 180, in activate_name_owner 
    self.start_service_by_name(bus_name) 
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 278, in start_service_by_name 
    'su', (bus_name, flags))) 
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking 
    message, timeout) 
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.bluez was not provided by any .service files 
 
(xfce4-notes:1693): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed 
 
(xfwm4:1667): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed 
No global tempdir found, creating new one. 
Temp directory /tmp/screenlets created. 
Creating new entry for ClockScreenlet in /tmp/screenlets/screenlets.baronipc.running 
[1759:1931:0713/073812:ERROR:nss_util.cc(819)] After loading Root Certs, loaded==false: NSS error code: -8018 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
 
(polkit-gnome-authentication-agent-1:1765): GLib-CRITICAL **: g_variant_new_string: assertion 'string != NULL' failed 
 
(polkit-gnome-authentication-agent-1:1765): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files 
nm-applet-Message: using fallback from indicator to GtkStatusIcon 
 
(process:1680): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
kded(1656) ContactRequestHandler::onNewAccountAdded:  
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
CachingBackend: Loading instances from cache 
CachingBackend: Loading <FolderView1> 
opacity='1.0' 
show_back='False' 
scale='1.0' 
sb_row='7' 
theme_name='default' 
is_sticky='True' 
banner_size='29' 
is_widget='True' 
height='222' 
width='425' 
keep_above='False' 
lock_position='True' 
is_dragged='False' 
keep_below='True' 
icon_size='29' 
x='80' 
skip_taskbar='True' 
y='823' 
folder_path='/home/baronipc/Desktop/Documents/Documents/Dropbox/Documents/CV' 
CachingBackend: Loading <FolderView4> 
opacity='1.0' 
icon_size='29' 
scale='1.0' 
theme_name='default' 
is_sticky='True' 
banner_size='29' 
is_widget='True' 
height='164' 
width='309' 
keep_above='False' 
is_dragged='False' 
keep_below='True' 
y='870' 
x='1496' 
skip_taskbar='True' 
expand2='Expand/Adjust to icons' 
full_path='True' 
folder_path='/home/baronipc/Desktop/Documents/Documents' 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
[1684:1684:0713/073815:ERROR:nss_util.cc(819)] After loading Root Certs, loaded==false: NSS error code: -8018 
[1949:1949:0713/073815:ERROR:nss_util.cc(819)] After loading Root Certs, loaded==false: NSS error code: -8018 
[1751:1751:0713/073815:ERROR:nss_util.cc(819)] After loading Root Certs, loaded==false: NSS error code: -8018 
[1751:1751:0713/073816:ERROR:process_singleton_posix.cc(277)] Failed to create /home/baronipc/.config/chromium/SingletonLock: File exists 
Found a running session of FolderView, adding new instance by service. 
Error in screenlets.services.get_service_by_name: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.FolderView was not provided by any .service files 
Screenlet has already been added to /tmp/screenlets/screenlets.baronipc.running 
[1949:1949:0713/073817:ERROR:url_pattern_set.cc(240)] Invalid url pattern: chrome://print/* 
[1684:1684:0713/073817:ERROR:url_pattern_set.cc(240)] Invalid url pattern: chrome://print/* 
[1949:2119:0713/073817:ERROR:connection.cc(1060)] History sqlite error 5, errno 0: database is locked, sql: DELETE FROM meta WHERE key=? 
[1684:2118:0713/073817:ERROR:connection.cc(1060)] History sqlite error 5, errno 0: database is locked, sql: COMMIT 
[1684:2134:0713/073818:ERROR:sandbox_origin_database.cc(195)] SandboxOriginDatabase failed at: Init@../../storage/browser/fileapi/sandbox_origin_database.cc:94 with error: IO error: /home/baronipc/.config/chromium/Default/File System/Origins/LOCK: No further details. (ChromeMethodBFE: 15::LockFile::1) 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
Created new window in existing browser session. 
[1684:1684:0713/073819:ERROR:desktop_window_tree_host_x11.cc(811)] Not implemented reached in virtual void views::DesktopWindowTreeHostX11::InitModalType(ui::ModalType) 
Dropbox isn't running! 
Done! 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
[1734:1734:0713/073828:ERROR:nss_util.cc(819)] After loading Root Certs, loaded==false: NSS error code: -8018 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
** (xfdesktop:1675): WARNING **: Unable to rename temp file to /home/baronipc/.config/xfce4/desktop/icons.screen0-1877x1064.rc: Operation not permitted 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
[1734:1734:0713/073835:ERROR:url_pattern_set.cc(240)] Invalid url pattern: chrome://print/* 
ERROR:dbus.proxies:Introspect error on :1.57:/org/screenlets/ScreenletsDaemon: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. 
Fontconfig error: Cannot load default config file 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
[17:17:0713/073838:ERROR:resource_request_policy.cc(57)] Denying load of chrome-extension://apdfllckaahabafndbhieahigkjlhalf/page_embed_script.js from hosted app. 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
ERROR:dbus.proxies:Introspect error on :1.57:/org/screenlets/ScreenletsDaemon: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. 
Loading instances in: /home/baronipc/.config/screenlets/Clock/default/ 
Loaded config from: Clock1.iniLoading instances in: /home/baronipc/.config/screenlets/FolderView/default/ 
 
Loaded config from: FolderView1.ini 
Traceback (most recent call last): 
  File "/usr/share/screenlets/screenlets-pack-all/FolderView/FolderViewScreenlet.py", line 1392, in <module> 
    screenlets.session.create_session(FolderViewScreenlet) 
  File "/usr/lib/pymodules/python2.7/screenlets/session.py", line 480, in create_session 
Traceback (most recent call last): 
  File "/usr/share/screenlets/screenlets-pack-all/Clock/ClockScreenlet.py", line 553, in <module> 
    screenlets.session.create_session(ClockScreenlet) 
  File "/usr/lib/pymodules/python2.7/screenlets/session.py", line 480, in create_session 
        session.start() 
session.start() 
  File "/usr/lib/pymodules/python2.7/screenlets/session.py", line 245, in start 
  File "/usr/lib/pymodules/python2.7/screenlets/session.py", line 245, in start 
        if self.__load_instances(): 
if self.__load_instances(): 
  File "/usr/lib/pymodules/python2.7/screenlets/session.py", line 399, in __load_instances 
  File "/usr/lib/pymodules/python2.7/screenlets/session.py", line 399, in __load_instances 
    sl = self.create_instance(id=filename[:-4], enable_saving=False) 
    sl = self.create_instance(id=filename[:-4], enable_saving=False) 
  File "/usr/lib/pymodules/python2.7/screenlets/session.py", line 151, in create_instance 
  File "/usr/lib/pymodules/python2.7/screenlets/session.py", line 151, in create_instance 
    sl = self.screenlet(id=id, session=self, **keyword_args) 
    sl = self.screenlet(id=id, session=self, **keyword_args) 
  File "/usr/share/screenlets/screenlets-pack-all/FolderView/FolderViewScreenlet.py", line 133, in __init__ 
  File "/usr/share/screenlets/screenlets-pack-all/Clock/ClockScreenlet.py", line 156, in __init__ 
    screenlets.Screenlet.__init__(self, width=200, height=200,ask_on_option_override=False, drag_drop=True,resize_on_scroll= False, **keyword_args) 
      File "/usr/lib/pymodules/python2.7/screenlets/__init__.py", line 837, in __init__ 
**keyword_args) 
  File "/usr/lib/pymodules/python2.7/screenlets/__init__.py", line 837, in __init__ 
        self.load_buttons(None) 
self.load_buttons(None) 
  File "/usr/lib/pymodules/python2.7/screenlets/__init__.py", line 1302, in load_buttons 
  File "/usr/lib/pymodules/python2.7/screenlets/__init__.py", line 1302, in load_buttons 
        self.closeb = self.gtk_icon_theme.load_icon ("gtk-close", 16, 0) 
self.closeb = self.gtk_icon_theme.load_icon ("gtk-close", 16, 0) 
glibglib.GError.: Icon 'gtk-close' not present in themeGError:  
Icon 'gtk-close' not present in theme 
[1684:1684:0713/073843:ERROR:extension_downloader.cc(695)] Invalid URL: '' for extension diclpocmbllagclnooehpmpjbccmmnpi 
[1684:1684:0713/073843:ERROR:extension_downloader.cc(695)] Invalid URL: '' for extension fkojlkbedcenfecoecpbemjpjonboaal 
[36:36:0713/073844:ERROR:dispatcher.cc(256)] Extension "chrome://chrome-signin/" not found 
[36:36:0713/073844:ERROR:dispatcher.cc(256)] Extension "chrome://chrome-signin/" not found 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
[36:36:0713/073846:ERROR:dispatcher.cc(256)] Extension "chrome://chrome-signin/" not found 
[36:36:0713/073846:ERROR:dispatcher.cc(256)] Extension "chrome://chrome-signin/" not found 
[36:36:0713/073846:ERROR:dispatcher.cc(256)] Extension "chrome://chrome-signin/" not found 
[36:36:0713/073846:ERROR:dispatcher.cc(256)] Extension "chrome://chrome-signin/" not found 
console.error: integratedinbox:  
  DEPRECATED: The widget module is deprecated.  Please consider using the sdk/ui module instead. 
Traceback (most recent call last): 
  File "resource://services-sync/status.js", line 36, in this.Status._authManager 
    cb.wait(); 
  File "resource://services-common/async.js", line 145, in makeSpinningCallback/callback.wait 
    callback.wait = () => Async.waitForSyncCallback(cb); 
  File "resource://services-common/async.js", line 102, in waitForSyncCallback 
    thread.processNextEvent(true); 
  File "resource://gre/modules/Promise-backend.js", line 688, in this.PromiseWalker.scheduleWalkerLoop/< 
    DOMPromise.resolve().then(() => this.walkerLoop()); 
  File "resource://gre/modules/Promise-backend.js", line 746, in this.PromiseWalker.walkerLoop 
    this.handlers.shift().process(); 
  File "resource://gre/modules/Promise-backend.js", line 867, in Handler.prototype.process 
    nextValue = this.onResolve.call(undefined, nextValue); 
  File "resource://gre/modules/commonjs/sdk/addon/runner.js", line 86, in startup/</< 
    run(options); 
  File "resource://gre/modules/commonjs/sdk/addon/runner.js", line 145, in run 
    let program = main(options.loader, options.main); 
  File "resource://gre/modules/commonjs/toolkit/loader.js", line 740, in main 
    return loader.load(loader, module).exports; 
  File "resource://gre/modules/commonjs/sdk/loader/cuddlefish.js", line 79, in CuddlefishLoader/options<.load 
    result = load(loader, module); 
  File "resource://gre/modules/commonjs/toolkit/loader.js", line 332, in load 
    evaluate(sandbox, module.uri); 
  File "resource://gre/modules/commonjs/toolkit/loader.js", line 280, in evaluate 
    : loadSubScript(uri, sandbox, encoding); 
  File "resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/lib/main.js", line 702, in null 
    var widgets = require("sdk/widget"); 
  File "resource://gre/modules/commonjs/toolkit/loader.js", line 625, in require 
    freeze(load(loader, module)); 
  File "resource://gre/modules/commonjs/sdk/loader/cuddlefish.js", line 79, in CuddlefishLoader/options<.load 
    result = load(loader, module); 
  File "resource://gre/modules/commonjs/toolkit/loader.js", line 332, in load 
    evaluate(sandbox, module.uri); 
  File "resource://gre/modules/commonjs/toolkit/loader.js", line 280, in evaluate 
    : loadSubScript(uri, sandbox, encoding); 
  File "resource://gre/modules/commonjs/sdk/widget.js", line 59, in null 
    require("./util/deprecate").deprecateUsage( 
  File "resource://gre/modules/commonjs/sdk/util/deprecate.js", line 18, in deprecateUsage 
    let stack = get().slice(2); 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
[1684:2063:0713/073855:ERROR:logging.h(775)] Failed to call method: org.freedesktop.PowerManagement.Inhibit.Inhibit: object_path= /org/freedesktop/PowerManagement/Inhibit: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.PowerManagement was not provided by any .service files 
[1684:2063:0713/073855:ERROR:power_save_blocker_x11.cc(249)] No response to Inhibit() request! 
[1684:2067:0713/073900:ERROR:channel.cc(300)] RawChannel read error (connection broken) 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
** Message: Remote error from secret service: org.freedesktop.Secret.Error.IsLocked: Cannot get secret of a locked object 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
 
(evolution:1682): evolution-shell-WARNING **: Cannot import any of the given URIs 
[ClassicMenu Indicator] /usr/share/pixmaps/baobab.xpm: Failed to open file '/usr/share/pixmaps/baobab.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/wesnoth-1.10-icon.xpm: Failed to open file '/usr/share/pixmaps/wesnoth-1.10-icon.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/wesnoth-1.10_editor-icon.xpm: Failed to open file '/usr/share/pixmaps/wesnoth-1.10_editor-icon.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/bitfling.xpm: Failed to open file '/usr/share/pixmaps/bitfling.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/bitpim.xpm: Failed to open file '/usr/share/pixmaps/bitpim.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/devede.xpm: Failed to open file '/usr/share/pixmaps/devede.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/dia_menu.xpm: Failed to open file '/usr/share/pixmaps/dia_menu.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/dia_menu.xpm: Failed to open file '/usr/share/pixmaps/dia_menu.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/gnome-eog.xpm: Failed to open file '/usr/share/pixmaps/gnome-eog.xpm': No such file or directory 
[ClassicMenu Indicator] cxmenu-cxoffice-b0402476-4e67-4ecc-b740-073046ee123d-459F_EZDownloader.0: Error opening file: No such file or directory 
[ClassicMenu Indicator] /home/baronipc/.cxoffice/Renault Carminat navigation 32/windata/cxmenu/icons/hicolor/32x32/apps/459F_EZDownloader.0.png: Failed to open file '/home/baronipc/.cxoffice/Renault Carminat navigation 32/windata/cxmenu/icons/hicolor/32x32/apps/459F_EZDownloader.0.png': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/gmobilemedia.xpm: Failed to open file '/usr/share/pixmaps/gmobilemedia.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/gnome-control-center.xpm: Failed to open file '/usr/share/pixmaps/gnome-control-center.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/gnome-mplayer.xpm: Failed to open file '/usr/share/pixmaps/gnome-mplayer.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/gnome-nettool.xpm: Failed to open file '/usr/share/pixmaps/gnome-nettool.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/aisleriot.xpm: Failed to open file '/usr/share/pixmaps/aisleriot.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/gnucash-icon-32x32.xpm: Failed to open file '/usr/share/pixmaps/gnucash-icon-32x32.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/lshw-gtk.xpm: Failed to open file '/usr/share/pixmaps/lshw-gtk.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/mobile-atlas-creator/mobac.xpm: Failed to open file '/usr/share/pixmaps/mobile-atlas-creator/mobac.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/gnome-planner.xpm: Failed to open file '/usr/share/pixmaps/gnome-planner.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/qbittorrent.xpm: Failed to open file '/usr/share/pixmaps/qbittorrent.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/qpdfview/qpdfview.xpm: Failed to open file '/usr/share/qpdfview/qpdfview.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/rhythmbox-small.xpm: Failed to open file '/usr/share/pixmaps/rhythmbox-small.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/stellarium.xpm: Failed to open file '/usr/share/pixmaps/stellarium.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/timidity.xpm: Failed to open file '/usr/share/pixmaps/timidity.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/totem.xpm: Failed to open file '/usr/share/pixmaps/totem.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/wammu.xpm: Failed to open file '/usr/share/pixmaps/wammu.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/wsicon32.xpm: Failed to open file '/usr/share/pixmaps/wsicon32.xpm': No such file or directory 
[ClassicMenu Indicator] /usr/share/pixmaps/xfce4-mixer.xpm: Failed to open file '/usr/share/pixmaps/xfce4-mixer.xpm': No such file or directory 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
 
(evolution:1682): evolution-mail-WARNING **: mail_ui_session_lookup_addressbook: Unable to connect to 'Contacts': The requested resource was not found: https://developers.google.com/accounts/docs/AuthForInstalledApps 
 
 
(evolution:1682): evolution-mail-WARNING **: mail_ui_session_lookup_addressbook: Unable to connect to 'Contacts': The requested resource was not found: https://developers.google.com/accounts/docs/AuthForInstalledApps 
 
 
(evolution:1682): evolution-mail-WARNING **: mail_ui_session_lookup_addressbook: Unable to connect to 'Contacts': The requested resource was not found: https://developers.google.com/accounts/docs/AuthForInstalledApps 
 
 
(evolution:1682): evolution-mail-WARNING **: mail_ui_session_lookup_addressbook: Unable to connect to 'Contacts': The requested resource was not found: https://developers.google.com/accounts/docs/AuthForInstalledApps 
 
 
(evolution:1682): evolution-mail-WARNING **: mail_ui_session_lookup_addressbook: Unable to connect to 'Contacts': The requested resource was not found: https://developers.google.com/accounts/docs/AuthForInstalledApps 
 
 
(evolution:1682): evolution-mail-WARNING **: mail_ui_session_lookup_addressbook: Unable to connect to 'Contacts': The requested resource was not found: https://developers.google.com/accounts/docs/AuthForInstalledApps 
 
 
(evolution:1682): evolution-mail-WARNING **: mail_ui_session_lookup_addressbook: Unable to connect to 'Contacts': The requested resource was not found: https://developers.google.com/accounts/docs/AuthForInstalledApps 
 
 
(evolution:1682): evolution-mail-WARNING **: mail_ui_session_lookup_addressbook: Unable to connect to 'Contacts': The requested resource was not found: https://developers.google.com/accounts/docs/AuthForInstalledApps 
 
 
(evolution:1682): evolution-mail-WARNING **: mail_ui_session_lookup_addressbook: Unable to connect to 'Contacts': The requested resource was not found: https://developers.google.com/accounts/docs/AuthForInstalledApps 
 
 
(firefox:1680): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.44.1/./gobject/gsignal.c:3406: signal name 'load_complete' is invalid for instance '0x7fd8860860f0' of type 'MaiAtkType139' 
 
(firefox:1680): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.44.1/./gobject/gsignal.c:3406: signal name 'load_complete' is invalid for instance '0x7fd886086140' of type 'MaiAtkType139' 
 
(firefox:1680): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.44.1/./gobject/gsignal.c:3406: signal name 'load_complete' is invalid for instance '0x7fd886086190' of type 'MaiAtkType139' 
 
(firefox:1680): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.44.1/./gobject/gsignal.c:3406: signal name 'load_complete' is invalid for instance '0x7fd8860861e0' of type 'MaiAtkType139' 
 
(firefox:1680): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.44.1/./gobject/gsignal.c:3406: signal name 'load_complete' is invalid for instance '0x7fd886086230' of type 'MaiAtkType139' 
 
(firefox:1680): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.44.1/./gobject/gsignal.c:3406: signal name 'load_complete' is invalid for instance '0x7fd886086280' of type 'MaiAtkType139' 
 
(firefox:1680): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.44.1/./gobject/gsignal.c:3406: signal name 'load_complete' is invalid for instance '0x7fd8860862d0' of type 'MaiAtkType139' 
 
(firefox:1680): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.44.1/./gobject/gsignal.c:3406: signal name 'load_complete' is invalid for instance '0x7fd886086320' of type 'MaiAtkType139' 
 
(firefox:1680): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.44.1/./gobject/gsignal.c:3406: signal name 'load_complete' is invalid for instance '0x7fd88f898400' of type 'MaiAtkType139' 
 
(firefox:1680): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.44.1/./gobject/gsignal.c:3406: signal name 'load_complete' is invalid for instance '0x7fd8860860a0' of type 'MaiAtkType139' 
 
(firefox:1680): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.44.1/./gobject/gsignal.c:3406: signal name 'load_complete' is invalid for instance '0x7fd886086050' of type 'MaiAtkType139' 
 
(firefox:1680): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.44.1/./gobject/gsignal.c:3406: signal name 'load_complete' is invalid for instance '0x7fd886086000' of type 'MaiAtkType139' 
 
(firefox:1680): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.44.1/./gobject/gsignal.c:3406: signal name 'load_complete' is invalid for instance '0x7fd89dc78770' of type 'MaiAtkType139' 
 
(evolution:1682): evolution-mail-WARNING **: mail_ui_session_lookup_addressbook: Unable to connect to 'Contacts': The requested resource was not found: https://developers.google.com/accounts/docs/AuthForInstalledApps 
 
Fontconfig error: Cannot load default config file 
 
** (firefox:1680): CRITICAL **: gst_app_src_set_size: assertion 'GST_IS_APP_SRC (appsrc)' failed 
 
** (firefox:1680): CRITICAL **: gst_app_src_set_size: assertion 'GST_IS_APP_SRC (appsrc)' failed 
 
** (firefox:1680): CRITICAL **: gst_app_src_set_size: assertion 'GST_IS_APP_SRC (appsrc)' failed 
console.error:  
  Message: TypeError: ElementSizer.ElementList is undefined 
  Stack: 
    ElementSizer.setupSizer@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/modules/gmail/ElementTools/ElementSizer/main.js:50:4 
cls/handle@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/messenger.js:53:21 
cls/<@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/messenger.js:149:4 
onEvent@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://gre/modules/commonjs/sdk/content/content-worker.js:45:22 
onEvent@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://gre/modules/commonjs/sdk/content/content-worker.js:45:22 
onChromeEvent@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://gre/modules/commonjs/sdk/content/content-worker.js:91:16 
 
console.error:  
  Message: TypeError: ElementSizer.ElementList is undefined 
  Stack: 
    ElementSizer.setupSizer@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/modules/gmail/ElementTools/ElementSizer/main.js:50:4 
cls/handle@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/messenger.js:53:21 
cls/<@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/messenger.js:149:4 
onEvent@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://gre/modules/commonjs/sdk/content/content-worker.js:45:22 
onEvent@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://gre/modules/commonjs/sdk/content/content-worker.js:45:22 
onChromeEvent@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://gre/modules/commonjs/sdk/content/content-worker.js:91:16 
 
console.error:  
  Message: TypeError: ElementOrderer[("order" + ElementOrderer.i2level)] is undefined 
  Stack: 
    ElementOrderer.placeElements@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/modules/gmail/ElementTools/ElementOrderer/main.js:7:8 
cls/handle@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/messenger.js:53:21 
cls/<@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/messenger.js:149:4 
onEvent@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://gre/modules/commonjs/sdk/content/content-worker.js:45:22 
onEvent@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://gre/modules/commonjs/sdk/content/content-worker.js:45:22 
onChromeEvent@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://gre/modules/commonjs/sdk/content/content-worker.js:91:16 
 
console.error:  
  Message: TypeError: ElementToggler.localization[language] is undefined 
  Stack: 
    ElementToggler.setupScroller/loadConfig@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/modules/gmail/ElementTools/ElementToggler/main.js:21:5 
ElementToggler.setupScroller/preferences_callback@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/modules/gmail/ElementTools/ElementToggler/main.js:51:4 
cls/doCallback@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/messenger.js:79:5 
cls/handle@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/messenger.js:48:5 
cls/<@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/messenger.js:149:4 
onEvent@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://gre/modules/commonjs/sdk/content/content-worker.js:45:22 
onEvent@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://gre/modules/commonjs/sdk/content/content-worker.js:45:22 
onChromeEvent@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://gre/modules/commonjs/sdk/content/content-worker.js:91:16 
 
console.error:  
  Message: TypeError: ElementToggler.localization[language] is undefined 
  Stack: 
    ElementToggler.setupScroller/loadConfig@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/modules/gmail/ElementTools/ElementToggler/main.js:21:5 
ElementToggler.setupScroller/preferences_callback@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/modules/gmail/ElementTools/ElementToggler/main.js:51:4 
cls/doCallback@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/messenger.js:79:5 
cls/handle@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/messenger.js:48:5 
cls/<@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/messenger.js:149:4 
onEvent@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://gre/modules/commonjs/sdk/content/content-worker.js:45:22 
onEvent@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://gre/modules/commonjs/sdk/content/content-worker.js:45:22 
onChromeEvent@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://gre/modules/commonjs/sdk/content/content-worker.js:91:16 
 
console.error:  
  Message: TypeError: ElementToggler.localization[language] is undefined 
  Stack: 
    ElementToggler.setupScroller/loadConfig@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/modules/gmail/ElementTools/ElementToggler/main.js:21:5 
ElementToggler.setupScroller/preferences_callback@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/modules/gmail/ElementTools/ElementToggler/main.js:51:4 
cls/doCallback@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/messenger.js:79:5 
cls/handle@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/messenger.js:48:5 
cls/<@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/messenger.js:149:4 
onEvent@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://gre/modules/commonjs/sdk/content/content-worker.js:45:22 
onEvent@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://gre/modules/commonjs/sdk/content/content-worker.js:45:22 
onChromeEvent@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://gre/modules/commonjs/sdk/content/content-worker.js:91:16 
 
 
** (firefox:1680): CRITICAL **: gst_app_src_set_size: assertion 'GST_IS_APP_SRC (appsrc)' failed 
 
** (firefox:1680): CRITICAL **: gst_app_src_set_size: assertion 'GST_IS_APP_SRC (appsrc)' failed 
 
** (firefox:1680): CRITICAL **: gst_app_src_set_size: assertion 'GST_IS_APP_SRC (appsrc)' failed 
 
(evolution:1682): evolution-mail-WARNING **: mail_ui_session_lookup_addressbook: Unable to connect to 'Contacts': The requested resource was not found: https://developers.google.com/accounts/docs/AuthForInstalledApps 
 
 
(evolution:1682): evolution-mail-WARNING **: mail_ui_session_lookup_addressbook: Unable to connect to 'Contacts': The requested resource was not found: https://developers.google.com/accounts/docs/AuthForInstalledApps 
 
 
(firefox:1680): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.44.1/./gobject/gsignal.c:3406: signal name 'load_complete' is invalid for instance '0x7fd88c780ad0' of type 'MaiAtkType139' 
 
(firefox:1680): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.44.1/./gobject/gsignal.c:3406: signal name 'load_complete' is invalid for instance '0x7fd8539f1050' of type 'MaiAtkType139' 
 
(firefox:1680): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.44.1/./gobject/gsignal.c:3406: signal name 'load_complete' is invalid for instance '0x7fd88c780b20' of type 'MaiAtkType139' 
 
(firefox:1680): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.44.1/./gobject/gsignal.c:3406: signal name 'load_complete' is invalid for instance '0x7fd88c780940' of type 'MaiAtkType139' 
 
(firefox:1680): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.44.1/./gobject/gsignal.c:3406: signal name 'load_complete' is invalid for instance '0x7fd8538c8990' of type 'MaiAtkType139' 
 
(firefox:1680): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.44.1/./gobject/gsignal.c:3406: signal name 'load_complete' is invalid for instance '0x7fd876d1a720' of type 'MaiAtkType139' 
 
(firefox:1680): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.44.1/./gobject/gsignal.c:3406: signal name 'load_complete' is invalid for instance '0x7fd8538c8d40' of type 'MaiAtkType139' 
 
(evolution:1682): evolution-mail-WARNING **: mail_ui_session_lookup_addressbook: Unable to connect to 'Contacts': The requested resource was not found: https://developers.google.com/accounts/docs/AuthForInstalledApps 
 
 
(evolution:1682): evolution-mail-WARNING **: mail_ui_session_lookup_addressbook: Unable to connect to 'Contacts': The requested resource was not found: https://developers.google.com/accounts/docs/AuthForInstalledApps 
 
 
(evolution:1682): evolution-mail-WARNING **: mail_ui_session_lookup_addressbook: Unable to connect to 'Contacts': The requested resource was not found: https://developers.google.com/accounts/docs/AuthForInstalledApps 
 
 
(firefox:1680): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.44.1/./gobject/gsignal.c:3406: signal name 'load_complete' is invalid for instance '0x7fd8586e1e80' of type 'MaiAtkType139' 
 
(firefox:1680): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.44.1/./gobject/gsignal.c:3406: signal name 'load_complete' is invalid for instance '0x7fd85f68a590' of type 'MaiAtkType139' 
 
(firefox:1680): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.44.1/./gobject/gsignal.c:3406: signal name 'load_complete' is invalid for instance '0x7fd854ee68a0' of type 'MaiAtkType139' 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
[1684:2067:0713/074255:ERROR:channel.cc(300)] RawChannel read error (connection broken) 
console.error:  
  Message: TypeError: loaded_preferences is undefined 
  Stack: 
    ElementToggler.setupScroller/loadConfig@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/modules/gmail/ElementTools/ElementToggler/main.js:20:5 
ElementToggler.setupScroller/preferences_callback@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/modules/gmail/ElementTools/ElementToggler/main.js:51:4 
cls/doCallback@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/messenger.js:79:5 
cls/handle@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/messenger.js:48:5 
cls/<@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://28197867-b1ef-4140-8e3b-55c45b9c8460/integratedinbox/data/messenger.js:149:4 
onEvent@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://gre/modules/commonjs/sdk/content/content-worker.js:45:22 
onEvent@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://gre/modules/commonjs/sdk/content/content-worker.js:45:22 
onChromeEvent@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/loader/sandbox.js -> resource://gre/modules/commonjs/sdk/content/content-worker.js:91:16 
 
couldn't lock 16384 bytes of memory (secret_session): Cannot allocate memory 
 
** (firefox:1680): CRITICAL **: gst_app_src_set_size: assertion 'GST_IS_APP_SRC (appsrc)' failed 
 
** (firefox:1680): CRITICAL **: gst_app_src_set_size: assertion 'GST_IS_APP_SRC (appsrc)' failed 
 
** (firefox:1680): CRITICAL **: gst_app_src_set_size: assertion 'GST_IS_APP_SRC (appsrc)' failed 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
 
(xfdesktop:1675): GVFS-WARNING **: can't init metadata tree /home/baronipc/.local/share/gvfs-metadata/home: open: Permission denied 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
 
(xfce4-terminal:4138): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion 'GDK_IS_WINDOW (window)' failed 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments 
is expects two string arguments[/PHP]

---

### Post by Jonners59 on 2015-07-13
Solved.  Removed the app....

---

