---
title: "desktop lags for 90s on startup"
date: 2007-01-20
forum: Desktop Environments
---

### Post by simonsimon on 2007-01-20
Hello all!

I'm running edgy/gnome+beryl on an HP Pavilion laptop and I have suddenly encountered a problem.  I see the Beryl splash, hear the startup sound, and then I get a 90 second wait time before my desktop loads.  Everything had been running fine...

I should mention that I got an install this morning and checked to install it without really reading what it was.  I saw the words Ubuntu and Edgy in there... :(

More info:

I don't get an error message of any kind.

I tried some things from other posts such as:

```
sudo /etc/init.d/dbus restart
```

and got this:

```
* Stopping System Tools Backends system-tools-backends [ ok ]
* Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon [[COLOR="Red"]fail[/COLOR]]
* Stopping Hardware abstraction layer hald [ ok ]
* Stopping system message bus dbus [ ok ]
* Starting system message bus dbus [ ok ]
* Starting Hardware abstraction layer hald [ ok ]
* Starting System Tools Backends system-tools-backends [ ok ] 
```

I tried this:

```
go into tty (ctrl+alt+F1)
sudo dpkg-reconfigure gnome-desktop-data
sudo dpkg-reconfigure gnome-control-center
sudo dpkg-reconfigure gnome-menus
sudo dpkg-reconfigure gnome-system-tools
sudo dpkg-reconfigure gnome-session
```

and no result.

I also tried this:

```
sudo aptitude update && sudo aptitude install -f

apt-get install -f 
```

Nothing.

I saw a request on a thread to post xsession errors.  I can't find this on my system.  Maybe that means there are no errors.  No clue.

I'm kinda done poking around in the dark.  Too much of this behavior generally ends in disaster for me.  So if anyone can lead me in the right direction I'd be a happy guy.

Thanks!

---

### Post by mcduck on 2007-01-20
> **simonsimon said:**
> 
I saw a request on a thread to post xsession errors.  I can't find this on my system.  Maybe that means there are no errors.  No clue.

The file is ~/.xsession-errors, it's a hidden file inside your home directory. You can hit ctrl-h in Nautilus to show hidden files.

---

### Post by simonsimon on 2007-01-20
Ah!  Thanks.

Here are the contents of xsession-errors.  Can anyone decipher this for me?  The repeated "connecting to daemon" thing seems a little odd.

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "simon"
/etc/gdm/Xsession: Beginning session setup...
beryl: Failed to load slide: /home/simon/download.png
beryl: Failed to load slide: /home/simon/download.png
SESSION_MANAGER=local/laptop:/tmp/.ICE-unix/7804
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
Starting gdesklets-daemon...

Connecting to daemon [###          ]evolution-alarm-notify-Message: Setting timeout for 29566 1169337600 1169308034
evolution-alarm-notify-Message:  Sat Jan 20 18:00:00 2007

evolution-alarm-notify-Message:  Sat Jan 20 09:47:14 2007


Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
                                        
Connected to daemon in 7623 milliseconds.
evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1169337600
alarm-notify.c:366 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:302 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:241 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1871 (alarm_queue_init)
alarm-queue.c:218 (queue_midnight_refresh) - Refresh at Sat Jan 20 18:00:00 2007
 
alarm-notify.c:218 (load_calendars) - Loading Calendar file:///home/simon/.evolution/calendar/local/system 
alarm-notify.c:454 (alarm_notify_add_calendar) - Calendar Open Async... 0x80cdc00
alarm-notify.c:218 (load_calendars) - Loading Calendar contacts:/// 
alarm-notify.c:454 (alarm_notify_add_calendar) - Calendar Open Async... 0x80cbed0
alarm-notify.c:218 (load_calendars) - Loading Calendar file:///home/simon/.evolution/tasks/local/system 
alarm-notify.c:454 (alarm_notify_add_calendar) - Calendar Open Async... 0x80d2530
alarm-notify.c:218 (load_calendars) - Loading Calendar file:///home/simon/.evolution/memos/local/system 
alarm-notify.c:454 (alarm_notify_add_calendar) - Calendar Open Async... 0x80d4530
alarm-notify.c:391 (cal_opened_cb) - Calendar Status 1
alarm-queue.c:2053 (alarm_queue_add_client) - Posting a task
alarm-notify.c:347 (alarm_msg_received) - 0x80d14d8: Received at thread b5e8dba0
alarm-queue.c:2004 (alarm_queue_add_async) - 0x80cdc00
alarm-queue.c:560 (load_alarms_for_today) - From Sat Jan 20 09:47:22 2007
 to Sat Jan 20 09:47:22 2007

alarm-queue.c:497 (load_alarms) 
alarm-notify.c:391 (cal_opened_cb) - Calendar Status 1
alarm-queue.c:2053 (alarm_queue_add_client) - Posting a task
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-notify.c:335 (alarm_msgport_replied) - 0x80d14d8: Replied to GUI thread
alarm-notify.c:347 (alarm_msg_received) - 0x80d5450: Received at thread b5e8dba0
alarm-queue.c:2004 (alarm_queue_add_async) - 0x80d2530
alarm-queue.c:560 (load_alarms_for_today) - From Sat Jan 20 09:47:22 2007
 to Sat Jan 20 09:47:22 2007

alarm-queue.c:497 (load_alarms) 
alarm-notify.c:391 (cal_opened_cb) - Calendar Status 1
alarm-queue.c:2053 (alarm_queue_add_client) - Posting a task
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-notify.c:335 (alarm_msgport_replied) - 0x80d5450: Replied to GUI thread
alarm-notify.c:347 (alarm_msg_received) - 0x80d70a8: Received at thread b5e8dba0
alarm-queue.c:2004 (alarm_queue_add_async) - 0x80d4530
alarm-queue.c:560 (load_alarms_for_today) - From Sat Jan 20 09:47:22 2007
 to Sat Jan 20 09:47:22 2007

alarm-queue.c:497 (load_alarms) 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-notify.c:335 (alarm_msgport_replied) - 0x80d70a8: Replied to GUI thread
alarm-notify.c:391 (cal_opened_cb) - Calendar Status 1
alarm-queue.c:2053 (alarm_queue_add_client) - Posting a task
alarm-notify.c:347 (alarm_msg_received) - 0x80d3850: Received at thread b5e8dba0
alarm-queue.c:2004 (alarm_queue_add_async) - 0x80cbed0
alarm-queue.c:560 (load_alarms_for_today) - From Sat Jan 20 09:47:22 2007
 to Sat Jan 20 09:47:22 2007

alarm-queue.c:497 (load_alarms) 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-notify.c:335 (alarm_msgport_replied) - 0x80d3850: Replied to GUI thread
alarm-queue.c:1833 (check_midnight_refresh)
alarm-queue.c:1833 (check_midnight_refresh)
alarm-queue.c:1833 (check_midnight_refresh)
alarm-queue.c:1833 (check_midnight_refresh)
alarm-queue.c:1833 (check_midnight_refresh)
alarm-queue.c:1833 (check_midnight_refresh)
alarm-queue.c:1833 (check_midnight_refresh)
alarm-queue.c:1833 (check_midnight_refresh)
alarm-queue.c:1833 (check_midnight_refresh)
alarm-queue.c:1833 (check_midnight_refresh)
alarm-queue.c:1833 (check_midnight_refresh)
alarm-queue.c:1833 (check_midnight_refresh)
alarm-queue.c:1833 (check_midnight_refresh)
alarm-queue.c:1833 (check_midnight_refresh)
alarm-queue.c:1833 (check_midnight_refresh)
alarm-queue.c:1833 (check_midnight_refresh)
alarm-queue.c:279 (midnight_refresh_cb) - Invoking task for midnight refresh
alarm-notify.c:347 (alarm_msg_received) - 0x80bebb0: Received at thread b5e8dba0
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:233 (add_client_alarms_cb) - Adding (nil)
alarm-queue.c:560 (load_alarms_for_evolution-alarm-notify-Message: alarm.c:235: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1169424000 1169337600
evolution-alarm-notify-Message:  Sun Jan 21 18:00:00 2007

evolution-alarm-notify-Message:  Sat Jan 20 18:00:00 2007
```

---

### Post by simonsimon on 2007-01-20
Update.

I got rid of some of the errors by uninstalling gdesklets and getting rid of the download.png in beryl cube.  

Now I'm left with:

```

Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
```

I did some searching on this but I can't find any resolution.  I found this:

> 
I had metacity stallign and take about 5 minutes to log in; turned out that my save session somehow included 2 copies of metacity loading, one a 'restart' type load and another standard. They were both at the same boot priority order. (Cant remember what value, either 20 or 40..)

But I don't know where to find this information for my system.  Can I find somewhere if I have the same thing going on?

Thanks.

---

### Post by simonsimon on 2007-01-21
After much poking around blindly I found this...

Is this what he's talking about?  Will fixing something here work to solve the problem?

```
# This is the default session that is launched if the user doesn't
# already have a session.
# The RestartCommand specifies the command to run from the $PATH.
# The Priority determines the order in which the commands are started
# (with Priority = 0 first) and defaults to 50.
# The id provides a name that is unique within this file and passed to the
# app as the client id which it must use to register with gnome-session.
# The clients must be numbered from 0 to the value of num_clients - 1.

[Default]
num_clients=6
0,id=default0
0,Priority=10
0,RestartCommand=gnome-wm --sm-client-id default0
1,id=default1
1,Priority=40
1,RestartCommand=gnome-panel --sm-client-id default1
2,id=default2
2,Priority=40
2,RestartCommand=nautilus --no-default-window --sm-client-id default2
3,id=default3
3,Priority=60
3,RestartCommand=gnome-cups-icon --sm-client-id default3
4,id=default4
4,Priority=40
4,RestartCommand=gnome-volume-manager --sm-client-id default4
5,id=default5
5,Priority=50
5,RestartCommand=vino-session --sm-client-id default5
```

---

### Post by simonsimon on 2007-01-21
Anyone?

---

### Post by simonsimon on 2007-01-22
This is the latest from xsession-errors:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "simon"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/laptop:/tmp/.ICE-unix/21866
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
evolution-alarm-notify-Message: Setting timeout for 19995 1169510400 1169490405
evolution-alarm-notify-Message:  Mon Jan 22 18:00:00 2007

evolution-alarm-notify-Message:  Mon Jan 22 12:26:45 2007

** Message: failed to load session from /home/simon/.nautilus/savedmBhvmp
```

Would any other information be helpful?

---

### Post by simonsimon on 2007-01-22
Does anyone know of another place to go to get support for this issue?

---

### Post by mgmiller on 2007-01-22
The only thing I noticed here was your avahi daemon startup failure.   If you don't need avahi, try uninstalling (or reinstalling) it through synaptic.  It will tell you if it needs to uninstall other things that depend on it.  It is possible, the system is timing out waiting  for the avahi daemon to load.  
Also take a look in System>Preferences>Sessions  and look on the startup programs tab for duplicate entries.

---

### Post by simonsimon on 2007-01-23
I went ahead and reinstalled.  I do need that service so I uninstalled it and rebooted.  I still got the same wait time so I reinstalled it.

---

### Post by lotacus on 2007-01-23
just quickly read through some posts. Perhaps there is something that is not throwing an error because there are no errors? You could check your startup scripts, perhaps even your services. Check your DHCP services. Is it trying to aquire an ip address after gnome has loaded? Try changing it so it aquires it during boot. (though this would make your boot time longer.) or setting your ip address to static. 

It's just a hunch and a hunch taken from the same long desktop load from windows. heh. Blah.

---

