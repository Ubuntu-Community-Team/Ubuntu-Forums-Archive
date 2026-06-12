---
title: "New X Server &amp; nvidia-settings"
date: 2010-03-24
forum: Desktop Environments
---

### Post by Drunken Pirate on 2010-03-24
Hello,

I am trying to start a game in a new X Server (I know this may belong in Gaming & Leisure but thought this was better place for it.)

Here is my script to launch the game: 

```
#!/bin/sh 

X :3 -ac & nvidia-settings --load-config-only 

# Goto game dir (modify as needed)
cd "/home/brent/.wine/drive_c/Program Files/World of Warcraft/"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game (modify as needed)
ck-launch-session
DISPLAY=:3 WINEDEBUG=-all padsp wine Wow.exe -opengl
```

It creates the new X Server but fails to launch the program with this error:

```
X.Org X Server 1.7.5
Release Date: 2010-02-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux brent-notebook 2.6.32-16-generic #25-Ubuntu SMP Tue Mar 9 16:33:52 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-16-generic root=UUID=74447921-c9c8-40a2-a0fa-26d868df52a0 ro quiet splash
Build Date: 12 March 2010  07:37:07AM
xorg-server 2:1.7.5-1ubuntu3 (buildd@) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.3.log", Time: Wed Mar 24 13:51:24 2010
(==) Using config file: "/etc/X11/xorg.conf"

ERROR: Invalid display device DFP-0 specified on line 46 of configuration file
       '/home/brent/.nvidia-settings-rc' (there are currently no enabled
       display devices on brent-notebook:0.0).


ERROR: Invalid display device DFP-0 specified on line 47 of configuration file
       '/home/brent/.nvidia-settings-rc' (there are currently no enabled
       display devices on brent-notebook:0.0).


ERROR: Invalid display device DFP-0 specified on line 48 of configuration file
       '/home/brent/.nvidia-settings-rc' (there are currently no enabled
       display devices on brent-notebook:0.0).


ERROR: The attribute 'XVideoSyncToDisplay' specified on line 54 of
       configuration file '/home/brent/.nvidia-settings-rc' cannot be assigned
       the value of DFP-0 (the currently enabled display devices are  on
       brent-notebook:0.0).

```

EDIT: Thought it might be a good idea to post my nvidia-settings-rc. It is attached to this post.

Any suggestions on what to do? I would like digital vibrance and similar settings to be applied to this new X Server. Thank you for your time.

---

