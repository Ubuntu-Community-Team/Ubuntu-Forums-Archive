---
title: "Nautilus fails to open sometimes on Unity"
date: 2016-11-17
forum: Desktop Environments
---

### Post by Brandon_MacEachern on 2016-11-17
Every once in a while, Nautilus will fail to open on Unity.  This is happening on both my desktop and laptop.  Both are currently up to date to 16.04 LTS (I am a first responder and can't upgrade to 16.10 yet as my radio gears software isn't compatible right now).

What happens is, either an invisible window for nautilus opens (completely transparent but shows a shadow), OR the icon will just keep pulsing in the launcher, like it's trying to load.  What's weird is that these two computers are entirely different machines with the same exact issue.  Any information you need I will provide.  They are both 64-bit.  I have run memory tests just to rule out hardware issues, but nothing is found.

Here's the system log when this happened.  From when I came to the computer to remove an SD card, and put another in, to just a few minutes ago before posting this (in case it captured anything at all)

```
Nov 17 17:05:01 BrandonsLaptop CRON[11520]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Nov 17 17:08:56 BrandonsLaptop kernel: [341792.217976] mmc0: card b368 removed
Nov 17 17:08:56 BrandonsLaptop udisksd[1929]: Cleaning up mount point /media/brandon/K-3 (device 179:1 no longer exist)
Nov 17 17:08:56 BrandonsLaptop kernel: [341792.416079] FAT-fs (mmcblk0p1): unable to read boot sector to mark fs as dirty
Nov 17 17:09:03 BrandonsLaptop kernel: [341799.486811] mmc0: new high speed SDXC card at address e624
Nov 17 17:09:03 BrandonsLaptop kernel: [341799.487189] mmcblk0: mmc0:e624 SL64G 59.5 GiB 
Nov 17 17:09:03 BrandonsLaptop kernel: [341799.503244]  mmcblk0: p1
Nov 17 17:09:03 BrandonsLaptop udisksd[1929]: Mounted /dev/mmcblk0p1 at /media/brandon/2634-3300 on behalf of uid 1000
Nov 17 17:09:05 BrandonsLaptop dbus[780]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Nov 17 17:09:05 BrandonsLaptop systemd[1]: Starting Hostname Service...
Nov 17 17:09:05 BrandonsLaptop dbus[780]: [system] Successfully activated service 'org.freedesktop.hostname1'
Nov 17 17:09:05 BrandonsLaptop systemd[1]: Started Hostname Service.
Nov 17 17:09:33 BrandonsLaptop gnome-session[1729]: gnome-session-binary[1729]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Nov 17 17:09:33 BrandonsLaptop gnome-session[1729]: gnome-session-binary[1729]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Nov 17 17:09:33 BrandonsLaptop gnome-session-binary[1729]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Nov 17 17:09:33 BrandonsLaptop gnome-session-binary[1729]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Nov 17 17:09:35 BrandonsLaptop gnome-session[1729]: gnome-session-binary[1729]: WARNING: Client '/org/gnome/SessionManager/Client4' failed to reply before timeout
Nov 17 17:09:35 BrandonsLaptop gnome-session-binary[1729]: WARNING: Client '/org/gnome/SessionManager/Client4' failed to reply before timeout
Nov 17 17:09:35 BrandonsLaptop gnome-session[1729]: gnome-session-binary[1729]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Nov 17 17:09:35 BrandonsLaptop gnome-session[1729]: gnome-session-binary[1729]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Nov 17 17:09:35 BrandonsLaptop gnome-session-binary[1729]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Nov 17 17:09:35 BrandonsLaptop gnome-session-binary[1729]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Nov 17 17:09:50 BrandonsLaptop systemd[1]: Stopping Session c2 of user brandon.
Nov 17 17:09:50 BrandonsLaptop NetworkManager[869]: <info>  [1479420590.6221] device (wlp3s0): state change: activated -> deactivating (reason 'connection-removed') [100 110 38]
Nov 17 17:09:50 BrandonsLaptop NetworkManager[869]: <info>  [1479420590.6227] manager: NetworkManager state is now DISCONNECTING
Nov 17 17:09:50 BrandonsLaptop whoopsie[769]: [17:09:50] offline
Nov 17 17:09:50 BrandonsLaptop NetworkManager[869]: <info>  [1479420590.6460] device (wlp3s0): state change: deactivating -> disconnected (reason 'connection-removed') [110 30 38]
Nov 17 17:09:50 BrandonsLaptop avahi-daemon[840]: Withdrawing address record for fe80::e346:9acc:19a8:6807 on wlp3s0.
Nov 17 17:09:50 BrandonsLaptop avahi-daemon[840]: Leaving mDNS multicast group on interface wlp3s0.IPv6 with address fe80::e346:9acc:19a8:6807.
Nov 17 17:09:50 BrandonsLaptop avahi-daemon[840]: Interface wlp3s0.IPv6 no longer relevant for mDNS.
Nov 17 17:09:50 BrandonsLaptop org.gnome.evolution.dataserver.Sources5[1537]: (evolution-source-registry:1815): GLib-GIO-WARNING **: Error releasing name org.gnome.evolution.dataserver.Sources5: The connection is closed
Nov 17 17:09:50 BrandonsLaptop org.gnome.evolution.dataserver.Sources5[1537]: (evolution-source-registry:1815): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Nov 17 17:09:50 BrandonsLaptop org.gnome.evolution.dataserver.Sources5[1537]: (evolution-source-registry:1815): GLib-CRITICAL **: Source ID 1 was not found when attempting to remove it
Nov 17 17:09:50 BrandonsLaptop org.gnome.evolution.dataserver.Sources5[1537]: (evolution-source-registry:1815): GLib-CRITICAL **: Source ID 2 was not found when attempting to remove it
Nov 17 17:09:50 BrandonsLaptop org.gnome.zeitgeist.Engine[1537]: (zeitgeist-daemon:2128): GLib-GIO-WARNING **: Error releasing name org.gnome.zeitgeist.Engine: The connection is closed
Nov 17 17:09:50 BrandonsLaptop org.gnome.zeitgeist.Engine[1537]: #033[31m[22:09:50.662107 WARNING]#033[0m zeitgeist-daemon.vala:449: The connection is closed
Nov 17 17:09:50 BrandonsLaptop org.gnome.zeitgeist.SimpleIndexer[1537]: (zeitgeist-fts:2135): GLib-GIO-WARNING **: Error releasing name org.gnome.zeitgeist.SimpleIndexer: The connection is closed
Nov 17 17:09:50 BrandonsLaptop org.gnome.zeitgeist.SimpleIndexer[1537]: ** (zeitgeist-fts:2135): WARNING **: zeitgeist-fts.vala:252: The connection is closed
Nov 17 17:09:50 BrandonsLaptop pulseaudio[1836]: [pulseaudio] module-x11-publish.c: PulseAudio information vanished from X11!
Nov 17 17:09:50 BrandonsLaptop bluetoothd[768]: Endpoint unregistered: sender=:1.64 path=/MediaEndpoint/A2DPSource
Nov 17 17:09:50 BrandonsLaptop bluetoothd[768]: Endpoint unregistered: sender=:1.64 path=/MediaEndpoint/A2DPSink
Nov 17 17:09:50 BrandonsLaptop systemd[1]: Stopped Session c2 of user brandon.
Nov 17 17:09:50 BrandonsLaptop NetworkManager[869]: <info>  [1479420590.6822] dhcp4 (wlp3s0): canceled DHCP transaction, DHCP client pid 1372
Nov 17 17:09:50 BrandonsLaptop NetworkManager[869]: <info>  [1479420590.6822] dhcp4 (wlp3s0): state changed bound -> done
Nov 17 17:09:50 BrandonsLaptop avahi-daemon[840]: Withdrawing address record for 192.168.1.235 on wlp3s0.
Nov 17 17:09:50 BrandonsLaptop avahi-daemon[840]: Leaving mDNS multicast group on interface wlp3s0.IPv4 with address 192.168.1.235.
Nov 17 17:09:50 BrandonsLaptop avahi-daemon[840]: Interface wlp3s0.IPv4 no longer relevant for mDNS.
Nov 17 17:09:50 BrandonsLaptop NetworkManager[869]: <info>  [1479420590.6834] dns-mgr: Writing DNS information to /sbin/resolvconf
Nov 17 17:09:50 BrandonsLaptop dnsmasq[1398]: setting upstream servers from DBus
Nov 17 17:09:50 BrandonsLaptop lightdm[1077]: ** (lightdm:1077): CRITICAL **: session_get_login1_session_id: assertion 'session != NULL' failed
Nov 17 17:09:50 BrandonsLaptop kernel: [341846.876176] wlp3s0: deauthenticating from 48:f8:b3:b1:95:9c by local choice (Reason: 3=DEAUTH_LEAVING)
Nov 17 17:09:50 BrandonsLaptop systemd[1]: Stopping User Manager for UID 1000...
Nov 17 17:09:50 BrandonsLaptop systemd[1310]: Stopped target Default.
Nov 17 17:09:50 BrandonsLaptop systemd[1310]: Reached target Shutdown.
Nov 17 17:09:50 BrandonsLaptop kernel: [341846.889551] cfg80211: World regulatory domain updated:
Nov 17 17:09:50 BrandonsLaptop kernel: [341846.889554] cfg80211:  DFS Master region: unset
Nov 17 17:09:50 BrandonsLaptop kernel: [341846.889555] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Nov 17 17:09:50 BrandonsLaptop kernel: [341846.889557] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Nov 17 17:09:50 BrandonsLaptop kernel: [341846.889558] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Nov 17 17:09:50 BrandonsLaptop kernel: [341846.889559] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Nov 17 17:09:50 BrandonsLaptop kernel: [341846.889560] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Nov 17 17:09:50 BrandonsLaptop kernel: [341846.889562] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Nov 17 17:09:50 BrandonsLaptop kernel: [341846.889563] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Nov 17 17:09:50 BrandonsLaptop kernel: [341846.889564] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Nov 17 17:09:50 BrandonsLaptop kernel: [341846.889565] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
Nov 17 17:09:50 BrandonsLaptop whoopsie[769]: [17:09:50] Cannot reach: https://daisy.ubuntu.com
Nov 17 17:09:50 BrandonsLaptop systemd[1310]: Stopped target Basic System.
Nov 17 17:09:50 BrandonsLaptop wpa_supplicant[1014]: wlp3s0: CTRL-EVENT-DISCONNECTED bssid=48:f8:b3:b1:95:9c reason=3 locally_generated=1
Nov 17 17:09:50 BrandonsLaptop systemd[1310]: Stopped target Paths.
Nov 17 17:09:50 BrandonsLaptop wpa_supplicant[1014]: p2p-dev-wlp3s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Nov 17 17:09:50 BrandonsLaptop systemd[1310]: Stopped target Timers.
Nov 17 17:09:50 BrandonsLaptop systemd[1310]: Stopped target Sockets.
Nov 17 17:09:50 BrandonsLaptop systemd[1310]: Starting Exit the Session...
Nov 17 17:09:50 BrandonsLaptop systemd[1310]: Received SIGRTMIN+24 from PID 11599 (kill).
Nov 17 17:09:50 BrandonsLaptop NetworkManager[869]: <info>  [1479420590.7056] manager: NetworkManager state is now DISCONNECTED
Nov 17 17:09:50 BrandonsLaptop systemd[1]: Stopped User Manager for UID 1000.
Nov 17 17:09:50 BrandonsLaptop systemd[1]: Removed slice User Slice of brandon.
Nov 17 17:09:50 BrandonsLaptop dbus[780]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Nov 17 17:09:50 BrandonsLaptop NetworkManager[869]: <warn>  [1479420590.7070] sup-iface[0xd14790,wlp3s0]: connection disconnected (reason -3)
Nov 17 17:09:50 BrandonsLaptop NetworkManager[869]: <info>  [1479420590.7070] device (wlp3s0): supplicant interface state: completed -> disconnected
Nov 17 17:09:50 BrandonsLaptop systemd[1]: Starting Network Manager Script Dispatcher Service...
Nov 17 17:09:50 BrandonsLaptop dbus[780]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Nov 17 17:09:50 BrandonsLaptop systemd[1]: Started Network Manager Script Dispatcher Service.
Nov 17 17:09:50 BrandonsLaptop nm-dispatcher: req:1 'down' [wlp3s0]: new request (1 scripts)
Nov 17 17:09:50 BrandonsLaptop nm-dispatcher: req:1 'down' [wlp3s0]: start running ordered scripts...
Nov 17 17:09:50 BrandonsLaptop lightdm[1077]: /etc/modprobe.d is not a file
Nov 17 17:09:50 BrandonsLaptop lightdm[1077]: message repeated 4 times: [ /etc/modprobe.d is not a file]
Nov 17 17:09:51 BrandonsLaptop lightdm[1077]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
Nov 17 17:09:51 BrandonsLaptop lightdm[1077]: NVIDIA-SMI couldn't find libnvidia-ml.so library in your system. Please make sure that the NVIDIA Display Driver is properly installed and present in your system.
Nov 17 17:09:51 BrandonsLaptop lightdm[1077]: Please also try adding directory that contains libnvidia-ml.so to your system PATH.
Nov 17 17:09:51 BrandonsLaptop lightdm[1077]: rmmod: ERROR: Module nvidia_uvm is not currently loaded
Nov 17 17:09:51 BrandonsLaptop lightdm[1077]: rmmod: ERROR: Module nvidia_drm is not currently loaded
Nov 17 17:09:51 BrandonsLaptop lightdm[1077]: rmmod: ERROR: Module nvidia_modeset is not currently loaded
Nov 17 17:09:51 BrandonsLaptop lightdm[1077]: rmmod: ERROR: Module nvidia is not currently loaded
Nov 17 17:09:51 BrandonsLaptop acpid: client 1086[0:0] has disconnected
Nov 17 17:09:51 BrandonsLaptop acpid: client connected from 11682[0:0]
Nov 17 17:09:51 BrandonsLaptop acpid: 1 client rule loaded
Nov 17 17:09:51 BrandonsLaptop systemd[1]: Created slice User Slice of lightdm.
Nov 17 17:09:51 BrandonsLaptop systemd[1]: Starting User Manager for UID 108...
Nov 17 17:09:51 BrandonsLaptop systemd[1]: Started Session c3 of user lightdm.
Nov 17 17:09:51 BrandonsLaptop systemd[11699]: Reached target Timers.
Nov 17 17:09:51 BrandonsLaptop systemd[11699]: Reached target Sockets.
Nov 17 17:09:51 BrandonsLaptop systemd[11699]: Reached target Paths.
Nov 17 17:09:51 BrandonsLaptop systemd[11699]: Reached target Basic System.
Nov 17 17:09:51 BrandonsLaptop systemd[11699]: Reached target Default.
Nov 17 17:09:51 BrandonsLaptop systemd[11699]: Startup finished in 9ms.
Nov 17 17:09:51 BrandonsLaptop systemd[1]: Started User Manager for UID 108.
Nov 17 17:09:51 BrandonsLaptop org.a11y.atspi.Registry[11736]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Nov 17 17:09:51 BrandonsLaptop rtkit-daemon[1232]: Successfully made thread 11806 of process 11806 (n/a) owned by '108' high priority at nice level -11.
Nov 17 17:09:51 BrandonsLaptop rtkit-daemon[1232]: Supervising 1 threads of 1 processes of 1 users.
Nov 17 17:09:51 BrandonsLaptop rtkit-daemon[1232]: Supervising 1 threads of 1 processes of 1 users.
Nov 17 17:09:51 BrandonsLaptop rtkit-daemon[1232]: Successfully made thread 11817 of process 11806 (n/a) owned by '108' RT at priority 5.
Nov 17 17:09:51 BrandonsLaptop rtkit-daemon[1232]: Supervising 2 threads of 1 processes of 1 users.
Nov 17 17:09:51 BrandonsLaptop rtkit-daemon[1232]: Supervising 2 threads of 1 processes of 1 users.
Nov 17 17:09:51 BrandonsLaptop rtkit-daemon[1232]: Successfully made thread 11818 of process 11806 (n/a) owned by '108' RT at priority 5.
Nov 17 17:09:51 BrandonsLaptop rtkit-daemon[1232]: Supervising 3 threads of 1 processes of 1 users.
Nov 17 17:09:51 BrandonsLaptop rtkit-daemon[1232]: Supervising 3 threads of 1 processes of 1 users.
Nov 17 17:09:51 BrandonsLaptop rtkit-daemon[1232]: Successfully made thread 11819 of process 11806 (n/a) owned by '108' RT at priority 5.
Nov 17 17:09:51 BrandonsLaptop rtkit-daemon[1232]: Supervising 4 threads of 1 processes of 1 users.
Nov 17 17:09:51 BrandonsLaptop bluetoothd[768]: Endpoint registered: sender=:1.278 path=/MediaEndpoint/A2DPSource
Nov 17 17:09:51 BrandonsLaptop bluetoothd[768]: Endpoint registered: sender=:1.278 path=/MediaEndpoint/A2DPSink
Nov 17 17:09:51 BrandonsLaptop pulseaudio[11806]: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
Nov 17 17:09:53 BrandonsLaptop org.gtk.vfs.Daemon[11713]: A connection to the bus can't be made
Nov 17 17:09:54 BrandonsLaptop systemd[1]: Created slice User Slice of brandon.
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0112] policy: auto-activating connection 'HomePWN-AC5 1'
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0123] device (wlp3s0): Activation: starting connection 'HomePWN-AC5 1' (848fb038-818b-4c31-8933-4f9469116764)
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0126] device (wlp3s0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 17 17:09:54 BrandonsLaptop kernel: [341850.213732] wlp3s0: authenticate with 48:f8:b3:b1:95:9c
Nov 17 17:09:54 BrandonsLaptop kernel: [341850.215968] wlp3s0: send auth to 48:f8:b3:b1:95:9c (try 1/3)
Nov 17 17:09:54 BrandonsLaptop kernel: [341850.216479] wlp3s0: authenticated
Nov 17 17:09:54 BrandonsLaptop kernel: [341850.218818] wlp3s0: associate with 48:f8:b3:b1:95:9c (try 1/3)
Nov 17 17:09:54 BrandonsLaptop kernel: [341850.219960] wlp3s0: RX AssocResp from 48:f8:b3:b1:95:9c (capab=0x1011 status=0 aid=1)
Nov 17 17:09:54 BrandonsLaptop kernel: [341850.221699] wlp3s0: associated
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0127] manager: NetworkManager state is now CONNECTING
Nov 17 17:09:54 BrandonsLaptop wpa_supplicant[1014]: wlp3s0: SME: Trying to authenticate with 48:f8:b3:b1:95:9c (SSID='HomePWN-AC5' freq=5240 MHz)
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0131] device (wlp3s0): state change: prepare -> config (reason 'none') [40 50 0]
Nov 17 17:09:54 BrandonsLaptop wpa_supplicant[1014]: wlp3s0: Trying to associate with 48:f8:b3:b1:95:9c (SSID='HomePWN-AC5' freq=5240 MHz)
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0132] device (wlp3s0): Activation: (wifi) access point 'HomePWN-AC5 1' has security, but secrets are required.
Nov 17 17:09:54 BrandonsLaptop wpa_supplicant[1014]: wlp3s0: Associated with 48:f8:b3:b1:95:9c
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0133] device (wlp3s0): state change: config -> need-auth (reason 'none') [50 60 0]
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0152] device (wlp3s0): state change: need-auth -> prepare (reason 'none') [60 40 0]
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0154] device (wlp3s0): state change: prepare -> config (reason 'none') [40 50 0]
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0156] device (wlp3s0): Activation: (wifi) connection 'HomePWN-AC5 1' has security, and secrets exist.  No new secrets needed.
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0156] Config: added 'ssid' value 'HomePWN-AC5'
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0156] Config: added 'scan_ssid' value '1'
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0156] Config: added 'key_mgmt' value 'WPA-PSK'
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0156] Config: added 'auth_alg' value 'OPEN'
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0156] Config: added 'psk' value '<omitted>'
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0159] sup-iface[0xd14790,wlp3s0]: config: set interface ap_scan to 1
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0259] device (wlp3s0): supplicant interface state: disconnected -> associating
Nov 17 17:09:54 BrandonsLaptop systemd[1]: Starting User Manager for UID 1000...
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0340] device (wlp3s0): supplicant interface state: associating -> associated
Nov 17 17:09:54 BrandonsLaptop systemd[1]: Started Session c4 of user brandon.
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0395] device (wlp3s0): supplicant interface state: associated -> 4-way handshake
Nov 17 17:09:54 BrandonsLaptop wpa_supplicant[1014]: wlp3s0: WPA: Key negotiation completed with 48:f8:b3:b1:95:9c [PTK=CCMP GTK=CCMP]
Nov 17 17:09:54 BrandonsLaptop wpa_supplicant[1014]: wlp3s0: CTRL-EVENT-CONNECTED - Connection to 48:f8:b3:b1:95:9c completed [id=0 id_str=]
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0451] device (wlp3s0): supplicant interface state: 4-way handshake -> completed
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0452] device (wlp3s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HomePWN-AC5'.
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0452] device (wlp3s0): state change: config -> ip-config (reason 'none') [50 70 0]
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0454] dhcp4 (wlp3s0): activation: beginning transaction (timeout in 45 seconds)
Nov 17 17:09:54 BrandonsLaptop systemd[11844]: Reached target Timers.
Nov 17 17:09:54 BrandonsLaptop systemd[11844]: Reached target Sockets.
Nov 17 17:09:54 BrandonsLaptop systemd[11844]: Reached target Paths.
Nov 17 17:09:54 BrandonsLaptop systemd[11844]: Reached target Basic System.
Nov 17 17:09:54 BrandonsLaptop systemd[11844]: Reached target Default.
Nov 17 17:09:54 BrandonsLaptop systemd[11844]: Startup finished in 9ms.
Nov 17 17:09:54 BrandonsLaptop systemd[1]: Started User Manager for UID 1000.
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0466] dhcp4 (wlp3s0): dhclient started with pid 11850
Nov 17 17:09:54 BrandonsLaptop dhclient[11850]: DHCPREQUEST of 192.168.1.235 on wlp3s0 to 255.255.255.255 port 67 (xid=0xd003541)
Nov 17 17:09:54 BrandonsLaptop dhclient[11850]: DHCPACK of 192.168.1.235 from 192.168.1.1
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0711]   address 192.168.1.235
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0711]   plen 24 (255.255.255.0)
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0711]   gateway 192.168.1.1
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0711]   server identifier 192.168.1.1
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0711]   lease time 86400
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0711]   hostname 'MyLenovoLaptopWifi'
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0711]   nameserver '208.67.222.222'
Nov 17 17:09:54 BrandonsLaptop avahi-daemon[840]: Joining mDNS multicast group on interface wlp3s0.IPv4 with address 192.168.1.235.
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0711]   nameserver '208.67.220.220'
Nov 17 17:09:54 BrandonsLaptop avahi-daemon[840]: New relevant interface wlp3s0.IPv4 for mDNS.
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0711]   nameserver '192.168.1.1'
Nov 17 17:09:54 BrandonsLaptop avahi-daemon[840]: Registering new address record for 192.168.1.235 on wlp3s0.IPv4.
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0711]   domain name 'cfl.rr.com'
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0711] dhcp4 (wlp3s0): state changed unknown -> bound
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0719] device (wlp3s0): state change: ip-config -> ip-check (reason 'none') [70 80 0]
Nov 17 17:09:54 BrandonsLaptop whoopsie[769]: [17:09:54] Cannot reach: https://daisy.ubuntu.com
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0723] device (wlp3s0): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0725] device (wlp3s0): state change: secondaries -> activated (reason 'none') [90 100 0]
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0726] manager: NetworkManager state is now CONNECTED_LOCAL
Nov 17 17:09:54 BrandonsLaptop dhclient[11850]: bound to 192.168.1.235 -- renewal in 36576 seconds.
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0761] manager: NetworkManager state is now CONNECTED_GLOBAL
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0762] policy: set 'HomePWN-AC5 1' (wlp3s0) as default for IPv4 routing and DNS
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.0763] dns-mgr: Writing DNS information to /sbin/resolvconf
Nov 17 17:09:54 BrandonsLaptop dnsmasq[1398]: setting upstream servers from DBus
Nov 17 17:09:54 BrandonsLaptop dnsmasq[1398]: using nameserver 208.67.222.222#53
Nov 17 17:09:54 BrandonsLaptop dnsmasq[1398]: using nameserver 208.67.220.220#53
Nov 17 17:09:54 BrandonsLaptop dnsmasq[1398]: using nameserver 192.168.1.1#53
Nov 17 17:09:54 BrandonsLaptop NetworkManager[869]: <info>  [1479420594.1260] device (wlp3s0): Activation: successful, device activated.
Nov 17 17:09:54 BrandonsLaptop nm-dispatcher: req:2 'up' [wlp3s0]: new request (1 scripts)
Nov 17 17:09:54 BrandonsLaptop nm-dispatcher: req:2 'up' [wlp3s0]: start running ordered scripts...
Nov 17 17:09:54 BrandonsLaptop whoopsie[769]: [17:09:54] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/1
Nov 17 17:09:54 BrandonsLaptop whoopsie[769]: [17:09:54] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/1
Nov 17 17:09:54 BrandonsLaptop whoopsie[769]: [17:09:54] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/1
Nov 17 17:09:54 BrandonsLaptop whoopsie[769]: [17:09:54] online
Nov 17 17:09:54 BrandonsLaptop org.ayatana.bamf[12010]: bamfdaemon start/running, process 12098
Nov 17 17:09:54 BrandonsLaptop systemd[1]: Reloading OpenBSD Secure Shell server.
Nov 17 17:09:54 BrandonsLaptop systemd[1]: Reloaded OpenBSD Secure Shell server.
Nov 17 17:09:54 BrandonsLaptop org.a11y.Bus[12010]: Activating service name='org.a11y.atspi.Registry'
Nov 17 17:09:54 BrandonsLaptop org.a11y.Bus[12010]: ** (process:12132): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Nov 17 17:09:54 BrandonsLaptop org.a11y.Bus[12010]: Successfully activated service 'org.a11y.atspi.Registry'
Nov 17 17:09:54 BrandonsLaptop org.a11y.atspi.Registry[12153]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Nov 17 17:09:54 BrandonsLaptop systemd[1]: Reloading OpenBSD Secure Shell server.
Nov 17 17:09:54 BrandonsLaptop systemd[1]: Reloaded OpenBSD Secure Shell server.
Nov 17 17:09:55 BrandonsLaptop systemd[1]: Started CUPS Scheduler.
Nov 17 17:09:55 BrandonsLaptop rtkit-daemon[1232]: Successfully made thread 12338 of process 12338 (n/a) owned by '1000' high priority at nice level -11.
Nov 17 17:09:55 BrandonsLaptop rtkit-daemon[1232]: Supervising 5 threads of 2 processes of 2 users.
Nov 17 17:09:55 BrandonsLaptop org.gnome.ScreenSaver[12010]: ** (gnome-screensaver:12281): WARNING **: Couldn't get presence status: The name org.gnome.SessionManager was not provided by any .service files
Nov 17 17:09:55 BrandonsLaptop org.gnome.ScreenSaver[12010]: ** (gnome-screensaver:12281): WARNING **: Config key not handled: picture-opacity
Nov 17 17:09:55 BrandonsLaptop org.gnome.ScreenSaver[12010]: ** (gnome-screensaver:12281): WARNING **: Config key not handled: primary-color
Nov 17 17:09:55 BrandonsLaptop org.gnome.ScreenSaver[12010]: ** (gnome-screensaver:12281): WARNING **: Config key not handled: secondary-color
Nov 17 17:09:55 BrandonsLaptop org.gnome.ScreenSaver[12010]: ** (gnome-screensaver:12281): WARNING **: Config key not handled: color-shading-type
Nov 17 17:09:55 BrandonsLaptop org.gnome.ScreenSaver[12010]: ** (gnome-screensaver:12281): WARNING **: Config key not handled: show-notifications
Nov 17 17:09:55 BrandonsLaptop org.gnome.ScreenSaver[12010]: ** (gnome-screensaver:12281): WARNING **: Config key not handled: picture-options
Nov 17 17:09:55 BrandonsLaptop org.gnome.ScreenSaver[12010]: ** (gnome-screensaver:12281): WARNING **: Config key not handled: show-full-name-in-top-bar
Nov 17 17:09:55 BrandonsLaptop org.gnome.ScreenSaver[12010]: ** (gnome-screensaver:12281): WARNING **: Config key not handled: picture-uri
Nov 17 17:09:55 BrandonsLaptop org.gnome.ScreenSaver[12010]: ** (gnome-screensaver:12281): WARNING **: Config key not handled: disable-command-line
Nov 17 17:09:55 BrandonsLaptop org.gnome.ScreenSaver[12010]: ** (gnome-screensaver:12281): WARNING **: Config key not handled: disable-application-handlers
Nov 17 17:09:55 BrandonsLaptop org.gnome.ScreenSaver[12010]: ** (gnome-screensaver:12281): WARNING **: Config key not handled: user-administration-disabled
Nov 17 17:09:55 BrandonsLaptop org.gnome.ScreenSaver[12010]: ** (gnome-screensaver:12281): WARNING **: Config key not handled: disable-printing
Nov 17 17:09:55 BrandonsLaptop org.gnome.ScreenSaver[12010]: ** (gnome-screensaver:12281): WARNING **: Config key not handled: disable-log-out
Nov 17 17:09:55 BrandonsLaptop org.gnome.ScreenSaver[12010]: ** (gnome-screensaver:12281): WARNING **: Config key not handled: disable-print-setup
Nov 17 17:09:55 BrandonsLaptop org.gnome.ScreenSaver[12010]: ** (gnome-screensaver:12281): WARNING **: Config key not handled: disable-save-to-disk
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
Nov 17 17:09:55 BrandonsLaptop rtkit-daemon[1232]: Supervising 5 threads of 2 processes of 2 users.
Nov 17 17:09:55 BrandonsLaptop rtkit-daemon[1232]: Successfully made thread 12373 of process 12338 (n/a) owned by '1000' RT at priority 5.
Nov 17 17:09:55 BrandonsLaptop rtkit-daemon[1232]: Supervising 6 threads of 2 processes of 2 users.
Nov 17 17:09:55 BrandonsLaptop rtkit-daemon[1232]: Supervising 6 threads of 2 processes of 2 users.
Nov 17 17:09:55 BrandonsLaptop rtkit-daemon[1232]: Successfully made thread 12376 of process 12338 (n/a) owned by '1000' RT at priority 5.
Nov 17 17:09:55 BrandonsLaptop rtkit-daemon[1232]: Supervising 7 threads of 2 processes of 2 users.
Nov 17 17:09:55 BrandonsLaptop rtkit-daemon[1232]: Supervising 7 threads of 2 processes of 2 users.
Nov 17 17:09:55 BrandonsLaptop rtkit-daemon[1232]: Successfully made thread 12377 of process 12338 (n/a) owned by '1000' RT at priority 5.
Nov 17 17:09:55 BrandonsLaptop rtkit-daemon[1232]: Supervising 8 threads of 2 processes of 2 users.
Nov 17 17:09:55 BrandonsLaptop bluetoothd[768]: Endpoint registered: sender=:1.306 path=/MediaEndpoint/A2DPSource
Nov 17 17:09:55 BrandonsLaptop bluetoothd[768]: Endpoint registered: sender=:1.306 path=/MediaEndpoint/A2DPSink
Nov 17 17:09:55 BrandonsLaptop pulseaudio[12338]: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
Nov 17 17:09:55 BrandonsLaptop bluetoothd[768]: RFCOMM server failed for Headset Voice gateway: rfcomm_bind: Address already in use (98)
Nov 17 17:09:55 BrandonsLaptop rtkit-daemon[1232]: Successfully made thread 12379 of process 12379 (n/a) owned by '1000' high priority at nice level -11.
Nov 17 17:09:55 BrandonsLaptop rtkit-daemon[1232]: Supervising 9 threads of 3 processes of 2 users.
Nov 17 17:09:55 BrandonsLaptop pulseaudio[12379]: [pulseaudio] pid.c: Daemon already running.
Nov 17 17:09:55 BrandonsLaptop rtkit-daemon[1232]: Successfully made thread 12381 of process 12381 (n/a) owned by '1000' high priority at nice level -11.
Nov 17 17:09:55 BrandonsLaptop rtkit-daemon[1232]: Supervising 9 threads of 3 processes of 2 users.
Nov 17 17:09:55 BrandonsLaptop pulseaudio[12381]: [pulseaudio] pid.c: Daemon already running.
Nov 17 17:09:55 BrandonsLaptop dbus[780]: [system] Activating via systemd: service name='org.freedesktop.locale1' unit='dbus-org.freedesktop.locale1.service'
Nov 17 17:09:55 BrandonsLaptop systemd[1]: Starting Locale Service...
Nov 17 17:09:55 BrandonsLaptop gnome-session-binary[12233]: Entering running state
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: (process:12400): indicator-application-service-WARNING **: Unable to get watcher name 'org.kde.StatusNotifierWatcher'
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: (process:12400): indicator-application-service-WARNING **: Name Lost
Nov 17 17:09:55 BrandonsLaptop dbus[780]: [system] Successfully activated service 'org.freedesktop.locale1'
Nov 17 17:09:55 BrandonsLaptop systemd[1]: Started Locale Service.
Nov 17 17:09:55 BrandonsLaptop org.gtk.vfs.AfcVolumeMonitor[12010]: Volume monitor alive
Nov 17 17:09:55 BrandonsLaptop avahi-daemon[840]: Joining mDNS multicast group on interface wlp3s0.IPv6 with address fe80::e346:9acc:19a8:6807.
Nov 17 17:09:55 BrandonsLaptop avahi-daemon[840]: New relevant interface wlp3s0.IPv6 for mDNS.
Nov 17 17:09:55 BrandonsLaptop avahi-daemon[840]: Registering new address record for fe80::e346:9acc:19a8:6807 on wlp3s0.*.
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: (gnome-software:12399): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: (gnome-software:12399): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Autoprobing TCP port in (all) network interface
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Listening IPv6://[::]:5900
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Listening IPv4://0.0.0.0:5900
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Autoprobing selected port 5900
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Advertising security type: 'TLS' (18)
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Re-binding socket to listen for VNC connections on TCP port 5900 in (all) interface
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Listening IPv6://[::]:5900
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Listening IPv4://0.0.0.0:5900
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Clearing securityTypes
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Advertising security type: 'TLS' (18)
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Clearing securityTypes
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Advertising security type: 'TLS' (18)
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Advertising authentication type: 'No Authentication' (1)
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Re-binding socket to listen for VNC connections on TCP port 5900 in (all) interface
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Listening IPv6://[::]:5900
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Listening IPv4://0.0.0.0:5900
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Clearing securityTypes
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Clearing authTypes
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Advertising security type: 'TLS' (18)
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Advertising authentication type: 'VNC Authentication' (2)
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Clearing securityTypes
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Clearing authTypes
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Advertising security type: 'TLS' (18)
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Advertising authentication type: 'VNC Authentication' (2)
Nov 17 17:09:55 BrandonsLaptop gnome-session[12233]: 17/11/2016 05:09:55 PM Advertising security type: 'VNC Authentication' (2)
Nov 17 17:09:56 BrandonsLaptop org.gnome.ScreenSaver[12010]: ** Message: Lost the name, shutting down.
Nov 17 17:09:57 BrandonsLaptop dbus[780]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Nov 17 17:09:57 BrandonsLaptop systemd[1]: Starting Hostname Service...
Nov 17 17:09:57 BrandonsLaptop gnome-session[12233]: Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)
Nov 17 17:09:57 BrandonsLaptop dbus[780]: [system] Successfully activated service 'org.freedesktop.hostname1'
Nov 17 17:09:57 BrandonsLaptop systemd[1]: Started Hostname Service.
Nov 17 17:09:57 BrandonsLaptop org.gtk.vfs.Daemon[12010]: ** (process:12592): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: Operation not supported by backend
Nov 17 17:09:57 BrandonsLaptop org.gtk.vfs.Daemon[12010]: ** (process:12590): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: Operation not supported by backend
Nov 17 17:09:58 BrandonsLaptop gnome-session[12233]: (nautilus:12403): GnomeDesktop-WARNING **: Unable to create loader for mime type audio/x-wav: Unrecognized image file format
Nov 17 17:09:58 BrandonsLaptop gnome-session[12233]: (nautilus:12403): GnomeDesktop-WARNING **: Error creating thumbnail for file:///media/brandon/2634-3300/message.wav: Unrecognized image file format
Nov 17 17:09:58 BrandonsLaptop gnome-session[12233]: (nautilus:12403): GnomeDesktop-WARNING **: Unable to create loader for mime type audio/x-wav: Unrecognized image file format
Nov 17 17:09:58 BrandonsLaptop gnome-session[12233]: (nautilus:12403): GnomeDesktop-WARNING **: Error creating thumbnail for file:///media/brandon/2634-3300/ringer.wav: Unrecognized image file format
Nov 17 17:10:14 BrandonsLaptop bluetoothd[768]: Endpoint unregistered: sender=:1.278 path=/MediaEndpoint/A2DPSource
Nov 17 17:10:14 BrandonsLaptop bluetoothd[768]: Endpoint unregistered: sender=:1.278 path=/MediaEndpoint/A2DPSink
Nov 17 17:10:15 BrandonsLaptop org.gnome.zeitgeist.Engine[12010]: Performing VACUUM operation... OK
Nov 17 17:10:15 BrandonsLaptop org.gnome.zeitgeist.Engine[12010]: ** (zeitgeist-datahub:12767): WARNING **: zeitgeist-datahub.vala:229: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
Nov 17 17:11:51 BrandonsLaptop systemd[1]: Stopping User Manager for UID 108...
Nov 17 17:11:51 BrandonsLaptop systemd[11699]: Stopped target Default.
Nov 17 17:11:51 BrandonsLaptop systemd[11699]: Stopped target Basic System.
Nov 17 17:11:51 BrandonsLaptop systemd[11699]: Stopped target Sockets.
Nov 17 17:11:51 BrandonsLaptop systemd[11699]: Stopped target Timers.
Nov 17 17:11:51 BrandonsLaptop systemd[11699]: Reached target Shutdown.
Nov 17 17:11:51 BrandonsLaptop systemd[11699]: Starting Exit the Session...
Nov 17 17:11:51 BrandonsLaptop systemd[11699]: Stopped target Paths.
Nov 17 17:11:51 BrandonsLaptop systemd[11699]: Received SIGRTMIN+24 from PID 13269 (kill).
Nov 17 17:11:51 BrandonsLaptop systemd[1]: Stopped User Manager for UID 108.
Nov 17 17:11:51 BrandonsLaptop systemd[1]: Removed slice User Slice of lightdm.
Nov 17 17:12:22 BrandonsLaptop gnome-session[12233]: Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)
Nov 17 17:13:00 BrandonsLaptop udisksd[1929]: Cleaning up mount point /media/brandon/2634-3300 (device 179:1 is not mounted)
Nov 17 17:13:00 BrandonsLaptop udisksd[1929]: Unmounted /dev/mmcblk0p1 on behalf of uid 1000
Nov 17 17:13:05 BrandonsLaptop kernel: [342042.130452] mmc0: card e624 removed
Nov 17 17:13:44 BrandonsLaptop com.canonical.Unity.Scope.Applications[12010]: Error loading package indexes: Couldn't stat '/var/cache/software-center/xapian'
```

Only Nautilus is doing this, no other application installed has frozen once.  In fact, 16.04 is quite stable for all of my software and has worked perfectly fine, it's just Nautilus that keeps requiring me to log out of the computer and log back in.  No restarts required, just a log off / log on.  Kind of at a loss.

---

### Post by mc4man on 2016-11-17
Happens here also, maybe once or twice a week. Haven't yet discovered what's up. Another way to 'fix' is to open system monitor & kill nautilus. (quiting nautilus like in,  nautilus -q doesn't work.

---

### Post by Brandon_MacEachern on 2016-11-17
> **mc4man said:**
> Happens here also, maybe once or twice a week. Haven't yet discovered what's up. Another way to 'fix' is to open system monitor & kill nautilus. (quiting nautilus like in,  nautilus -q doesn't work.

I tried this once, but I couldn't get Nautilus to re-open.  At least I'm not the only one running into this, lol.

---

### Post by pablosquared on 2016-11-22
I've had this too, on both 15.10 and 16.04 - hasn't happened so often in he last few months, but it still occurs. I've just upgraded to 16.10 so I'll monitor for further recurrences.

---

### Post by Brandon_MacEachern on 2016-12-06
Do either of you by any chance have Banshee installed?

It seems it "may" be Banshee, based on my video capture of it happening to me just now.  It seems Banshee and its Music Lens were stalling it, based on the log entries that were showing up here when it happened.  I've always chose Banshee over Rythmbox.  Looks like I may be limited in my music player of choice.

[https://www.youtube.com/watch?v=gJdzED7z9nQ](https://www.youtube.com/watch?v=gJdzED7z9nQ)

I might end up filing the bug myself.

---

### Post by Brandon_MacEachern on 2016-12-07
I have filed a bug report on this.  Those of you who are having the same issue, please chip in:  [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1648215](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1648215)

---

