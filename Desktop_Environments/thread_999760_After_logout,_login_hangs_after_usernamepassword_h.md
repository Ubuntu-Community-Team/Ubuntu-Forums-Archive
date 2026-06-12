---
title: "After logout, login hangs after username/password has been entered with background co"
date: 2008-12-02
forum: Desktop Environments
---

### Post by weiqigao on 2008-12-02
Hi,

I just installed Ubuntu 8.10 amd64 on my new computer.

I'm having problem logging in after a logout.

After logging out, the login screen appears.

After I enter my username/password the screen turns to the background color with nothing on it but the mouse pointer.  I have to press the power button on the box to restart.

If, instead of logging out, I choose to restart the computer, then I can login normally and reach my desktop.

Any help would be appreciated.

--
Weiqi Gao
[http://www.weiqigao.com/blog/](http://www.weiqigao.com/blog/)

---

### Post by weiqigao on 2008-12-06
Here's some more information.

After I logout and try to login but is stuck with a blank screen (with the Ubuntu-themed background color) and a mouse cursor, I can ssh into the box from another machine.

And here's what I found in the log files:

# in /var/log/kern.log
Dec  6 13:59:02 gao-2009 kernel: [18201.079033] compiz.real[6843] trap stack segment ip:41024e sp:7fff74c12ba0 error:0
Dec  6 13:59:04 gao-2009 kernel: [18203.448685] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
Dec  6 13:59:04 gao-2009 kernel: [18203.723948] set status page addr 0x00033000
Dec  6 13:59:15 gao-2009 kernel: [18214.228353] mtrr: no MTRR for d0000000,10000000 found
Dec  6 13:59:17 gao-2009 kernel: [18216.169514] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
Dec  6 13:59:17 gao-2009 kernel: [18216.445139] set status page addr 0x00033000
Dec  6 13:59:27 gao-2009 kernel: [18225.959611] mtrr: no MTRR for d0000000,10000000 found
Dec  6 13:59:32 gao-2009 kernel: [18231.368117] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
Dec  6 13:59:32 gao-2009 kernel: [18231.643658] set status page addr 0x00033000


# in /var/log/debug
Dec  6 13:59:04 gao-2009 kernel: [18203.723948] set status page addr 0x00033000
Dec  6 13:59:15 gao-2009 kernel: [18214.228353] mtrr: no MTRR for d0000000,10000000 found
Dec  6 13:59:17 gao-2009 kernel: [18216.445139] set status page addr 0x00033000
Dec  6 13:59:27 gao-2009 kernel: [18225.959611] mtrr: no MTRR for d0000000,10000000 found
Dec  6 13:59:32 gao-2009 kernel: [18231.643658] set status page addr 0x0003300


# in /var/log/daemon.log
Dec  6 13:59:02 gao-2009 scim-bridge: Failed to open the panel socket
Dec  6 13:59:03 gao-2009 scim-bridge: Failed to open the panel socket
Dec  6 13:59:03 gao-2009 acpid: client connected from 8760[0:0] 
Dec  6 13:59:04 gao-2009 scim-bridge: Failed to open the panel socket
Dec  6 13:59:04 gao-2009 scim-bridge: Cleanup, done. Exitting...
Dec  6 13:59:05 gao-2009 gdmgreeter[8773]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Dec  6 13:59:16 gao-2009 acpid: client connected from 8786[0:0] 
Dec  6 13:59:18 gao-2009 gdmchooser[8797]: GLib-GObject-WARNING: /build/buildd/glib2.0-2.18.2/gobject/gsignal.c:1152: unable to lookup signal "activate" of unloaded type `GtkMenuItem' 
Dec  6 13:59:31 gao-2009 acpid: client connected from 8812[0:0] 
Dec  6 13:59:33 gao-2009 gdmgreeter[8825]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Dec  6 14:00:08 gao-2009 gnome-session[8845]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout


# in /var/log/auth.log
Dec  6 13:59:58 gao-2009 gdm[8807]: pam_unix(gdm:session): session opened for user weiqi by (uid=0)
Dec  6 13:59:58 gao-2009 gdm[8807]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Dec  6 13:59:58 gao-2009 gdm[8807]: gnome-keyring-daemon: couldn't lookup keyring component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Dec  6 13:59:58 gao-2009 gdm[8807]: Autolaunch error: X11 initialization failed.
Dec  6 13:59:58 gao-2009 gdm[8807]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Dec  6 13:59:58 gao-2009 gdm[8807]: Autolaunch error: X11 initialization failed.
Dec  6 13:59:58 gao-2009 gdm[8807]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Dec  6 13:59:58 gao-2009 gdm[8807]: Autolaunch error: X11 initialization failed.
Dec  6 13:59:58 gao-2009 gdm[8807]: )


# /var/log/gdm/:0.log
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux gao-2009 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec  6 13:59:31 2008
(==) Using config file: "/etc/X11/xorg.conf"
error setting MTRR (base = 0xd0000000, size = 0x10000000, type = 1) Invalid argument (22)
AUDIT: Sat Dec  6 13:59:33 2008: 8812 X: client 4 rejected from local host ( uid=0 gid=0 pid=8827 )
AUDIT: Sat Dec  6 13:59:58 2008: 8812 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=8831 )
AUDIT: Sat Dec  6 13:59:58 2008: 8812 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=8832 )
AUDIT: Sat Dec  6 13:59:58 2008: 8812 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=8833 )

---

### Post by sagematt on 2008-12-07
I have the same problem.

I invite you to subscribe to the bug in Launchpad: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/282081](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/282081)

---

