---
title: "Deluge freezes no error"
date: 2009-06-04
forum: General Help
---

### Post by mikeym on 2009-06-04
I just ran a wee update and I'm afraid that I didn't pay too much attention to what was installed, now deluge wont start. I'm using 1.1.8 from the 3rd party repo for deluge, but the same happens if I use 1.1.6 

It freezes when I connect to a local daemon when not in classic mode and when just freezes when opening in classic mode. 

There are no error messages (or anything else other than the version) at the prompt.

---

### Post by phoenix42 on 2009-06-04
I had the same problem. From .config/deluge/deluged.log it was evident that deluge daemon could not load module libtorrent. It appears that the module name was changed in the last update, but the import in deluge daemon was not. This is strange since python-libtorrent is now part of deluge project.

To fix the problem I downgraded packages libtorrent-rasterbar2 and python-libtorrent to version 0.14.2 and now deluge is working fine.

---

### Post by theShaggy on 2009-06-17
I have found that using Update Manager renders Deluge useless, because it will not update python-libtorrent for some reason.  When there is a new version of the library, it reads as "unable to upgrade" and only lets you partially-upgrade the client.

The only way to solve it is to remove and reinstall Deluge with each successive update, until somebody can figure out why this is happening.

---

### Post by dopple on 2009-08-17
After I updated libtorrent-rasterbar2 and python-libtorrent weren't installed at all.

---

### Post by dopple on 2009-09-06
Just a quick update. Deluge started doing the same thing, freezing when it was started.
I went to see if those 2 packages had been removed somehow but they were still there. After marking both for re-installation, it's fine now.

---

### Post by dopple on 2009-10-13
Nope. Still happening. It seems to be intermittent. 
Here's the output of running from the command line with the debug switch
```
graham@graham-laptop:~$ deluge -L debug
[INFO    ] 18:07:53 main:117 Deluge ui 1.1.9
[DEBUG   ] 18:07:53 main:118 options: {'loglevel': 'debug', 'default_ui': None, 'args': None, 'quiet': False, 'ui': None, 'logfile': None, 'config': None}
[DEBUG   ] 18:07:53 main:119 args: []
[DEBUG   ] 18:07:53 main:120 ui_args: []
[INFO    ] 18:07:53 main:123 Starting ui..
[DEBUG   ] 18:07:53 ui:47 UI init..
[DEBUG   ] 18:07:53 configmanager:91 Getting config 'ui.conf'
[DEBUG   ] 18:07:53 config:253 Config /home/graham/.config/deluge/ui.conf loaded: {'default_ui': 'gtk'}
[INFO    ] 18:07:53 ui:64 Starting GtkUI..
[DEBUG   ] 18:07:53 client:113 CoreProxy init..
[DEBUG   ] 18:07:54 configmanager:91 Getting config 'gtkui.conf'
[DEBUG   ] 18:07:54 config:253 Config /home/graham/.config/deluge/gtkui.conf loaded: {'close_to_tray': True, 'ntf_sound_path': '/home/graham', 'window_width': 809, 'default_load_path': '/tmp', 'window_y_pos': 88, 'ntf_email': False, 'tray_upload_speed_list': [5.0, 10.0, 30.0, 80.0, 300.0], 'show_statusbar': True, 'ntf_popup': False, 'ntf_pass': '', 'show_sidebar': True, 'autoconnect_host_uri': None, 'window_maximized': False, 'enable_system_tray': True, 'tray_download_speed_list': [5.0, 10.0, 30.0, 80.0, 300.0], 'show_connection_manager_on_start': True, 'lock_tray': False, 'ntf_sound': False, 'tray_password': '', 'focus_add_dialog': True, 'ntf_server': '', 'start_in_tray': False, 'ntf_tray_blink': True, 'check_new_releases': False, 'autoadd_queued': False, 'classic_mode': True, 'window_pane_position': 333, 'enabled_plugins': ['Blocklist'], 'show_rate_in_title': True, 'autoadd_enable': False, 'ntf_username': '', 'interactive_add': True, 'sidebar_show_zero': False, 'window_x_pos': 362, 'window_height': 480, 'ntf_security': None, 'connection_limit_list': [50, 100, 200, 300, 500], 'sidebar_position': 170, 'show_new_releases': True, 'autoconnect': False, 'choose_directory_dialog_path': '/home/graham', 'sidebar_show_trackers': True, 'autostart_localhost': False, 'show_toolbar': True, 'autoadd_location': '', 'config_location': '/home/graham/.config/deluge', 'ntf_email_add': '', 'signal_port': 58563}
1.1.9
[DEBUG   ] 18:07:54 gtkui:182 retcode: 0
[DEBUG   ] 18:07:54 component:106 Registered QueuedTorrents with ComponentRegistry..
[DEBUG   ] 18:07:54 configmanager:91 Getting config 'gtkui.conf'
[DEBUG   ] 18:07:54 component:106 Registered IPCInterface with ComponentRegistry..
[DEBUG   ] 18:07:54 component:106 Registered DbusInterface with ComponentRegistry..
[DEBUG   ] 18:07:54 ipcinterface:87 Processing args from other process: []
[DEBUG   ] 18:07:54 ipcinterface:90 Not connected to host.. Adding to queue.
[INFO    ] 18:07:54 dbusinterface:88 Registering with DBUS..
[DEBUG   ] 18:07:54 component:106 Registered Signals with ComponentRegistry..
[DEBUG   ] 18:07:54 signalreceiver:56 SignalReceiver init..
[DEBUG   ] 18:07:54 configmanager:91 Getting config 'gtkui.conf'
[DEBUG   ] 18:07:54 config:135 Setting 'signal_port' to 48248 of <type 'int'>
[DEBUG   ] 18:07:54 config:278 Saving new config file /home/graham/.config/deluge/gtkui.conf.new
[DEBUG   ] 18:07:54 config:290 Backing up old config file to /home/graham/.config/deluge/gtkui.conf~
[DEBUG   ] 18:07:54 config:298 Moving new config file /home/graham/.config/deluge/gtkui.conf.new to /home/graham/.config/deluge/gtkui.conf..
[DEBUG   ] 18:07:54 component:106 Registered MainWindow with ComponentRegistry..
[DEBUG   ] 18:07:54 configmanager:91 Getting config 'gtkui.conf'
[DEBUG   ] 18:07:55 config:212 Registering function for show_rate_in_title key..
[DEBUG   ] 18:07:55 mainwindow:92 Showing window
[DEBUG   ] 18:07:55 menubar:54 MenuBar init..
[DEBUG   ] 18:07:55 component:106 Registered MenuBar with ComponentRegistry..
[DEBUG   ] 18:07:55 configmanager:91 Getting config 'gtkui.conf'
[DEBUG   ] 18:07:55 component:106 Registered ToolBar with ComponentRegistry..
[DEBUG   ] 18:07:55 toolbar:52 ToolBar Init..
[DEBUG   ] 18:07:55 configmanager:91 Getting config 'gtkui.conf'
[DEBUG   ] 18:07:55 component:106 Registered TorrentView with ComponentRegistry..
[DEBUG   ] 18:07:55 listview:137 ListView initialized..
[DEBUG   ] 18:07:55 listview:236 Loading ListView state file: torrentview.state
[DEBUG   ] 18:07:55 torrentview:130 TorrentView Init..
[DEBUG   ] 18:07:55 component:106 Registered TorrentDetails with ComponentRegistry..
[DEBUG   ] 18:07:55 torrentdetails:411 Loading TorrentDetails state file: tabs.state
[DEBUG   ] 18:07:55 torrentdetails:70 parent: None
[DEBUG   ] 18:07:55 torrentdetails:70 parent: None
[DEBUG   ] 18:07:55 files_tab:251 Loading FilesTab state file: files_tab.state
[DEBUG   ] 18:07:55 torrentdetails:70 parent: None
[DEBUG   ] 18:07:55 peers_tab:205 Loading PeersTab state file: peers_tab.state
[DEBUG   ] 18:07:55 torrentdetails:70 parent: None
[DEBUG   ] 18:07:55 torrentdetails:70 parent: None
[DEBUG   ] 18:07:55 component:106 Registered SideBar with ComponentRegistry..
[DEBUG   ] 18:07:55 configmanager:91 Getting config 'gtkui.conf'
[DEBUG   ] 18:07:55 component:106 Registered FilterTreeView with ComponentRegistry..
[DEBUG   ] 18:07:55 configmanager:91 Getting config 'gtkui.conf'
[DEBUG   ] 18:07:55 sidebar:86 add tab:filters
[DEBUG   ] 18:07:56 filtertreeview:270 nothing selected
[DEBUG   ] 18:07:56 component:106 Registered Preferences with ComponentRegistry..
[DEBUG   ] 18:07:56 configmanager:91 Getting config 'gtkui.conf'
[DEBUG   ] 18:07:56 component:106 Registered SystemTray with ComponentRegistry..
[DEBUG   ] 18:07:56 configmanager:91 Getting config 'gtkui.conf'
[DEBUG   ] 18:07:56 config:212 Registering function for enable_system_tray key..
[DEBUG   ] 18:07:56 systemtray:81 Enabling the system tray icon..
[DEBUG   ] 18:07:56 component:106 Registered StatusBar with ComponentRegistry..
[DEBUG   ] 18:07:56 configmanager:91 Getting config 'gtkui.conf'
[DEBUG   ] 18:07:56 component:106 Registered AddTorrentDialog with ComponentRegistry..
[DEBUG   ] 18:07:56 coreconfig:44 CoreConfig init..
[DEBUG   ] 18:07:56 component:106 Registered CoreConfig with ComponentRegistry..
[DEBUG   ] 18:07:56 component:106 Registered PluginManager with ComponentRegistry..
[DEBUG   ] 18:07:56 configmanager:91 Getting config 'gtkui.conf'
[DEBUG   ] 18:07:56 pluginmanagerbase:64 Plugin manager init..
[DEBUG   ] 18:07:56 configmanager:91 Getting config 'gtkui.conf'
[DEBUG   ] 18:07:56 pluginmanagerbase:115 Found plugin: Blocklist 1.0
[DEBUG   ] 18:07:56 pluginmanagerbase:115 Found plugin: Label 0.1
[DEBUG   ] 18:07:56 component:106 Registered ConnectionManager with ComponentRegistry..
[DEBUG   ] 18:07:56 configmanager:91 Getting config 'hostlist.conf.1.1'
[DEBUG   ] 18:07:56 config:253 Config /home/graham/.config/deluge/hostlist.conf.1.1 loaded: {'hosts': ['http://127.0.0.1:58846']}
[DEBUG   ] 18:07:56 configmanager:91 Getting config 'gtkui.conf'
[INFO    ] 18:07:56 connectionmanager:490 Starting localhost:58846 daemon..
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 525, in __bootstrap_inner
    self.run()
  File "/var/lib/python-support/python2.6/deluge/core/preferencesmanager.py", line 451, in run
    + "&plugins=" + quote_plus(self.config["enabled_plugins"])
  File "/usr/lib/python2.6/urllib.py", line 1228, in quote_plus
    return quote(s, safe)
  File "/usr/lib/python2.6/urllib.py", line 1220, in quote
    res = map(safe_map.__getitem__, s)
KeyError: 'Blocklist'

```

---

