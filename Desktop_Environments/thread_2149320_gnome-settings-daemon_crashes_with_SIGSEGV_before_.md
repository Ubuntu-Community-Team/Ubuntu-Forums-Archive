---
title: "gnome-settings-daemon crashes with SIGSEGV before session is established"
date: 2013-05-28
forum: Desktop Environments
---

### Post by honzag on 2013-05-28
Hi all,
my problem seems to be similar to this: [http://www.ubuntuupdates.org/package/core/precise/main/proposed/gnome-settings-daemon](http://www.ubuntuupdates.org/package/core/precise/main/proposed/gnome-settings-daemon)   [TABLE="class: gridyellow, width: 100%"]
[TR]
[TH="bgcolor: #EEEEBB"]**Version: **3.4.2-0ubuntu0.6.2[/TH]
[TH="bgcolor: #EEEEBB, align: right"]2013-01-30 18:06:58 UTC[/TH]
[/TR]
[/TABLE]
but I do not use smartcard authentication - just common username/password.
It fails with any user - I have 4 - with different DM : Gnome-classic-with-no-effects, Gnome-classic, Gnome, Unity .
I am able to go thru the first one only - via manual  startinit xinit and gnome-session -f  and even this one crashes but X-windows survive so I can send the event by the ubuntu crash collector (and also  write this thread.

some date:

cd /var/log

root@XCZC2352H3J:/var/log# uname -a
Linux XCZC2352H3J 3.2.0-44-generic #69-Ubuntu SMP Thu May 16 17:35:01 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

root@XCZC2352H3J:/var/log# grep EE Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.483] (II) Loading extension MIT-SCREEN-SAVER


root@XCZC2352H3J:/var/log# grep 'May 28 10:59' kern.log
May 28 10:59:19 XCZC2352H3J kernel: [ 5484.340690] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 28 10:59:19 XCZC2352H3J kernel: [ 5484.342723] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 28 10:59:19 XCZC2352H3J kernel: [ 5484.517987] init: Disconnected from system bus
May 28 10:59:19 XCZC2352H3J kernel: [ 5484.711419] gnome-settings-[6826]: segfault at 8 ip 00007fcb580eaf20 sp 00007fff4a766db0 error 4 in libpower.so[7fcb580db000+18000]
May 28 10:59:19 XCZC2352H3J kernel: [ 5484.776573] init: whoopsie main process ended, respawning
May 28 10:59:19 XCZC2352H3J kernel: [ 5484.797235] init: plymouth-upstart-bridge main process (6849) terminated with status 1
May 28 10:59:19 XCZC2352H3J kernel: [ 5484.950352] gnome-panel[6324]: segfault at 10d028008 ip 00007f689fc93e2d sp 00007fff50c5ee90 error 4 in libglib-2.0.so.0.3200.3[7f689fc33000+f2000]
May 28 10:59:20 XCZC2352H3J kernel: [ 5485.555905] iwlwifi 0000:24:00.0: RF_KILL bit toggled to enable radio.
May 28 10:59:22 XCZC2352H3J kernel: [ 5487.545622] iwlwifi 0000:24:00.0: RF_KILL bit toggled to disable radio.

root@XCZC2352H3J:/var/log# grep 'May 28 10:59' syslog
May 28 10:59:15 XCZC2352H3J AptDaemon: INFO: Quitting due to inactivity
May 28 10:59:15 XCZC2352H3J AptDaemon: INFO: Quitting was requested
May 28 10:59:18 XCZC2352H3J bluetoothd[1037]: Terminating
May 28 10:59:18 XCZC2352H3J NetworkManager[1057]: <info> caught signal 15, shutting down normally.
May 28 10:59:18 XCZC2352H3J NetworkManager[1057]: <warn> quit request received, terminating...
May 28 10:59:18 XCZC2352H3J NetworkManager[1057]: <info> (eth0): now unmanaged
May 28 10:59:18 XCZC2352H3J NetworkManager[1057]: <info> (eth0): device state change: activated -> unmanaged (reason 'removed') [100 10 36]
May 28 10:59:18 XCZC2352H3J bluetoothd[1037]: Stopping SDP server
May 28 10:59:18 XCZC2352H3J bluetoothd[1037]: Exit
May 28 10:59:18 XCZC2352H3J bluez: Stopping uarts
May 28 10:59:19 XCZC2352H3J NetworkManager[1057]: <info> (eth0): deactivating device (reason 'removed') [36]
May 28 10:59:19 XCZC2352H3J dnsmasq[1129]: exiting on receipt of SIGTERM
May 28 10:59:19 XCZC2352H3J NetworkManager[1057]: <info> DNS: starting dnsmasq...
May 28 10:59:19 XCZC2352H3J NetworkManager[1057]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
May 28 10:59:19 XCZC2352H3J dnsmasq[6756]: started, version 2.59 cache disabled
May 28 10:59:19 XCZC2352H3J dnsmasq[6756]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May 28 10:59:19 XCZC2352H3J dnsmasq[6756]: warning: no upstream servers configured
May 28 10:59:19 XCZC2352H3J bluez: Stopping rfcomm
May 28 10:59:19 XCZC2352H3J NetworkManager[1057]: <info> (eth0): cleaning up...
May 28 10:59:19 XCZC2352H3J NetworkManager[1057]: <info> (eth0): taking down device.
May 28 10:59:19 XCZC2352H3J NetworkManager[1057]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
May 28 10:59:19 XCZC2352H3J dbus[1012]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 28 10:59:19 XCZC2352H3J NetworkManager[1057]: <info> (wlan0): now unmanaged
May 28 10:59:19 XCZC2352H3J NetworkManager[1057]: <info> (wlan0): device state change: unavailable -> unmanaged (reason 'removed') [20 10 36]
May 28 10:59:19 XCZC2352H3J NetworkManager[1057]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
May 28 10:59:19 XCZC2352H3J kernel: [ 5484.340690] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 28 10:59:19 XCZC2352H3J kernel: [ 5484.342723] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 28 10:59:19 XCZC2352H3J NetworkManager[1057]: <info> (eth0): removing resolv.conf from /sbin/resolvconf
May 28 10:59:19 XCZC2352H3J dnsmasq[6756]: exiting on receipt of SIGTERM
May 28 10:59:19 XCZC2352H3J dbus[1012]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 28 10:59:19 XCZC2352H3J NetworkManager[1057]: <info> exiting (success)
May 28 10:59:19 XCZC2352H3J nm-dispatcher.action: Caught signal 15, shutting down...
May 28 10:59:19 XCZC2352H3J kernel: [ 5484.517987] init: Disconnected from system bus
May 28 10:59:19 XCZC2352H3J modem-manager[1035]: <info>  Caught signal 15, shutting down...
May 28 10:59:19 XCZC2352H3J kernel: [ 5484.711419] gnome-settings-[6826]: segfault at 8 ip 00007fcb580eaf20 sp 00007fff4a766db0 error 4 in libpower.so[7fcb580db000+18000]
May 28 10:59:19 XCZC2352H3J kernel: [ 5484.776573] init: whoopsie main process ended, respawning
May 28 10:59:19 XCZC2352H3J kernel: [ 5484.797235] init: plymouth-upstart-bridge main process (6849) terminated with status 1
May 28 10:59:19 XCZC2352H3J bluetoothd[6850]: Bluetooth daemon 4.98
May 28 10:59:19 XCZC2352H3J bluetoothd[6850]: Starting SDP server
May 28 10:59:19 XCZC2352H3J bluetoothd[6850]: Failed to init alert plugin
May 28 10:59:19 XCZC2352H3J bluetoothd[6850]: Failed to init time plugin
May 28 10:59:19 XCZC2352H3J bluetoothd[6850]: Failed to init proximity plugin
May 28 10:59:19 XCZC2352H3J bluetoothd[6850]: Failed to init gatt_example plugin
May 28 10:59:19 XCZC2352H3J dbus[6846]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
May 28 10:59:19 XCZC2352H3J dbus[6846]: [system] Successfully activated service 'org.freedesktop.UPower'
May 28 10:59:19 XCZC2352H3J dbus[6846]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
May 28 10:59:19 XCZC2352H3J dbus[6846]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
May 28 10:59:19 XCZC2352H3J polkitd[6882]: started daemon version 0.104 using authority implementation `local' version `0.104'
May 28 10:59:19 XCZC2352H3J dbus[6846]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
May 28 10:59:19 XCZC2352H3J dbus[6846]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
May 28 10:59:19 XCZC2352H3J dbus[6846]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
May 28 10:59:19 XCZC2352H3J dbus[6846]: [system] Successfully activated service 'org.freedesktop.Accounts'
May 28 10:59:19 XCZC2352H3J accounts-daemon[6968]: started daemon version 0.6.15
May 28 10:59:19 XCZC2352H3J kernel: [ 5484.950352] gnome-panel[6324]: segfault at 10d028008 ip 00007f689fc93e2d sp 00007fff50c5ee90 error 4 in libglib-2.0.so.0.3200.3[7f689fc33000+f2000]
May 28 10:59:20 XCZC2352H3J anacron[7044]: Anacron 2.3 started on 2013-05-28
May 28 10:59:20 XCZC2352H3J anacron[7044]: Normal exit (0 jobs run)
May 28 10:59:20 XCZC2352H3J gnome-session[6243]: WARNING: Application 'gnome-panel.desktop' killed by signal
May 28 10:59:20 XCZC2352H3J dbus[6846]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
May 28 10:59:20 XCZC2352H3J dbus[6846]: [system] Successfully activated service 'org.freedesktop.UDisks'
May 28 10:59:20 XCZC2352H3J kernel: [ 5485.555905] iwlwifi 0000:24:00.0: RF_KILL bit toggled to enable radio.
May 28 10:59:21 XCZC2352H3J gnome-session[6243]: WARNING: Application 'gnome-settings-daemon.desktop' killed by signal
May 28 10:59:22 XCZC2352H3J kernel: [ 5487.545622] iwlwifi 0000:24:00.0: RF_KILL bit toggled to disable radio.
May 28 10:59:31 XCZC2352H3J acpid: client 6075[0:0] has disconnected
May 28 10:59:31 XCZC2352H3J acpid: client connected from 6075[0:0]
May 28 10:59:31 XCZC2352H3J acpid: 1 client rule loaded

root@XCZC2352H3J:/var/log# cat gdm/\:0-greeter.log
gnome-session[1576]: WARNING: Failed to start app: Unable to start application: Nelze spustit proces potomka „/usr/lib/at-spi/at-spi-registryd“ (Adresá&#345; nebo soubor neexistuje)
gnome-session[1576]: WARNING: Failed to start app: Unable to start application: Nelze spustit proces potomka „gnome-power-manager“ (Adresá&#345; nebo soubor neexistuje)
Xlib:  extension "NV-GLX" missing on display ":0".


(gnome-settings-daemon:1581): color-plugin-WARNING **: failed to create directory on startup: Chyba p&#345;i vytvá&#345;ení adresá&#345;e: Operace zamítnuta
gdm-simple-greeter[1771]: Gtk-WARNING: Overriding tab label for notebook
gdm-simple-greeter[1771]: Gtk-WARNING: Overriding tab label for notebook
gdm-simple-greeter[1771]: Gtk-WARNING: Overriding tab label for notebook
gdm-simple-greeter[1771]: Gtk-WARNING: Overriding tab label for notebook
gdm-simple-greeter[1771]: Gtk-WARNING: Overriding tab label for notebook


(gnome-settings-daemon:1581): color-plugin-WARNING **: failed to create profile from EDID data: Chyba p&#345;i vytvá&#345;ení adresá&#345;e: Operace zamítnuta


(gnome-settings-daemon:1581): color-plugin-WARNING **: failed to create profile from EDID data: Chyba p&#345;i vytvá&#345;ení adresá&#345;e: Operace zamítnuta
gdm-simple-greeter[1771]: Gtk-WARNING: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkwidget.c:7117: widget not within a GtkWindow
gdm-simple-greeter[1771]: Gtk-CRITICAL: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed
gdm-simple-greeter[1771]: Gtk-CRITICAL: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed
gdm-simple-greeter[1771]: Gtk-WARNING: gtk_widget_size_allocate(): attempt to allocate widget with width -47 and height -47
Varování správce oken: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1000007 (P&#345;ihlašo)
Varování správce oken: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
gdm-simple-greeter[1771]: Gtk-CRITICAL: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed
gdm-simple-greeter[1771]: Gtk-CRITICAL: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed
gdm-simple-greeter[1771]: Gtk-WARNING: gtk_widget_size_allocate(): attempt to allocate widget with width -47 and height -47
gdm-simple-greeter[1771]: CRITICAL: get_column_number: assertion `i < gtk_tree_view_get_n_columns (treeview)' failed
gdm-simple-greeter[1771]: CRITICAL: get_column_number: assertion `i < gtk_tree_view_get_n_columns (treeview)' failed
Varování správce oken: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1000007 (P&#345;ihlašo)
Varování správce oken: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Varování správce oken: CurrentTime used to choose focus window; focus window may not be correct.
Varování správce oken: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.


** (gnome-settings-daemon:1581): WARNING **: Name taken or bus went away - shutting down


(gnome-settings-daemon:1581): libappindicator-WARNING **: Unable to send signal for NewStatus: Spojení bylo ukon&#269;eno



root@XCZC2352H3J:/var/log# set| grep -e ^LANG -e ^LC_ | grep =
LANG=cs_CZ.UTF-8
LANGUAGE=en_US:en:cs_CZ
LC_ADDRESS=cs_CZ.UTF-8
LC_IDENTIFICATION=cs_CZ.UTF-8
LC_MEASUREMENT=cs_CZ.UTF-8
LC_MONETARY=cs_CZ.UTF-8
LC_NAME=cs_CZ.UTF-8
LC_NUMERIC=cs_CZ.UTF-8
LC_PAPER=cs_CZ.UTF-8
LC_TELEPHONE=cs_CZ.UTF-8
LC_TIME=cs_CZ.UTF-8


I am about downgrading [COLOR=#333333][FONT=Ubuntu]**“gnome-settings-daemon" to **[/FONT][/COLOR] 3.4.1  But I prefer some more sophisticated solution.

Can anyone give any suggestion?
Jan

PS. I tried also the lightdm but result was quite similar: I can sign in but after some seconds of invisible activity the login screen re-appears.

---

