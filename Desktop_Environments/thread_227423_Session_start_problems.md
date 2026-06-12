---
title: "Session start problems"
date: 2006-08-01
forum: Desktop Environments
---

### Post by Nycthbris on 2006-08-01
I have been having problems with starting the normal gnome settion. Booting and startup is fine until after GDM. I log in, the wallpaper and desktop icons appear, so do the panels, but with no icons or menus (Apps, trash etc.) If I open my home folder through an icon (or anything else on my desktop for that matter), nothing happens. I am running xgl/compiz and the problem only started after I installed gtkwifi-settings-client and the ubuntu equivalent of SuSE's control center (both listed in the 3rd party forums). I can post more info if needed. Any help is greatly appreciated!

Also occasionally after logging in it will freeze with the ubuntu splash while loading the window manager

---

### Post by Nycthbris on 2006-08-01
Here is my .xsession-errors file if that helps (renamed .xsession-errors2):

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "jon"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/Jonix:/tmp/.ICE-unix/5113
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-1000/socket
This socket already exists indicating esd is already running.
Exiting...
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz.real: No managable screens found on display :0.0

** (cgwd:5240): WARNING **: Cannot open pixmap
gnome-window-decorator: no process killed
gnome-window-decorator: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
Starting gdesklets-daemon...

Connecting to daemon [###          ]
(gnome-panel:5193): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

Connecting to daemon [ ###         ]Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

Connecting to daemon [  ###        ]Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

Connecting to daemon [   ###       ]Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]

.....(this goes on for ~500 lines)

Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
                                        
Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.
The application 'nautilus' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'update-notifier' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'compiz-start.py' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
X connection to :0.0 broken (explicit kill or server shutdown).

The application 'cgwd' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'gnome-cups-icon' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
gdesklets-daemon: Fatal IO error 104 (Connection reset by peer) on X server :0.0.

```

Hope this helps to answer my question!

---

