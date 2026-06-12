---
title: "winbind authenticated users can't use gnome"
date: 2010-03-22
forum: Desktop Environments
---

### Post by JimKusz on 2010-03-22
Hi all:

I've recently set up a couple ubuntu 9.10 boxes with the intent of using them as either terminal servers (as part of LTSP or via NX), or just plain old workstations for local users.  

The catch is we have a collection of workstations, and an active directory domain controller that is running as the central authentication server.  I've gotten all the winbind stuff setup, and ssh logins work fine.  However, when a user attempts to log in graphically via gnome/gdm, the session starts to load (the pannels top and bottom appear, sometimes the desktop appears), then the session ends.

The system logs don't show anything.  The only log I can find anything in is the users .xsession-errors file, which spouts tons of errors about dbus issues.  If I create a local user and log in with that, everything works perfectly.  Here is my xsession-errors:

Xsession: X session started for kusznir at Mon Mar 22 16:09:33 PDT 2010
xhost:  must be on local machine to add or remove hosts.
/etc/X11/Xsession.d/80_ltsp-sound: 7: /usr/bin/asoundconf: not found
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
x-session-manager[6415]: devkit-power-gobject-WARNING: Couldn't connect to system bus: Did not receive a
 reply. Possible causes include: the remote application did not send a reply, the message bus security p
olicy blocked the reply, the reply timeout expired, or the network connection was broken.
x-session-manager[6415]: WARNING: Could not connect to ConsoleKit: Did not receive a reply. Possible cau
ses include: the remote application did not send a reply, the message bus security policy blocked the re
ply, the reply timeout expired, or the network connection was broken.
x-session-manager[6415]: WARNING: Could not connect to ConsoleKit: Did not receive a reply. Possible cau
ses include: the remote application did not send a reply, the message bus security policy blocked the re
ply, the reply timeout expired, or the network connection was broken.
GNOME_KEYRING_SOCKET=/tmp/keyring-hhOOWu/socket
SSH_AUTH_SOCK=/tmp/keyring-hhOOWu/socket.ssh
GNOME_KEYRING_PID=6456

(gnome-settings-daemon:6460): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:6460): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Window manager warning: Failed to read saved session file /net/files/home/kusznir/.config/metacity/sessi
ons/10e3109bb545560761126929937424169600000064150022.ms: Failed to open file '/net/files/home/kusznir/.c
onfig/metacity/sessions/10e3109bb545560761126929937424169600000064150022.ms': No such file or directory

** (gnome-panel:6485): WARNING **: Did not receive a reply. Possible causes include: the remote applicat
ion did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, 
or the network connection was broken.
Unable to find a synaptics device.

** (gnome-settings-daemon:6460): WARNING **: pa_context_get_card_info_by_index() failed

(gnome-panel:6485): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume
 monitor with dbus name org.gtk.Private.GduVolumeMonitor: org.freedesktop.DBus.Error.Spawn.ChildSignaled
: Process /usr/lib/gvfs/gvfs-gdu-volume-monitor received signal 11
** (gnome-panel:6485): DEBUG: Adding applet 0.
** (gnome-panel:6485): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:6485): DEBUG: Adding applet 1.

** (polkit-gnome-authentication-agent-1:6505): WARNING **: Error connecting to bus: org.freedesktop.DBus
.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a 
reply, the message bus security policy blocked the reply, the reply timeout expired, or the network conn
ection was broken.

process 6505: arguments to dbus_connection_get_data() were incorrect, assertion "connection != NULL" fai
led in file dbus-connection.c line 5797.
This is normally a bug in some application using the D-Bus library.
process 6505: arguments to dbus_connection_set_data() were incorrect, assertion "connection != NULL" fai
led in file dbus-connection.c line 5761.
This is normally a bug in some application using the D-Bus library.

** ERROR **: Not enough memory to set up DBusConnection for use with GLib
aborting...
** (gnome-panel:6485): DEBUG: Adding applet 2.
** (gnome-panel:6485): DEBUG: Adding applet 3.
** (gnome-panel:6485): DEBUG: Adding applet 4.

(update-notifier:6506): libgdu-WARNING **: Couldn't connect to system bus: Did not receive a reply. Poss
ible causes include: the remote application did not send a reply, the message bus security policy blocke
d the reply, the reply timeout expired, or the network connection was broken.
** (gnome-panel:6485): DEBUG: Adding applet 5.

(gdu-notification-daemon:6509): libgdu-WARNING **: Couldn't connect to system bus: Did not receive a rep
ly. Possible causes include: the remote application did not send a reply, the message bus security polic
y blocked the reply, the reply timeout expired, or the network connection was broken.
*** ERROR ***
TI:16:09:36    TH:0xac6890    FI:gpm-main.c    FN:main,220
 - This program cannot start until you start the dbus system service.
It is <b>strongly recommended</b> you reboot your computer after starting this service.
Traceback:
    gnome-power-manager [0x41c384]
    gnome-power-manager [0x41071e]
    /lib/libc.so.6(__libc_start_main+0xfd) [0x7f9ac1363abd]
    gnome-power-manager [0x4089b9]

(nautilus:6488): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()'
 failed

** (gnome-volume-control-applet:6520): WARNING **: pa_context_get_card_info_by_index() failed
Unable to open desktop file /usr/share/applications/thunderbird.desktop for panel launcher: No such file
 or directory
** (gnome-panel:6485): DEBUG: Adding applet 6.
** (gnome-panel:6485): DEBUG: Adding applet 7.

** (nautilus:6488): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:6488): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:6488): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension

** (bluetooth-applet:6515): WARNING **: Could not open RFKILL control device, please verify your install
ation
Connecting to system bus failed: Did not receive a reply. Possible causes include: the remote applicatio
n did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or
 the network connection was broken.

** (bluetooth-applet:6515): CRITICAL **: dbus_g_proxy_new_for_name: assertion `connection != NULL' faile
d

** (bluetooth-applet:6515): CRITICAL **: dbus_g_proxy_add_signal: assertion `DBUS_IS_G_PROXY (proxy)' fa
iled

** (bluetooth-applet:6515): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)
' failed

** (bluetooth-applet:6515): CRITICAL **: dbus_g_proxy_new_for_name: assertion `connection != NULL' faile
d

** (bluetooth-applet:6515): CRITICAL **: dbus_g_proxy_add_signal: assertion `DBUS_IS_G_PROXY (proxy)' fa
iled

** (bluetooth-applet:6515): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)
' failed

** (bluetooth-applet:6515): CRITICAL **: dbus_g_proxy_add_signal: assertion `DBUS_IS_G_PROXY (proxy)' fa
iled

** (bluetooth-applet:6515): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)
' failed

** (bluetooth-applet:6515): CRITICAL **: dbus_g_proxy_add_signal: assertion `DBUS_IS_G_PROXY (proxy)' fa
iled

** (bluetooth-applet:6515): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)
' failed

** (bluetooth-applet:6515): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (bluetooth-applet:6515): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed
** Message: killswitches state 3

** (nm-applet:6525): WARNING **: <WARN>  bus_init(): Could not get the system bus.  Make sure the messag
e bus daemon is running!  Message: Did not receive a reply. Possible causes include: the remote applicat
ion did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, 
or the network connection was broken.


** (nm-applet:6525): CRITICAL **: nm_remote_settings_system_new: assertion `bus != NULL' failed

** (nm-applet:6525): CRITICAL **: nm_settings_service_export: assertion `priv->bus != NULL' failed

** (nm-applet:6525): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (nm-applet:6525): WARNING **: <WARN>  request_name(): Could not acquire the NetworkManagerUserSetting
s service.
  Error: (-1) (unknown)

x-session-manager[6415]: CRITICAL: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (gnome-panel:6485): WARNING **: Could not ask session manager if shut down is available: Message did 
not receive a reply (timeout by message bus)

(nautilus:6488): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume mo
nitor with dbus name org.gtk.Private.GduVolumeMonitor: org.freedesktop.DBus.Error.Spawn.ChildSignaled: P
rocess /usr/lib/gvfs/gvfs-gdu-volume-monitor received signal 11
Window manager warning: Fatal IO error 11 (Resource temporarily unavailable) on display '192.168.3.133:7
.0'.
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server 192.168.3.133:7.
0.
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server 192.168.3.133:7.0.
canberra-gtk-play: Fatal IO error 11 (Resource temporarily unavailable) on X server 192.168.3.133:7.0.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server 192.168.3.133:7.0.
gnome-volume-control-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server 192.168.3.
133:7.0.
gnome-panel: Fatal IO error 0 (Success) on X server 192.168.3.133:7.0.
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TC
P/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome](http://projects.gnome).
org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection was discon
nected before a reply was received)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TC
P/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome](http://projects.gnome).
org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TC
P/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome](http://projects.gnome).
org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TC
P/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome](http://projects.gnome).
org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TC
P/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome](http://projects.gnome).
org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TC
P/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome](http://projects.gnome).
org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TC
P/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome](http://projects.gnome).
org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TC
P/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome](http://projects.gnome).
org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TC
P/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome](http://projects.gnome).
org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TC
P/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome](http://projects.gnome).
org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TC
P/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome](http://projects.gnome).
org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TC
P/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome](http://projects.gnome).
org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TC
P/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome](http://projects.gnome).
org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TC
P/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome](http://projects.gnome).
org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TC
P/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome](http://projects.gnome).
org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TC
P/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome](http://projects.gnome).
org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TC
P/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome](http://projects.gnome).
org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TC
P/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome](http://projects.gnome).
org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TC
P/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome](http://projects.gnome).
org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TC
P/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome](http://projects.gnome).
org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TC
P/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome](http://projects.gnome).
org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TC
P/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome](http://projects.gnome).
org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TC
P/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome](http://projects.gnome).
org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)

(nautilus:6488): GVFS-RemoteVolumeMonitor-WARNING **: Owner :1.22 of volume monitor org.gtk.Private.GPho
to2VolumeMonitor disconnected from the bus; removing drives/volumes/mounts

(gnome-panel:6485): GLib-GObject-CRITICAL **: g_object_run_dispose: assertion `G_IS_OBJECT (object)' fai
led
Invalid MIT-MAGIC-COOKIE-1 key
(evolution-alarm-notify:6513): Gtk-WARNING **: cannot open display: 192.168.3.133:7.0
---------------------
/etc/samba/smb.conf
---------------------
[global]
        security = ads
        realm = CASAS.WSU.EDU
        password server = ad1.casas.wsu.edu
        workgroup = CASAS
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        idmap backend = rid:CASAS.WSU.EDU=10000-20000
        winbind enum users = yes
        winbind enum groups = yes
        template homedir = /net/files/home/%U
        template shell = /bin/bash
        encrypt passwords = yes
        winbind use default domain = yes

-----------------------
/usr/share/pam-configs/winbind
-----------------------
Name: Winbind (Domain) authentication
Default: yes
Priority: 704
Conflicts: 
Auth-Type: Primary
Auth:
    [success=end default=ignore]    pam_winbind.so try_first_pass krb5_auth krb5_ccache_type=FILE
Auth-Initial:
    [success=end default=ignore]    pam_winbind.so krb5_auth krb5_ccache_type=FILE
Account-Type: Additional
Account:
    sufficient            pam_winbind.so 
Password-Type: Primary
Password:
    requisite            pam_winbind.so 
Password-Initial:
    requisite            pam_winbind.so
Session-Type: Additional
Session:
    required            pam_mkhomedir.so umask=0022

----------------
Again, logging in via SSH works fine; I've also been able to log in with a tdm-looking "rescue" window manager, and it worked.  I don't have kde installed to test against.

I origionally followed the instructions posted on the forum somewhere on how to configure ubuntu for winbind.  I had to tweak them a bit to make it work at all, and then I encapsulated the pam settings in the above file as I would be applying this to several workstations.

Thanks!
--Jim

---

### Post by JimKusz on 2010-03-23
Some updates from further testing.

I installed all of KDE, and tried logging in with KDE.  It does work, although there are several KDE crash daemons as well as error messages from evolution-data-server or something like that.  They all seem to point back to dbus connection problems.

I have also noticed that:

1) getent passwd shows one cohesive password file with both local and remote users in it, all with unique UIDs (as expected);
2) cd ~username for remote users does NOT work, but I can do a getent passwd |grep username and cd to the listed home directory just fine.  On an older cluster of systems running NIS, this is not a problem (ie, cd ~remoteuser works fine).

So, at this point, I don't know if this is a samba/winbind problem, or a dbus/os problem...It may very well be in the wrong catagory on the forum as well, just so far going to the individual projects or #ubuntu on IRC has not turned up any help; I'm not sure where to go now.

--Jim

---

### Post by JimKusz on 2010-03-23
Another update...and more mud in the water.

I'm writing this from another ubuntu 9.10 workstation, set up identically to the one I'm having all the problems on.  I'm in gnome, and logged in via a winbind account...go figure.

Originally, I ran into my original problem cited above, so I built this additional workstation as a clean install to test from.  This workstation worked fine.  All configurations were done identically (I copied most of my config files directly from the non-working system above), and sure enough, it didn't have any of the dbus problems.  In fact, I can also use ~remoteuser in my shell here and it works as well.  (I'm suspecting these are connected).  

So, not being able to find any issue, I reformatted and rebuilt the first system, and again set it up (this time copying the files from this (test) workstation), and the problem remains.

So now I'm really confused.  I've got two identically-configured systems, one works and the other does not.  I've reformatted and rebuilt the non-working one once using the same steps I used to make the working one, and still no-go.  What gives?  There's not much left unchanged: the IP address, host name, and physical hardware....And I don't see any possible cause any of those can have.

--Jim

---

