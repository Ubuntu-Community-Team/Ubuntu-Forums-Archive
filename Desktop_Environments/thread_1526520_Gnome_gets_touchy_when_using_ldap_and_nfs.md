---
title: "Gnome gets touchy when using ldap and nfs"
date: 2010-07-08
forum: Desktop Environments
---

### Post by N-t-F on 2010-07-08
Hello everyone, I'm experiencing a strange issue. I suppose it comes from my configuration rather than a bug, but I'm lost.

I have a client (Ubuntu 10.04, 32 bits) connecting to a server (Ubuntu Server Edition 10.04, 64 bits). The client features two kinds of user. The local user is the administrator (named rootlocal) and other users authenticate on the server through LDAP and have their homes on the server thanks to NFS.

Everything works just fine with the local user (luckily!).

But when regular users log into their session, the mouse pointer remains a circle (Ubuntu's hourglass, sort of), the content of the desktop is not displayed (except for the wallpaper) and they can't use graphical applications. The terminal works just fine however and command-line applications can be used (just tried with nano and R).

So, I've tried to experiment a little and here is the result:
1) user with local authentication and local home: everything is ok.
2) user with local authentication and NFS home: graphical applications don't work.
3) user with LDAP authentication and local home: everything is ok.
4) user with LDAP authentication and NFS home: graphical applications don't work.

So the problem seems to be linked to having the home directory served through NFS. I first thought I had a problem with filesystem rights, but using nano to create files work just fine in any of those setups, as well as using mkdir.

At this point, I created an image of my disk and made another experiment: I installed NIS on my client and connected it to my good old NIS/NFS server. Everything worked just fine.

I reloaded my disk image, went back to my first setup (LDAP/NFS) and tried installing XFCE. This worked just fine too, so the problem seems to be related to Gnome, after all.

But my greatest surprise came when I tried to log into Gnome while XFCE was still installed and that worked. :shock: So, installing XFCE or connecting through it seems to have fixed something. I have reloaded my disk image and it doesn't work anymore (so the fix, whatever it could be, wasn't on server side).

I'm completely lost. :frown: The only thing I can think of, right now, is that perhaps some accounts used by Gnome are not given proper rights to write in the home directory of the user?

I don't know what kind of information may help to solve the problem, but I at least post the content of the .xsession-errors after a graphical hang:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=fr_FR.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
gnome-session[1548]: WARNING: Application 'gnome-keyring-secrets.desktop' failed to register before timeout
gnome-session[1548]: WARNING: Application 'gnome-keyring-pkcs11.desktop' failed to register before timeout
gnome-session[1548]: WARNING: Application 'gnome-settings-daemon.desktop' failed to register before timeout
gnome-session[1548]: WARNING: Application 'gnome-keyring-ssh.desktop' failed to register before timeout
gnome-session[1548]: WARNING: Could not launch application 'nm-applet.desktop': Unable to start application: L'exécution du processus fils «*nm-applet*» a échoué (Aucun fichier ou dossier de ce type)

(polkit-gnome-authentication-agent-1:1610): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1610): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gnome-power-manager:1614): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x98e1528'
Avertissement du gestionnaire de fenêtres*: La lecture du fichier de session enregistré /home/tests/test2/.config/metacity/sessions/10c444e7df7d50084127857623518483300000015480027.ms a échoué*: L'ouverture du fichier «*/home/tests/test2/.config/metacity/sessions/10c444e7df7d50084127857623518483300000015480027.ms*» a échoué*: Aucun fichier ou dossier de ce type
Initializing nautilus-gdu extension
Impossible d'ouvrir le fichier de bureau evolution-mail.desktop pour le lanceur du tableau de bord
GNOME_KEYRING_CONTROL=/tmp/keyring-AumKnk
SSH_AUTH_SOCK=/tmp/keyring-AumKnk/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-AumKnk
SSH_AUTH_SOCK=/tmp/keyring-AumKnk/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-AumKnk
SSH_AUTH_SOCK=/tmp/keyring-AumKnk/ssh
gnome-session[1548]: WARNING: Could not launch application 'evolution-alarm-notify.desktop': Unable to start application: L'exécution du processus fils «*/usr/lib/evolution/2.28/evolution-alarm-notify*» a échoué (Aucun fichier ou dossier de ce type)
lock: Aucun verrou disponible
** (update-notifier:1685): DEBUG: Skipping reboot required
lock: Aucun verrou disponible

(gnome-terminal:1702): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed

(nautilus:1699): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
lock: Aucun verrou disponible
lock: Aucun verrou disponible

```

I may try to check what happens if I install XFCE, log into it, then log into Gnome, then uninstall XFCE... Time consuming, but possibly interesting.

---

### Post by N-t-F on 2010-07-08
An update to this. I went to lunch leaving open the regular user session and when I came back one hour or so later, it had displayed the content of the desktop and various elements of the graphical interface were accessible (the menus, mostly). Still, I've tried to launch Open Office, then Firefox, and both seem to hang. I'll let them be for a couple of hours, just to check if things are horribly slow rather than really not working.

I'm still lost, but will try to investigate everything in my configuration that may cause monstrous slowdowns.

Any advice or idea would be welcome, though.

---

### Post by N-t-F on 2010-07-09
Yet another update.

Looks like I've been too quick in considering that everything was fine with XFCE. What's certain is that the desktop is displayed without problem and menus do work from the start. Applications, however, do not all behave appropriately. Gedit, Kile or even Gimp can be used without problem, but others like Firefox or Open Office just freeze when I try to launch them.

Looking at their processes, I have noticed their status was "rpc_wait_bit_killable". Although I have not found what it exactly means, web searches seem to indicate it is related with NFS communication errors or latency. Posts usually refer to some NFSv4 bug, so even though I'm apparently using NFSv3, this gives me a direction for further investigation.

I'm still eager for advice, though.

---

### Post by zoccav on 2010-07-10
Same behaviour here. When the home directory is an NFS share logging hangs. I suppose as I didn't wait an hour like N-t-F did.

Anyway, here's my $0.10 on this.

I compared ~/.xsession-errors files from the user which works and the one which doesn't. The first difference shows up in line 4 where apparently Gnome keyring control is initialised.

I have checked tmp/keyring-*. The OK user has 3 UNIX sockets in the directory (ssh, pkcs11 and control) and the NOT-OK user just has the control UNIX socket.


One wonders whether the home directory affects the Gnome keyring control...


Here's the functioning user's ~/.xsession-errors file.
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-pD3r8K
GNOME_KEYRING_CONTROL=/tmp/keyring-pD3r8K
GNOME_KEYRING_CONTROL=/tmp/keyring-pD3r8K
SSH_AUTH_SOCK=/tmp/keyring-pD3r8K/ssh
Unable to find a synaptics device.

(polkit-gnome-authentication-agent-1:3218): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:3218): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gnome-power-manager:3225): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x99de320'
Initializing nautilus-gdu extension
Starting gtk-window-decorator
I/O warning : failed to load external entity "/xroot/.compiz/session/106ee411b01783c68212787422496935000000031570027"

(gnome-terminal:3310): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed
evolution-alarm-notify-Message: Setting timeout for 64121 1278806400 1278742279
evolution-alarm-notify-Message:  Sun Jul 11 02:00:00 2010

evolution-alarm-notify-Message:  Sat Jul 10 08:11:19 2010

```

And here's the non-functioning user's ~/.xsession-errors file.
```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
gnome-session[2894]: WARNING: Application 'gnome-keyring-ssh.desktop' failed to register before timeout
gnome-session[2894]: WARNING: Application 'gnome-keyring-pkcs11.desktop' failed to register before timeout
gnome-session[2894]: WARNING: Application 'gnome-settings-daemon.desktop' failed to register before timeout
gnome-session[2894]: WARNING: Application 'gnome-keyring-secrets.desktop' failed to register before timeout

(polkit-gnome-authentication-agent-1:2955): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:2955): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gnome-power-manager:2965): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x9e30718'
Initializing nautilus-gdu extension
evolution-alarm-notify-Message: Setting timeout for 64268 1278806400 1278742132
evolution-alarm-notify-Message:  Sun Jul 11 02:00:00 2010

evolution-alarm-notify-Message:  Sat Jul 10 08:08:52 2010

** (update-notifier:3050): DEBUG: Skipping reboot required

```

---

### Post by N-t-F on 2010-07-15
I also wonder about this keyring issue. But I notice that gnome-settings has the very same problem.

I have (successfully) tried again to log into xfce and here is the corresponding .xsession-errors file:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=fr_FR.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/startxfce4: X server already running on display :0
<stdin>:1:3: error: invalid preprocessing directive #Those
<stdin>:2:3: error: invalid preprocessing directive #or
<stdin>:3:3: error: invalid preprocessing directive #Xft
<stdin>:4:3: error: invalid preprocessing directive #Xft

** (gnome-screensaver:1859): WARNING **: Failed to get session presence proxy: Could not get owner of name 'org.gnome.SessionManager': no such name
xfdesktop[1880]: starting up

** (xfce4-session:1863): WARNING **: Unable to launch "nm-applet --sm-disable" (specified by autostart/nm-applet.desktop): L'exécution du processus fils «*nm-applet*» a échoué (Aucun fichier ou dossier de ce type)

(gnome-power-manager:1928): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x862b448'
** (update-notifier:1911): DEBUG: Skipping reboot required

MCS->Xfconf settings migration complete


(polkit-gnome-authentication-agent-1:1985): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1985): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
xfce4-settings-helper is already running

(gnome-terminal:1995): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed
GNOME_KEYRING_CONTROL=/tmp/keyring-bovyr6
SSH_AUTH_SOCK=/tmp/keyring-bovyr6/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-bovyr6
SSH_AUTH_SOCK=/tmp/keyring-bovyr6/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-bovyr6
SSH_AUTH_SOCK=/tmp/keyring-bovyr6/ssh
lock: Aucun verrou disponible
lock: Aucun verrou disponible
```

The home directory is on the nfs server but this time gnome-keyring apparently manages to launch correctly. Now, the fact that I have problems with Firefox and Open Office may be totally unrelated to the issue with nfs. Could be an issue specific to xfce versus those applications.

So, my Gnome client works fine when connected to my old Slackware nfs-server but not with the new Ubuntu 10.04 server. But the same client seems to work with the new server (haven't tried with the old one) if xfce is used instead of Gnome.

In the end, it seems to me that the problem is caused both by the nfs server AND gnome. Looks like they're at each other's throat. Great, innit? :-|

To tell the truth, I'm seriously beginning to consider throwing Ubuntu away as far as my clients are concerned and trying Xubuntu instead, but I suppose there will be problems too, like the ones with Firefox and Open Office... That, and there is apparently a server-side to this problem, which would remain worrying.

---

### Post by N-t-F on 2010-07-16
I've tried to install a simple Ubuntu 10.04 Client from scratch, quick and dirty. I've installed it from a live-CD, made sure the network was working and installed only nfs-kernel-server and its dependencies. Then I created a directory for one of my users in the /home partition and exported it.

Guess what? It works pretty well. The user can log into Gnome and use Firefox just fine.

So, the problem must come from the server, somehow. But it is also Ubuntu 10.04, with the same nfs-kernel-server package installed and the same /etc/exports. The two big differences I can see are that the server uses the 64 bits version of the system while the other one runs the 32 bits version and that I have enabled quotas on the true server and not on the quick and dirty one. If one of those is the cause of the problem, I'm quite desperate because it would be a fool thing to do to run a file server without quotas. Using a client 32 bits version does not seem to be an option either.

Out of curiosity, does anyone here use an Ubuntu Server to serve files through NFS? This would give me hope. :cool:

In the meantime, I keep testing things. :-k

---

### Post by sao104 on 2010-07-19
hi, im new to this....

i've had the same problem, my LDAP account can not enter in graphical session....
i'm using Centos 5.4 64bit as LDAP server as well as NFS server for user's home directories and ubuntu 10.04 32 bit as clients 

before trying on to the 'real' client i'm using VirtualBox to test my server and client configuration, everything works fine... i can login on to LDAP server in gnome session with home directories on NFS server

but when i'm using 'real' client on PC, with the same configuration from VirtualBox, i've had the same problem as you, i can't enter the gnome session, just mouse pointer and wallpaper without desktop contents

so my concern is what is the difference between VirtualBox and 'real' client?

btw, i'm doing your suggestion using xfce but after one minute it hangs, and when i'm running an application it seemed very slow

sorry for bad english...

---

### Post by N-t-F on 2010-07-19
Not that my English is outstanding, either. I guess that it's fine as long as we manage to understand each others correctly. ;)

In order to try my last experiment with a 64 bits system, I have wiped out my server and made a fresh install of it, only configuring basic network interface and installing nfs-kernel-server.

It doesn't work. NFS-based clients hang as soon as they connect to Gnome. I'm formating the server again (to make certain it's absolutely clean) and will reinstall it without quotas this time, just to check if they are responsible of the problem. :s

---

### Post by N-t-F on 2010-07-19
Okay, I have reinstalled the NFS server twice. Once skipping the quota flag on the /home partition and once using ext3 instead of ext4. It did not solve the problem. I even tried editing /etc/hosts.allow to put:

```
portmap: ALL
lockd: ALL
mountd: ALL
statd: ALL
```

which was not necessary on the 32 bits version, anyway.

I give up and consider NFS broken on Ubuntu 10.04 64 bits, unless someone can tell me otherwise. Now, it will be quite a mess to switch to some other distro in time. I may try Debian.

---

### Post by N-t-F on 2010-07-19
Last development: I've installed Debian 5.05 on my server and configured it to serve home through NFS. I still have the timeout message for gnome-keyring failing to register BUT the session does not hang and applications seem to work as intended (including Firefox and Open Office, which were the most annoying).

So, I'll have to create a complete server from there, I'm afraid. :( Hopefully, Debian will be close enough to Ubuntu for my previous tuning to be of use.

I feel I should fill in a bug in Launchpad, too. Never done that and don't really know how to proceed, but I'll check that if I can (still) find enough time.

---

### Post by sao104 on 2010-07-27
> **N-t-F said:**
> 

I give up and consider NFS broken on Ubuntu 10.04 64 bits, unless someone can tell me otherwise. Now, it will be quite a mess to switch to some other distro in time. I may try Debian.

i am now using samba to share my home directories and xfce as my login session, and everithing works fine...:p

---

### Post by zoccav on 2010-08-22
OK, I finally got around this for me.

I tried Fedora-13 (both 64 and 32 bits versions) and had the same problems so I concluded that the distro wasn't the issue but the mounting of the home directory.

I noticed that file locking did not work on the client which mounted the home directory through NFS.

I had to check my FreeBSD server and get file locking going.
1) The ZFS pool had to be configured for NFS share (off topic but included for the sake of completeness):
```
# zpool create home raidz2 da0 da1 da2 da3 da4 da5 da6 da7
# zfs set sharenfs=on home
# zfs set sharenfs="-alldirs -public -maproot=root -network 192.168.1.0 -mask 255.255.255.0" home
```
2) In /etc/rc.conf I added following lines
```
nfs_server_enable="YES"
rpcbind_enable="YES"
rpc_lockd_enable="YES"
rpc_statd_enable="YES"
mountd_enable="YES"
mountd_flags="-r"
```
3) The mountd had to be restarted but I decided to test if everything would after reboot. I was.

On the client the firewall and SE-Linux were both enabled and these interfered with lockd so I disabled both. NOTE: I'm on a private LAN with a firewall so I'm OK with a lower security level on my clients.

To test file locking, install following script as *flocktest*:
```
#!/usr/bin/perl -w

use strict;
use Fcntl ':flock';

open( FH, ">>$ARGV[0]" );

flock( FH, LOCK_EX );
```

Run *flocktest* as:
```

flocktest ~/test.file

```

If the scripts doesn't exit immediately but waits then file locking on file *~/test.file* does not work. Remove file *~/test.file* after testing.

I now have Fedora-13 32 bits working with NFS mounted home directories and I am planning to move to a 64 bits distro.

---

### Post by N-t-F on 2010-08-25
Thanks for the tip!

I have installed Debian 5.05 on the server after my last post and everything has worked fine since then. I have tested your script, out of curiosity, and it did not hang at all. :)

---

### Post by di_dum_dum on 2010-10-06
Hello all,

I had exactly the same problem. I have a 64-bit server and a 32-bit fstab-nfs client as well as a 64-bit autofs-nfs client. On both clients strictly local users could login and nfs folders were accessible, however users with networked home folders got the cursor waiting-circle on login. Finally the desktop would load after ~20 minutes but everything would still be extremely slow and none of the programs (OO/firefox) would run.

I finally fixed it by adding the "nolock" option in fstab/autofs file. No problems since, although I not really sure how this made such a big difference.

Even if this is a bit late, I hope it can help if someone has this problem.

---

