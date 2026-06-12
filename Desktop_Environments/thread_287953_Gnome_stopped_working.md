---
title: "Gnome stopped working"
date: 2006-10-29
forum: Desktop Environments
---

### Post by Bloodypriest on 2006-10-29
Yesterday, I finally got a working edgy installation... or so I thought. I was able to login into gnome only once. At that time, I took the opportunity to do some changes to the configuration:

1. I activated my network connection, which had not been correctly activated. Didn't want to have to do dhclient manually every time.

2. I deactivated powernowd since I don't need it (Cool 'n' Quiet is deactivated in my bios).

3. Tried reconfiguring debconf to use the gnome interface but it did not work so I reconfigured it back to the dialog interface.

Next, I rebooted. And I tried to log in again into Gnome. But it never worked. After the log in screen disappeared, the only thing I got was a light brown screen for a while then a grey box in the top left corner of the screen. And then, nothing else, it just froze there forever. I had to kill it with CTRL-ALT-BACKSPACE.

After looking on the web, I found a potential solution on a forum which was to delete .gconf* and .gnome* . Didn't work. The XOrg.0.log was not very informative either as all the errors I got were not fatal. The .xsession-errors was even less informative; the messages it contained were not errors at all.

I am now out of my wits. Please help me.

---

### Post by Bloodypriest on 2006-10-29
UPDATE: Using the xterm failsafe session and duplicating the commands in /usr/share/gnome/default.session , I can manually start gnome. So it would happen that the problem happens even before the session file is read. Even then something is still not right, it takes about 5 minutes for the gnome panel to appear.

According to the error messages I get, it would appear I have a problem with dbus:

```

jean-michel@Marvin:~$ gnome-wm --sm-client-id default0&
[1] 5191
jean-michel@Marvin:~$ gnome-panel --sm-client-id default1&
[2] 5195
jean-michel@Marvin:~$ nautilus --no-default-window --sm-client-id default2&
[3] 5203
jean-michel@Marvin:~$ 
(nautilus:5203): libgnomevfs-WARNING **: Failed to open session DBUS connection: Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)
Volume monitoring will not work.

jean-michel@Marvin:~$ gnome-cups-icon --sm-client-id default3&
[4] 5210
jean-michel@Marvin:~$ gnome-volume-manager --sm-client-id default4&
[5] 5224
jean-michel@Marvin:~$ vino-session --sm-client-id default5&
[6] 5241
[5]   Done                    gnome-volume-manager --sm-client-id default4
jean-michel@Marvin:~$ bash: vino-session: command not found

[6]+  Exit 127                vino-session --sm-client-id default5
jean-michel@Marvin:~$ 
(gnome-panel:5195): libgnomevfs-WARNING **: Failed to open session DBUS connection: Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)
Volume monitoring will not work.

(gnome-panel:5195): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 25
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-1000/socket
This socket already exists indicating esd is already running.
Exiting...

jean-michel@Marvin:~$ 

```

Can someone help me now?

---

### Post by Bloodypriest on 2006-10-29
Finally solved the problem. Finally found out that if I left it alone for 5 minutes so it started after all and that I got more info in the .xsession-errors. Doing so, I also found out that it was related to dbus and gnome-settings-daemon.

So once I was able to start manually gnome-settings-daemon every time I logged in (had to reinstall and reconfigure both dbus and gnome-session), I took a peek again at .xsession-errors and found out that the reason why the darn thing would not start was that I had updated my hostname (in /etc/hostname) but I hadn't updated the alias for 127.0.0.1 in /etc/hosts.

In short, if gnome-settings-daemon doesn't work correctly, a possible cause could be that the alias for 127.0.0.1 in /etc/hosts is different that the hostname in /etc/hostname.

---

