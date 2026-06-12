---
title: "Problems while modifying ubuntu 12.10 login screen like as Backtrack"
date: 2013-01-28
forum: Desktop Environments
---

### Post by srekcahrai on 2013-01-28
I removed unity and installed gnome in ubuntu 12.10 and I have only root user.

I didn't want the login screen (wanted to make like backtrack) so I editted /etc/default/grub and changed
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```to

```

GRUB_CMDLINE_LINUX_DEFAULT="text"

```I am able to login root from terminal (tty1). And as I input
```

startx

```Ubuntu background and mouse only appears.

But instead inputting startx and inputting this command
```

service gdm start

```then gnome login screen appears and I can login normally. But I don't want the login screen.

How can I make my login same as in Backtrack? Please you can share your ideas.

The result of ~/.xsession-errors
```

Xsession: X session started for root at Mon Jan 28 12:11:24 NPT 2013
localuser:root being added to access control list
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/run/user/root/keyring-eziufh
SSH_AUTH_SOCK=/run/user/root/keyring-eziufh/ssh
GPG_AGENT_INFO=/run/user/root/keyring-eziufh/gpg:0:1
GNOME_KEYRING_CONTROL=/run/user/root/keyring-eziufh
GNOME_KEYRING_PID=1821
GNOME_KEYRING_CONTROL=/run/user/root/keyring-eziufh
SSH_AUTH_SOCK=/run/user/root/keyring-eziufh/ssh
GNOME_KEYRING_CONTROL=/run/user/root/keyring-eziufh
=== xinerama setup Configuration ===
  Clone: false
  Output: Laptop attached to default
     status: on
     width: 1024
     height: 768
     rate: 61
     primary: true
     position: 0 0
=== auto-configure - xinerama mode Configuration ===
  Clone: false
  Output: Laptop attached to default
     status: on
     width: 1024
     height: 768
     rate: 61
     primary: true
     position: 0 0
=== Applying Configuration Configuration ===
  Clone: false
  Output: Laptop attached to default
     status: on
     width: 1024
     height: 768
     rate: 61
     primary: true
     position: 0 0
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp

** (gnome-settings-daemon:1818): WARNING **: Failed to connect context: OK
Initializing tracker-store...
Tracker-Message: Setting up monitor for changes to config file:'/root/.config/tracker/tracker-store.cfg'
Tracker-Message: Setting up monitor for changes to config file:'/root/.config/tracker/tracker-store.cfg'
Starting log:
  File:'/root/.local/share/tracker/tracker-store.log'
Initializing tracker-miner-fs...
Tracker-Message: Setting up monitor for changes to config file:'/root/.config/tracker/tracker-miner-fs.cfg'
Starting log:
  File:'/root/.local/share/tracker/tracker-miner-fs.log'

(gnome-settings-daemon:1818): color-plugin-WARNING **: failed to get edid: unable to get EDID for output

(gnome-settings-daemon:1818): color-plugin-WARNING **: unable to get EDID for xrandr-default: unable to get EDID for output

(gnome-settings-daemon:1818): color-plugin-WARNING **: failed to reset xrandr-default gamma tables: gamma size is zero

(gnome-panel:2120): Gtk-CRITICAL **: gtk_accelerator_parse_with_keycode: assertion `accelerator != NULL' failed

** (gnome-panel:2120): WARNING **: Unable to parse mouse modifier '(null)'

** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon

(gnome-panel:2120): Gtk-CRITICAL **: gtk_accelerator_parse_with_keycode: assertion `accelerator != NULL' failed

** (gnome-panel:2120): WARNING **: Unable to parse mouse modifier '(null)'


(gnome-panel:2120): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.34.1/./gobject/gsignal.c:2459: signal `size_request' is invalid for instance `0x899bf30'
** Message: moving back from GtkStatusIcon to indicator

** (gnome-user-share:2559): WARNING **: gnome-user-share cannot be started as root for security reasons.
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


Received signal:1->'Hangup'
Received signal:1->'Hangup'

(tracker-miner-fs:2110): GVFS-RemoteVolumeMonitor-WARNING **: Owner of volume monitor org.gtk.Private.UDisks2VolumeMonitor disconnected from the bus; removing drives/volumes/mounts

(tracker-miner-fs:2110): GVFS-RemoteVolumeMonitor-WARNING **: Owner of volume monitor org.gtk.Private.GPhoto2VolumeMonitor disconnected from the bus; removing drives/volumes/mounts

```

---

### Post by srekcahrai on 2013-01-29
bump

---

### Post by Cheesemill on 2013-01-29
You should never need to logon as root, especially to a GUI. Have a look at these threads...

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by srekcahrai on 2013-02-01
Thanks a lot for making me aware about security and risks about root user. I have created a new sudo user immediately. But my problem still lies.
> 
I didn't want the login screen (wanted to make like backtrack) so I editted /etc/default/grub and changed.

How can I make my login into CLI?

---

### Post by grahammechanical on 2013-02-02
Perhaps you could explain what you mean by 'like Backtrack.' 

When you run the command

```
startx
```

you start the Xserver and that is why you get to a desktop. But a desktop without Unity because you removed it.

> In simplest terms the startx command is responsible for launching the X session on your computer. The X session is the underpinnings of the graphical desktop environment, without which the graphical desktop would not run.

[http://www.brighthub.com/computing/linux/articles/17895.aspx]("http://www.brighthub.com/computing/linux/articles/17895.aspx")

When you run the command

```
service gdm start
```

you start the Gnome Display Manager. In other words you start the log in screen. The machine is obeying your commands.

May I suggest that you give clearer information about what you want to do. It seems that you are already loading to a Linux command-line. Do you want to install the Backtrack User Interface on Ubuntu?

Regards.

---

### Post by srekcahrai on 2013-02-02
> **grahammechanical said:**
> 
When you run the command

```
service gdm start
```you start the Gnome Display Manager. In other words you start the log in screen. The machine is obeying your commands.


I tried this one before and it worked perfectly. But I wanted gdm to start automatically so I kept in startup too. But as gdm started from the startup there were problems like having two cursors and none of them worked properly. And the screen would be dirty when you move the mouse.

Thanks for your help, grahammechanical. Keep posting.

---

