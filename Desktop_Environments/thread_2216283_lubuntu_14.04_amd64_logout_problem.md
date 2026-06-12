---
title: "lubuntu 14.04 amd64 logout problem"
date: 2014-04-11
forum: Desktop Environments
---

### Post by ebenash on 2014-04-11
Hi,

I have installed and updated lubuntu 14.04. And after reboot , I logged into default lubuntu session but the system immediately logged out just few seconds after loading the desktop. 

I rebooted the system couple of times but same problem persists on every login. 

There's no problem with the other desktop environment (lubuntu-netbook & openbox).

Please help.

---

### Post by joshwiker14 on 2014-04-18
I have this issue too.
I upgraded to Lubuntu 14.04 from 13.10
I have a Dell Latitude D830
architechture: amd64

I looked at lightdm log, dmesg, 

lightdm.log
```
[+0.43s] DEBUG: Logging to /var/log/lightdm/lightdm.log[+0.43s] DEBUG: Starting Light Display Manager 1.10.0, UID=0 PID=1178
[+0.43s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.43s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.43s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.43s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.43s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
[+0.43s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/90-nvidia.conf
[+0.43s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.43s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.43s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/20-lubuntu.conf
[+0.43s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.43s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.43s] DEBUG: Registered seat module xlocal
[+0.43s] DEBUG: Registered seat module xremote
[+0.43s] DEBUG: Registered seat module unity
[+0.43s] DEBUG: Registered seat module surfaceflinger
[+0.43s] DEBUG: Adding default seat
[+0.43s] DEBUG: Seat: Starting
[+0.43s] DEBUG: Seat: Creating greeter session
[+0.53s] DEBUG: Seat: Creating display server of type x
[+0.53s] DEBUG: Deactivating Plymouth
[+0.55s] DEBUG: Using VT 7
[+0.55s] DEBUG: Seat: Starting local X display on VT 7
[+0.55s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.60s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.60s] DEBUG: DisplayServer x-0: Launching X Server
[+0.60s] DEBUG: Launching process 1238: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.60s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.60s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.60s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+2.52s] DEBUG: Loading users from org.freedesktop.Accounts
[+2.52s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+4.30s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+8.10s] DEBUG: Got signal 10 from process 1238
[+8.10s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+8.10s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+8.10s] DEBUG: Quitting Plymouth; retaining splash
[+8.12s] DEBUG: Launching process 1367: /sbin/prime-offload
[+8.14s] DEBUG: Process 1367 exited with return value 0
[+8.14s] DEBUG: Seat: Exit status of /sbin/prime-offload: 0
[+8.14s] DEBUG: Seat: Display server ready, starting session authentication
[+8.14s] DEBUG: Session pid=1377: Started with service 'lightdm-greeter', username 'lightdm'
[+8.37s] DEBUG: Session pid=1377: Authentication complete with return value 0: Success
[+8.37s] DEBUG: Seat: Session authenticated, running command
[+8.37s] DEBUG: Session pid=1377: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
[+8.38s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+8.38s] DEBUG: Session pid=1377: Logging to /var/log/lightdm/x-0-greeter.log
[+8.46s] DEBUG: Activating VT 7
[+8.46s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c1
[+10.24s] DEBUG: Session pid=1377: Greeter connected version=1.10.0
[+14.18s] DEBUG: Session pid=1377: Greeter start authentication for josh
[+14.18s] DEBUG: Session pid=1640: Started with service 'lightdm', username 'josh'
[+14.29s] DEBUG: Session pid=1640: Got 1 message(s) from PAM
[+14.29s] DEBUG: Session pid=1377: Prompt greeter with 1 message(s)
[+21.00s] DEBUG: Session pid=1377: Continue authentication
[+21.03s] DEBUG: Session pid=1640: Authentication complete with return value 0: Success
[+21.03s] DEBUG: Session pid=1377: Authenticate result for user josh: Success
[+21.03s] DEBUG: Session pid=1377: User josh authorized
[+21.03s] DEBUG: Session pid=1377: Greeter sets language en_US
[+21.10s] DEBUG: Session pid=1377: Greeter requests session Lubuntu
[+21.10s] DEBUG: Seat: Stopping greeter; display server will be re-used for user session
[+21.10s] DEBUG: Session pid=1377: Sending SIGTERM
[+21.17s] DEBUG: Session pid=1377: Greeter closed communication channel
[+21.17s] DEBUG: Session pid=1377: Exited with return value 0
[+21.17s] DEBUG: Seat: Session stopped
[+21.17s] DEBUG: Seat: Greeter stopped, running session
[+21.17s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+21.18s] DEBUG: Session pid=1640: Running command /usr/sbin/lightdm-session /usr/bin/lxsession -s Lubuntu -e LXDE
[+21.18s] DEBUG: Creating shared data directory /var/lib/lightdm-data/josh
[+21.18s] DEBUG: Session pid=1640: Logging to .xsession-errors
[+21.21s] DEBUG: Activating VT 7
[+21.21s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c2
[+22.44s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+37.13s] DEBUG: Session pid=1640: Exited with return value 0
[+37.13s] DEBUG: Seat: Session stopped
[+37.13s] DEBUG: Seat: Stopping display server, no sessions require it
[+37.13s] DEBUG: Sending signal 15 to process 1238
[+38.40s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+40.37s] DEBUG: Process 1238 exited with return value 0
[+40.37s] DEBUG: DisplayServer x-0: X server stopped
[+40.37s] DEBUG: Releasing VT 7
[+40.37s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+40.37s] DEBUG: Seat: Display server stopped
[+40.37s] CRITICAL: x_server_local_get_authority_file_path: assertion 'server != NULL' failed
[+40.37s] CRITICAL: x_server_get_address: assertion 'server != NULL' failed
[+40.37s] DEBUG: Launching process 1966: /sbin/prime-switch
[+40.41s] DEBUG: Process 1966 exited with return value 0
[+40.41s] DEBUG: Seat: Exit status of /sbin/prime-switch: 0
[+40.41s] DEBUG: Seat: Active display server stopped, starting greeter
[+40.41s] DEBUG: Seat: Creating greeter session
[+40.41s] DEBUG: Seat: Creating display server of type x
[+40.41s] DEBUG: Using VT 7
[+40.41s] DEBUG: Seat: Starting local X display on VT 7
[+40.41s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+40.41s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+40.41s] DEBUG: DisplayServer x-0: Launching X Server
[+40.41s] DEBUG: Launching process 1978: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+40.41s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+42.47s] DEBUG: Got signal 10 from process 1978
[+42.47s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+42.47s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+42.47s] DEBUG: Launching process 1979: /sbin/prime-offload
[+42.47s] DEBUG: Process 1979 exited with return value 0
[+42.47s] DEBUG: Seat: Exit status of /sbin/prime-offload: 0
[+42.47s] DEBUG: Seat: Display server ready, starting session authentication
[+42.47s] DEBUG: Session pid=1985: Started with service 'lightdm-greeter', username 'lightdm'
[+42.50s] DEBUG: Session pid=1985: Authentication complete with return value 0: Success
[+42.50s] DEBUG: Seat: Session authenticated, running command
[+42.50s] DEBUG: Session pid=1985: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
[+42.50s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+42.50s] DEBUG: Session pid=1985: Logging to /var/log/lightdm/x-0-greeter.log
[+42.50s] DEBUG: Activating VT 7
[+42.50s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c3
[+42.65s] DEBUG: Session pid=1985: Greeter connected version=1.10.0
[+43.07s] DEBUG: Session pid=1985: Greeter start authentication for josh
[+43.07s] DEBUG: Session pid=2038: Started with service 'lightdm', username 'josh'
[+43.08s] DEBUG: Session pid=2038: Got 1 message(s) from PAM
[+43.08s] DEBUG: Session pid=1985: Prompt greeter with 1 message(s)
[+64.62s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+577.80s] DEBUG: Session pid=1985: Continue authentication
[+577.84s] DEBUG: Session pid=2038: Authentication complete with return value 0: Success
[+577.84s] DEBUG: Session pid=1985: Authenticate result for user josh: Success
[+577.84s] DEBUG: Session pid=1985: User josh authorized
[+577.84s] DEBUG: Session pid=1985: Greeter sets language en_US
[+577.91s] DEBUG: Session pid=1985: Greeter requests session Lubuntu-Netbook
[+577.99s] DEBUG: Writing /home/josh/.dmrc
[+578.12s] DEBUG: Seat: Stopping greeter; display server will be re-used for user session
[+578.12s] DEBUG: Session pid=1985: Sending SIGTERM
[+578.12s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+578.20s] DEBUG: Session pid=1985: Greeter closed communication channel
[+578.20s] DEBUG: Session pid=1985: Exited with return value 0
[+578.20s] DEBUG: Seat: Session stopped
[+578.20s] DEBUG: Seat: Greeter stopped, running session
[+578.20s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session1
[+578.20s] DEBUG: Session pid=2038: Running command /usr/sbin/lightdm-session /usr/bin/lxsession -s Lubuntu-Netbook -e LXDE
[+578.20s] DEBUG: Creating shared data directory /var/lib/lightdm-data/josh
[+578.20s] DEBUG: Session pid=2038: Logging to .xsession-errors
[+578.22s] DEBUG: Activating VT 7
[+578.22s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c5
[+579.71s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+650.04s] DEBUG: Session pid=2038: Exited with return value 0
[+650.04s] DEBUG: Seat: Session stopped
[+650.04s] DEBUG: Seat: Stopping display server, no sessions require it
[+650.04s] DEBUG: Sending signal 15 to process 1978
[+651.25s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+652.86s] DEBUG: Process 1978 exited with return value 0
[+652.86s] DEBUG: DisplayServer x-0: X server stopped
[+652.86s] DEBUG: Releasing VT 7
[+652.86s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+652.86s] DEBUG: Seat: Display server stopped
[+652.86s] CRITICAL: x_server_local_get_authority_file_path: assertion 'server != NULL' failed
[+652.86s] CRITICAL: x_server_get_address: assertion 'server != NULL' failed
[+652.86s] DEBUG: Launching process 3239: /sbin/prime-switch
[+652.88s] DEBUG: Process 3239 exited with return value 0
[+652.88s] DEBUG: Seat: Exit status of /sbin/prime-switch: 0
[+652.88s] DEBUG: Seat: Active display server stopped, starting greeter
[+652.88s] DEBUG: Seat: Creating greeter session
[+652.88s] DEBUG: Seat: Creating display server of type x
[+652.88s] DEBUG: Using VT 7
[+652.88s] DEBUG: Seat: Starting local X display on VT 7
[+652.88s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+652.88s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+652.88s] DEBUG: DisplayServer x-0: Launching X Server
[+652.88s] DEBUG: Launching process 3251: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+652.88s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+654.99s] DEBUG: Got signal 10 from process 3251
[+654.99s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+654.99s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+654.99s] DEBUG: Launching process 3252: /sbin/prime-offload
[+655.00s] DEBUG: Process 3252 exited with return value 0
[+655.00s] DEBUG: Seat: Exit status of /sbin/prime-offload: 0
[+655.00s] DEBUG: Seat: Display server ready, starting session authentication
[+655.00s] DEBUG: Session pid=3258: Started with service 'lightdm-greeter', username 'lightdm'
[+655.02s] DEBUG: Session pid=3258: Authentication complete with return value 0: Success
[+655.02s] DEBUG: Seat: Session authenticated, running command
[+655.02s] DEBUG: Session pid=3258: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
[+655.03s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+655.03s] DEBUG: Session pid=3258: Logging to /var/log/lightdm/x-0-greeter.log
[+655.04s] DEBUG: Activating VT 7
[+655.04s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c6
[+655.13s] DEBUG: Session pid=3258: Greeter connected version=1.10.0
[+655.56s] DEBUG: Session pid=3258: Greeter start authentication for josh
[+655.56s] DEBUG: Session pid=3311: Started with service 'lightdm', username 'josh'
[+655.56s] DEBUG: Session pid=3311: Got 1 message(s) from PAM
[+655.56s] DEBUG: Session pid=3258: Prompt greeter with 1 message(s)
[+660.67s] DEBUG: Session pid=3258: Continue authentication
[+660.71s] DEBUG: Session pid=3311: Authentication complete with return value 0: Success
[+660.71s] DEBUG: Session pid=3258: Authenticate result for user josh: Success
[+660.71s] DEBUG: Session pid=3258: User josh authorized
[+660.71s] DEBUG: Session pid=3258: Greeter sets language en_US
[+660.77s] DEBUG: Session pid=3258: Greeter requests session Lubuntu-Netbook
[+660.77s] DEBUG: Seat: Stopping greeter; display server will be re-used for user session
[+660.77s] DEBUG: Session pid=3258: Sending SIGTERM
[+660.83s] DEBUG: Session pid=3258: Greeter closed communication channel
[+660.83s] DEBUG: Session pid=3258: Exited with return value 0
[+660.83s] DEBUG: Seat: Session stopped
[+660.83s] DEBUG: Seat: Greeter stopped, running session
[+660.83s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session2
[+660.83s] DEBUG: Session pid=3311: Running command /usr/sbin/lightdm-session /usr/bin/lxsession -s Lubuntu-Netbook -e LXDE
[+660.83s] DEBUG: Creating shared data directory /var/lib/lightdm-data/josh
[+660.83s] DEBUG: Session pid=3311: Logging to .xsession-errors
[+660.84s] DEBUG: Activating VT 7
[+660.84s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c7
[+662.34s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+1544.87s] DEBUG: Got signal 15 from process 1
[+1544.87s] DEBUG: Caught Terminated signal, shutting down
[+1544.87s] DEBUG: Stopping display manager
[+1544.87s] DEBUG: Seat: Stopping
[+1544.87s] DEBUG: Seat: Stopping display server
[+1544.87s] DEBUG: Sending signal 15 to process 3251
[+1544.87s] DEBUG: Seat: Stopping session
[+1544.87s] DEBUG: Session pid=3311: Sending SIGTERM
[+1545.13s] DEBUG: Session pid=3311: Exited with return value 0
[+1545.13s] DEBUG: Seat: Session stopped
[+1546.29s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+1548.40s] DEBUG: Process 3251 exited with return value 0
[+1548.40s] DEBUG: DisplayServer x-0: X server stopped
[+1548.40s] DEBUG: Releasing VT 7
[+1548.40s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+1548.40s] DEBUG: Seat: Display server stopped
[+1548.40s] CRITICAL: x_server_local_get_authority_file_path: assertion 'server != NULL' failed
[+1548.40s] CRITICAL: x_server_get_address: assertion 'server != NULL' failed
[+1548.40s] DEBUG: Launching process 4059: /sbin/prime-switch
[+1548.42s] DEBUG: Process 4059 exited with return value 0
[+1548.42s] DEBUG: Seat: Exit status of /sbin/prime-switch: 0
[+1548.42s] DEBUG: Seat: Stopped
[+1548.42s] DEBUG: Display manager stopped
[+1548.42s] DEBUG: Stopping daemon
[+1548.42s] DEBUG: Exiting with return value 0
```

some of dmesg output:
```
[   96.918288] lxsession[2423]: segfault at 0 ip 000000000040a6c0 sp 00007fffe67a92b0 error 4 in lxsession[400000+35000]
```

.cache/lxsession/LXDE/run.log:
```
** Message: environement.vala:58: Exporting primary_variable** Message: environement.vala:59: desktop_environnement XDG_CURRENT_DESKTOP
** Message: environement.vala:176: custom_config :
** Message: environement.vala:177: config_dirs :/etc/xdg/xdg-LXDE:/etc/xdg
** Message: environement.vala:178: confir_dirs not null, export : /etc/xdg/xdg-LXDE:/etc/xdg
** Message: environement.vala:183: Exporting XDG_CONFIG_DIRS
** Message: environement.vala:217: custom_data :/usr/local/share:/usr/share:/usr/share/gdm:/var/lib/menu-xdg:
** Message: environement.vala:218: data_dirs :/usr/local/share/:/usr/share/:/usr/share/gdm/:/var/lib/menu-xdg/
** Message: environement.vala:219: data_dirs not null, export : /usr/local/share:/usr/share:/usr/share/gdm:/var/lib/menu-xdg:/usr/local/share/:/usr/share/:/usr/share/gdm/:/var/lib/menu-xdg/
** Message: environement.vala:224: Exporting XDG_DATA_DIRS
** Message: utils.vala:68: User config used : /home/josh/.config/lxsession/LXDE/desktop.conf
** Message: utils.vala:89: Final file used : /home/josh/.config/lxsession/LXDE/desktop.conf
** Message: settings.vala:619: Create new config key: Session;windows_manager;command;
** Message: settings.vala:105: Enter if of read_value for Session, windows_manager, command, string, openbox: 
** Message: settings.vala:359: key of set_value: Session;windows_manager;command;
** Message: settings.vala:924: Changing Session - windows_manager - command to openbox
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;windows_manager;session;
** Message: settings.vala:105: Enter if of read_value for Session, windows_manager, session, string, LXDE: 
** Message: settings.vala:359: key of set_value: Session;windows_manager;session;
** Message: settings.vala:924: Changing Session - windows_manager - session to LXDE
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;windows_manager;extras;
** Message: settings.vala:513: Key file does not have key 'windows_manager/extras'
** Message: settings.vala:105: Enter if of read_value for Session, windows_manager, extras, string, (null): 
** Message: settings.vala:513: Key file does not have key 'panel/command'
** Message: settings.vala:513: Key file does not have key 'dock/command'
** Message: settings.vala:513: Key file does not have key 'file_manager/command'
** Message: settings.vala:513: Key file does not have key 'desktop_manager/command'
** Message: settings.vala:619: Create new config key: Session;launcher_manager;command;
** Message: settings.vala:105: Enter if of read_value for Session, launcher_manager, command, string, lxpanelctl: 
** Message: settings.vala:359: key of set_value: Session;launcher_manager;command;
** Message: settings.vala:924: Changing Session - launcher_manager - command to lxpanelctl
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;launcher_manager;autostart;
** Message: settings.vala:513: Key file does not have key 'launcher_manager/autostart'
** Message: settings.vala:105: Enter if of read_value for Session, launcher_manager, autostart, string, (null): 
** Message: settings.vala:513: Key file does not have key 'composite_manager/command'
** Message: settings.vala:513: Key file does not have key 'im1/command'
** Message: settings.vala:513: Key file does not have key 'im2/command'
** Message: settings.vala:513: Key file does not have key 'widget1/command'
** Message: settings.vala:513: Key file does not have key 'notification/command'
** Message: settings.vala:513: Key file does not have key 'keybindings/command'
** Message: settings.vala:619: Create new config key: Session;screensaver;command;
** Message: settings.vala:513: Key file does not have key 'screensaver/command'
** Message: settings.vala:105: Enter if of read_value for Session, screensaver, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;power_manager;command;
** Message: settings.vala:513: Key file does not have key 'power_manager/command'
** Message: settings.vala:105: Enter if of read_value for Session, power_manager, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;polkit;command;
** Message: settings.vala:513: Key file does not have key 'polkit/command'
** Message: settings.vala:105: Enter if of read_value for Session, polkit, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;audio_manager;command;
** Message: settings.vala:513: Key file does not have key 'audio_manager/command'
** Message: settings.vala:105: Enter if of read_value for Session, audio_manager, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;quit_manager;command;
** Message: settings.vala:105: Enter if of read_value for Session, quit_manager, command, string, lxsession-logout: 
** Message: settings.vala:359: key of set_value: Session;quit_manager;command;
** Message: settings.vala:924: Changing Session - quit_manager - command to lxsession-logout
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:105: Enter if of read_value for Session, quit_manager, command, string, lxsession-logout: 
** Message: settings.vala:619: Create new config key: Session;quit_manager;image;
** Message: settings.vala:105: Enter if of read_value for Session, quit_manager, image, string, /usr/share/lxde/images/logout-banner.png: 
** Message: settings.vala:359: key of set_value: Session;quit_manager;image;
** Message: settings.vala:924: Changing Session - quit_manager - image to /usr/share/lxde/images/logout-banner.png
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;quit_manager;layout;
** Message: settings.vala:105: Enter if of read_value for Session, quit_manager, layout, string, top: 
** Message: settings.vala:359: key of set_value: Session;quit_manager;layout;
** Message: settings.vala:924: Changing Session - quit_manager - layout to top
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;workspace_manager;command;
** Message: settings.vala:513: Key file does not have key 'workspace_manager/command'
** Message: settings.vala:105: Enter if of read_value for Session, workspace_manager, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;terminal_manager;command;
** Message: settings.vala:105: Enter if of read_value for Session, terminal_manager, command, string, lxterminal: 
** Message: settings.vala:359: key of set_value: Session;terminal_manager;command;
** Message: settings.vala:924: Changing Session - terminal_manager - command to lxterminal
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;screenshot_manager;command;
** Message: settings.vala:513: Key file does not have key 'screenshot_manager/command'
** Message: settings.vala:105: Enter if of read_value for Session, screenshot_manager, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;lock_manager;command;
** Message: settings.vala:105: Enter if of read_value for Session, lock_manager, command, string, lxlock: 
** Message: settings.vala:359: key of set_value: Session;lock_manager;command;
** Message: settings.vala:924: Changing Session - lock_manager - command to lxlock
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;message_manager;command;
** Message: settings.vala:513: Key file does not have key 'message_manager/command'
** Message: settings.vala:105: Enter if of read_value for Session, message_manager, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;upgrade_manager;command;
** Message: settings.vala:513: Key file does not have key 'upgrade_manager/command'
** Message: settings.vala:105: Enter if of read_value for Session, upgrade_manager, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;clipboard;command;
** Message: settings.vala:105: Enter if of read_value for Session, clipboard, command, string, lxclipboard: 
** Message: settings.vala:359: key of set_value: Session;clipboard;command;
** Message: settings.vala:924: Changing Session - clipboard - command to lxclipboard
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;disable_autostart;;
** Message: settings.vala:105: Enter if of read_value for Session, disable_autostart, (null), string, no: 
** Message: settings.vala:359: key of set_value: Session;disable_autostart;;
** Message: settings.vala:912: Changing Session - disable_autostart to no
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;upstart_user_session;;
** Message: settings.vala:513: Key file does not have key 'upstart_user_session'
** Message: settings.vala:105: Enter if of read_value for Session, upstart_user_session, (null), string, (null): 
** Message: settings.vala:619: Create new config key: Session;xsettings_manager;command;
** Message: settings.vala:105: Enter if of read_value for Session, xsettings_manager, command, string, build-in: 
** Message: settings.vala:359: key of set_value: Session;xsettings_manager;command;
** Message: settings.vala:924: Changing Session - xsettings_manager - command to build-in
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;proxy_manager;command;
** Message: settings.vala:105: Enter if of read_value for Session, proxy_manager, command, string, build-in: 
** Message: settings.vala:359: key of set_value: Session;proxy_manager;command;
** Message: settings.vala:924: Changing Session - proxy_manager - command to build-in
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;proxy_manager;http;
** Message: settings.vala:513: Key file does not have key 'proxy_manager/http'
** Message: settings.vala:105: Enter if of read_value for Session, proxy_manager, http, string, (null): 
** Message: settings.vala:619: Create new config key: Session;a11y;command;
** Message: settings.vala:513: Key file does not have key 'a11y/command'
** Message: settings.vala:105: Enter if of read_value for Session, a11y, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;keyring;command;
** Message: settings.vala:105: Enter if of read_value for Session, keyring, command, string, ssh-agent: 
** Message: settings.vala:359: key of set_value: Session;keyring;command;
** Message: settings.vala:924: Changing Session - keyring - command to ssh-agent
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Session;xrandr;command;
** Message: settings.vala:513: Key file does not have key 'xrandr/command'
** Message: settings.vala:105: Enter if of read_value for Session, xrandr, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;webbrowser;command;
** Message: settings.vala:513: Key file does not have key 'webbrowser/command'
** Message: settings.vala:105: Enter if of read_value for Session, webbrowser, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;email;command;
** Message: settings.vala:513: Key file does not have key 'email/command'
** Message: settings.vala:105: Enter if of read_value for Session, email, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;pdf_reader;command;
** Message: settings.vala:513: Key file does not have key 'pdf_reader/command'
** Message: settings.vala:105: Enter if of read_value for Session, pdf_reader, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;video_player;command;
** Message: settings.vala:513: Key file does not have key 'video_player/command'
** Message: settings.vala:105: Enter if of read_value for Session, video_player, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;audio_player;command;
** Message: settings.vala:513: Key file does not have key 'audio_player/command'
** Message: settings.vala:105: Enter if of read_value for Session, audio_player, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;images_display;command;
** Message: settings.vala:513: Key file does not have key 'images_display/command'
** Message: settings.vala:105: Enter if of read_value for Session, images_display, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;text_editor;command;
** Message: settings.vala:513: Key file does not have key 'text_editor/command'
** Message: settings.vala:105: Enter if of read_value for Session, text_editor, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;archive;command;
** Message: settings.vala:513: Key file does not have key 'archive/command'
** Message: settings.vala:105: Enter if of read_value for Session, archive, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;charmap;command;
** Message: settings.vala:513: Key file does not have key 'charmap/command'
** Message: settings.vala:105: Enter if of read_value for Session, charmap, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;calculator;command;
** Message: settings.vala:513: Key file does not have key 'calculator/command'
** Message: settings.vala:105: Enter if of read_value for Session, calculator, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;spreadsheet;command;
** Message: settings.vala:513: Key file does not have key 'spreadsheet/command'
** Message: settings.vala:105: Enter if of read_value for Session, spreadsheet, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;bittorent;command;
** Message: settings.vala:513: Key file does not have key 'bittorent/command'
** Message: settings.vala:105: Enter if of read_value for Session, bittorent, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;document;command;
** Message: settings.vala:513: Key file does not have key 'document/command'
** Message: settings.vala:105: Enter if of read_value for Session, document, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;webcam;command;
** Message: settings.vala:513: Key file does not have key 'webcam/command'
** Message: settings.vala:105: Enter if of read_value for Session, webcam, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;burn;command;
** Message: settings.vala:513: Key file does not have key 'burn/command'
** Message: settings.vala:105: Enter if of read_value for Session, burn, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;notes;command;
** Message: settings.vala:513: Key file does not have key 'notes/command'
** Message: settings.vala:105: Enter if of read_value for Session, notes, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;disk_utility;command;
** Message: settings.vala:513: Key file does not have key 'disk_utility/command'
** Message: settings.vala:105: Enter if of read_value for Session, disk_utility, command, string, (null): 
** Message: settings.vala:619: Create new config key: Session;tasks;command;
** Message: settings.vala:513: Key file does not have key 'tasks/command'
** Message: settings.vala:105: Enter if of read_value for Session, tasks, command, string, (null): 
** Message: settings.vala:513: Key file does not have group 'Keymap'
** Message: settings.vala:619: Create new config key: State;laptop_mode;;
** Message: settings.vala:513: Key file does not have key 'laptop_mode'
** Message: settings.vala:105: Enter if of read_value for State, laptop_mode, (null), string, (null): 
** Message: settings.vala:619: Create new config key: State;guess_default;;
** Message: settings.vala:105: Enter if of read_value for State, guess_default, (null), string, true: 
** Message: settings.vala:359: key of set_value: State;guess_default;;
** Message: settings.vala:912: Changing State - guess_default to true
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Dbus;lxde;;
** Message: settings.vala:105: Enter if of read_value for Dbus, lxde, (null), string, true: 
** Message: settings.vala:359: key of set_value: Dbus;lxde;;
** Message: settings.vala:912: Changing Dbus - lxde to true
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Dbus;gnome;;
** Message: settings.vala:513: Key file does not have key 'gnome'
** Message: settings.vala:105: Enter if of read_value for Dbus, gnome, (null), string, (null): 
** Message: settings.vala:619: Create new config key: Updates;type;;
** Message: settings.vala:513: Key file does not have group 'Updates'
** Message: settings.vala:105: Enter if of read_value for Updates, type, (null), string, (null): 
** Message: settings.vala:619: Create new config key: Environment;type;;
** Message: settings.vala:513: Key file does not have key 'type'
** Message: settings.vala:105: Enter if of read_value for Environment, type, (null), string, (null): 
** Message: settings.vala:619: Create new config key: Environment;menu_prefix;;
** Message: settings.vala:105: Enter if of read_value for Environment, menu_prefix, (null), string, lxde-: 
** Message: settings.vala:359: key of set_value: Environment;menu_prefix;;
** Message: settings.vala:912: Changing Environment - menu_prefix to lxde-
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;sNet;ThemeName;
** Message: settings.vala:105: Enter if of read_value for GTK, sNet, ThemeName, string, Clearlooks: 
** Message: settings.vala:359: key of set_value: GTK;sNet;ThemeName;
** Message: settings.vala:924: Changing GTK - sNet - ThemeName to Clearlooks
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;sNet;IconThemeName;
** Message: settings.vala:105: Enter if of read_value for GTK, sNet, IconThemeName, string, nuoveXT2: 
** Message: settings.vala:359: key of set_value: GTK;sNet;IconThemeName;
** Message: settings.vala:924: Changing GTK - sNet - IconThemeName to nuoveXT2
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;sGtk;FontName;
** Message: settings.vala:105: Enter if of read_value for GTK, sGtk, FontName, string, Sans 10: 
** Message: settings.vala:359: key of set_value: GTK;sGtk;FontName;
** Message: settings.vala:924: Changing GTK - sGtk - FontName to Sans 10
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;iGtk;ToolbarStyle;
** Message: settings.vala:105: Enter if of read_value for GTK, iGtk, ToolbarStyle, string, 3: 
** Message: settings.vala:359: key of set_value: GTK;iGtk;ToolbarStyle;
** Message: settings.vala:924: Changing GTK - iGtk - ToolbarStyle to 3
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;iGtk;ButtonImages;
** Message: settings.vala:105: Enter if of read_value for GTK, iGtk, ButtonImages, string, 1: 
** Message: settings.vala:359: key of set_value: GTK;iGtk;ButtonImages;
** Message: settings.vala:924: Changing GTK - iGtk - ButtonImages to 1
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;iGtk;MenuImages;
** Message: settings.vala:105: Enter if of read_value for GTK, iGtk, MenuImages, string, 1: 
** Message: settings.vala:359: key of set_value: GTK;iGtk;MenuImages;
** Message: settings.vala:924: Changing GTK - iGtk - MenuImages to 1
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;iGtk;CursorThemeSize;
** Message: settings.vala:105: Enter if of read_value for GTK, iGtk, CursorThemeSize, string, 18: 
** Message: settings.vala:359: key of set_value: GTK;iGtk;CursorThemeSize;
** Message: settings.vala:924: Changing GTK - iGtk - CursorThemeSize to 18
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;iXft;Antialias;
** Message: settings.vala:105: Enter if of read_value for GTK, iXft, Antialias, string, 1: 
** Message: settings.vala:359: key of set_value: GTK;iXft;Antialias;
** Message: settings.vala:924: Changing GTK - iXft - Antialias to 1
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;iXft;Hinting;
** Message: settings.vala:105: Enter if of read_value for GTK, iXft, Hinting, string, 1: 
** Message: settings.vala:359: key of set_value: GTK;iXft;Hinting;
** Message: settings.vala:924: Changing GTK - iXft - Hinting to 1
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;sXft;HintStyle;
** Message: settings.vala:105: Enter if of read_value for GTK, sXft, HintStyle, string, hintslight: 
** Message: settings.vala:359: key of set_value: GTK;sXft;HintStyle;
** Message: settings.vala:924: Changing GTK - sXft - HintStyle to hintslight
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;sXft;RGBA;
** Message: settings.vala:105: Enter if of read_value for GTK, sXft, RGBA, string, rgb: 
** Message: settings.vala:359: key of set_value: GTK;sXft;RGBA;
** Message: settings.vala:924: Changing GTK - sXft - RGBA to rgb
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;sGtk;ColorScheme;
** Message: settings.vala:513: Key file does not have key 'sGtk/ColorScheme'
** Message: settings.vala:105: Enter if of read_value for GTK, sGtk, ColorScheme, string, (null): 
** Message: settings.vala:619: Create new config key: GTK;sGtk;CursorThemeName;
** Message: settings.vala:105: Enter if of read_value for GTK, sGtk, CursorThemeName, string, DMZ-White: 
** Message: settings.vala:359: key of set_value: GTK;sGtk;CursorThemeName;
** Message: settings.vala:924: Changing GTK - sGtk - CursorThemeName to DMZ-White
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;iGtk;ToolbarIconSize;
** Message: settings.vala:105: Enter if of read_value for GTK, iGtk, ToolbarIconSize, string, 3: 
** Message: settings.vala:359: key of set_value: GTK;iGtk;ToolbarIconSize;
** Message: settings.vala:924: Changing GTK - iGtk - ToolbarIconSize to 3
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;iNet;EnableEventSounds;
** Message: settings.vala:105: Enter if of read_value for GTK, iNet, EnableEventSounds, string, 1: 
** Message: settings.vala:359: key of set_value: GTK;iNet;EnableEventSounds;
** Message: settings.vala:924: Changing GTK - iNet - EnableEventSounds to 1
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: GTK;iNet;EnableInputFeedbackSounds;
** Message: settings.vala:105: Enter if of read_value for GTK, iNet, EnableInputFeedbackSounds, string, 1: 
** Message: settings.vala:359: key of set_value: GTK;iNet;EnableInputFeedbackSounds;
** Message: settings.vala:924: Changing GTK - iNet - EnableInputFeedbackSounds to 1
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Mouse;AccFactor;;
** Message: settings.vala:105: Enter if of read_value for Mouse, AccFactor, (null), string, 20: 
** Message: settings.vala:359: key of set_value: Mouse;AccFactor;;
** Message: settings.vala:912: Changing Mouse - AccFactor to 20
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Mouse;AccThreshold;;
** Message: settings.vala:105: Enter if of read_value for Mouse, AccThreshold, (null), string, 10: 
** Message: settings.vala:359: key of set_value: Mouse;AccThreshold;;
** Message: settings.vala:912: Changing Mouse - AccThreshold to 10
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Mouse;LeftHanded;;
** Message: settings.vala:105: Enter if of read_value for Mouse, LeftHanded, (null), string, 0: 
** Message: settings.vala:359: key of set_value: Mouse;LeftHanded;;
** Message: settings.vala:912: Changing Mouse - LeftHanded to 0
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Keyboard;Delay;;
** Message: settings.vala:105: Enter if of read_value for Keyboard, Delay, (null), string, 500: 
** Message: settings.vala:359: key of set_value: Keyboard;Delay;;
** Message: settings.vala:912: Changing Keyboard - Delay to 500
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Keyboard;Interval;;
** Message: settings.vala:105: Enter if of read_value for Keyboard, Interval, (null), string, 30: 
** Message: settings.vala:359: key of set_value: Keyboard;Interval;;
** Message: settings.vala:912: Changing Keyboard - Interval to 30
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:619: Create new config key: Keyboard;Beep;;
** Message: settings.vala:105: Enter if of read_value for Keyboard, Beep, (null), string, 1: 
** Message: settings.vala:359: key of set_value: Keyboard;Beep;;
** Message: settings.vala:912: Changing Keyboard - Beep to 1
** Message: settings.vala:860: Saving desktop file
** Message: settings.vala:435: Monitoring: /home/josh/.config/lxsession/LXDE/desktop.conf
** Message: settings.vala:439: Desktop file is already in config home, do nothing
** Message: settings.vala:346: Settings default for GTK, iGtk, ColorScheme : 
** Message: settings.vala:359: key of set_value: GTK;iGtk;ColorScheme;
** Message: settings.vala:924: Changing GTK - iGtk - ColorScheme to 
** Message: settings.vala:860: Saving desktop file
** Message: environement.vala:79: Exporting variable
** Message: environement.vala:80: desktop_environnement XDG_CURRENT_DESKTOP
** Message: environement.vala:176: custom_config :
** Message: environement.vala:177: config_dirs :/etc/xdg/xdg-LXDE:/etc/xdg
** Message: environement.vala:178: confir_dirs not null, export : /etc/xdg/xdg-LXDE:/etc/xdg
** Message: environement.vala:183: Exporting XDG_CONFIG_DIRS
** Message: environement.vala:217: custom_data :
** Message: environement.vala:218: data_dirs :/usr/local/share:/usr/share:/usr/share/gdm:/var/lib/menu-xdg:/usr/local/share/:/usr/share/:/usr/share/gdm/:/var/lib/menu-xdg/
** Message: environement.vala:219: data_dirs not null, export : /usr/local/share:/usr/share:/usr/share/gdm:/var/lib/menu-xdg:/usr/local/share/:/usr/share/:/usr/share/gdm/:/var/lib/menu-xdg/
** Message: environement.vala:224: Exporting XDG_DATA_DIRS
** Message: utils.vala:79: Config system location : /etc/xdg/xdg-LXDE/lxsession/LXDE
** Message: utils.vala:79: Config system location : /etc/xdg/lxsession/LXDE
** Message: utils.vala:85: System system path location : /etc/xdg/lxsession/LXDE/conffiles.conf
** Message: utils.vala:89: Final file used : /etc/xdg/lxsession/LXDE/conffiles.conf
** Message: options.vala:164: Activate xsettings_manager build-in
** Message: utils.vala:68: User config used : /home/josh/.config/lxsession/LXDE/desktop.conf
** Message: utils.vala:89: Final file used : /home/josh/.config/lxsession/LXDE/desktop.conf
xprop:  no such property "_NET_NUMBER_OF_DESKTOPS"
xprop:  no such property "_NET_DESKTOP_NAMES"
** Message: main.vala:231: DEBUG2 : openbox
** Message: utils.vala:68: User config used : /home/josh/.config/lxsession/LXDE/autostart
** Message: utils.vala:89: Final file used : /home/josh/.config/lxsession/LXDE/autostart
** Message: autostart.vala:42: Autostart path : /home/josh/.config/lxsession/LXDE/autostart
** Message: app.vala:76: Launching xscreensaver 
** Message: app.vala:76: Launching lxpanel 
** Message: app.vala:76: Launching pcmanfm 
** Message: app.vala:76: Launching /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 


(polkit-gnome-authentication-agent-1:4392): GLib-CRITICAL **: g_variant_new_string: assertion 'string != NULL' failed


(polkit-gnome-authentication-agent-1:4392): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
** Message: options.vala:107: Create build-in Clipboard
** Message: main.vala:429: Check keymap_mode (null)
** Message: app.vala:76: Launching /usr/bin/ssh-agent 
SSH_AUTH_SOCK=/tmp/ssh-h2w8M3XkjQea/agent.4425; export SSH_AUTH_SOCK;
SSH_AGENT_PID=4429; export SSH_AGENT_PID;
echo Agent pid 4429;
** Message: app.vala:130: /usr/bin/ssh-agent exit with this type of exit: 0
Openbox-Message: Requested key "XF86Terminal" does not exist on the display


** (pcmanfm:4391): WARNING **: modules directory is not accessible
** Message: settings.vala:482: Desktop file change, reloading XSettings daemon
** Message: options.vala:186: Reload xsettings_manager build-in
** Message: utils.vala:68: User config used : /home/josh/.config/lxsession/LXDE/desktop.conf
** Message: utils.vala:89: Final file used : /home/josh/.config/lxsession/LXDE/desktop.conf
** Message: settings.vala:476: Reload the xsettings option
** Message: settings.vala:482: Desktop file change, reloading XSettings daemon
** Message: options.vala:186: Reload xsettings_manager build-in
** Message: utils.vala:68: User config used : /home/josh/.config/lxsession/LXDE/desktop.conf
** Message: utils.vala:89: Final file used : /home/josh/.config/lxsession/LXDE/desktop.conf
** Message: settings.vala:476: Reload the xsettings option
[4394:4506:0418/180920:ERROR:download.cc(109)] PostClientToServerMessage() failed during GetUpdates
Created new window in existing browser session.
[4394:4394:0418/180936:ERROR:generic_change_processor.cc(289)] Favicon Images Failed to delete Favicon Images node. Local data. DeleteSyncedFavicon@../../chrome/browser/sync/glue/favicon_cache.cc:1014could not find entry matching the lookup criteria.
[4394:4394:0418/180936:ERROR:generic_change_processor.cc(220)] Favicon Images datatype error was encountered: Failed to delete Favicon Images node. Local data. DeleteSyncedFavicon@../../chrome/browser/sync/glue/favicon_cache.cc:1014could not find entry matching the lookup criteria.
[4394:4394:0418/180936:ERROR:generic_change_processor.cc(222)] Delete: Bad entry.
[4394:4394:0418/180936:ERROR:generic_change_processor.cc(289)] Favicon Tracking Failed to delete Favicon Tracking node. Local data. DeleteSyncedFavicon@../../chrome/browser/sync/glue/favicon_cache.cc:1022could not find entry matching the lookup criteria.
[4394:4394:0418/180936:ERROR:generic_change_processor.cc(220)] Favicon Tracking datatype error was encountered: Failed to delete Favicon Tracking node. Local data. DeleteSyncedFavicon@../../chrome/browser/sync/glue/favicon_cache.cc:1022could not find entry matching the lookup criteria.
[4394:4394:0418/180936:ERROR:generic_change_processor.cc(222)] Delete: Bad entry.


(pcmanfm:4391): Gtk-WARNING **: Radio group does not contain an action with value '0'


(openbox:4385): GLib-CRITICAL **: Source ID 7 was not found when attempting to remove it
[WARNING:flash/platform/pepper/pep_module.cpp(63)] SANDBOXED
```

It looks like lxsession is crashing, and causing the login to fail.
I have tried reinstalling lxsession, the problem still persists.

NOTE: I CAN'T login via the default Lubuntu session, but CAN login via the other sessions(LXDE).

EDIT: I forgot to mention that I am also using the proprietary Nvidia drivers.

---

### Post by joshwiker14 on 2014-04-21
I found a solution, I had to disable xcompmgr on startup

this is how i did that:
I browsed to /home/USERNAME/.config/lxsession/Lubuntu
Opened desktop.conf
changed composite_manager/autostart=true to composite_manager/autostart=false
saved
logged out, changed session, and logged in!

---

### Post by diegooo on 2014-10-28
You save my day.

I got this problem as well.

I already had another login agent cause i connect via SSH with VNC server.

Changing [COLOR=#000000]composite_manager/autostart=true to composite_manager/autostart=false in desktop.conf remove the error.

Thx for sharing this.[/COLOR]

---

### Post by joshwiker14 on 2014-10-28
> **diegooo said:**
> You save my day.

I got this problem as well.

I already had another login agent cause i connect via SSH with VNC server.

Changing [COLOR=#000000]composite_manager/autostart=true to composite_manager/autostart=false in desktop.conf remove the error.

Thx for sharing this.[/COLOR]

no prob

---

