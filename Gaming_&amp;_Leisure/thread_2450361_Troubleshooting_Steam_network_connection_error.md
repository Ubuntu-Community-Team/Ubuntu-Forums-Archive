---
title: "Troubleshooting Steam network connection error?"
date: 2020-09-12
forum: Gaming &amp; Leisure
---

### Post by sldayo on 2020-09-12
Hello,

I am unable to use Steam on Linux. I tried Ubuntu 20.04 and 20.04.1, Pop!_OS 20.04, Linux Mint 20 Cinnamon, Solus 4.1 Budgie and even SteamOS. I've tried to get help from the Steam community to no avail.

It used to work for me on Ubuntu 20.04 via flatpak only but that stopped working months ago. It worked for a few days on Linux Mint recently and suddenly stopped working.

Installation methods tried: apt, deb package, flatpak, Ubuntu Software.

Steam attempts to log in or connect for a few seconds and then shows the error message "Could not connect to Steam network."

[https://youtu.be/jq7Qsdz1jIs](https://youtu.be/jq7Qsdz1jIs)

Can someone please help me troubleshoot the issue?

Other things I have tried:

[LIST]
[*]Run steam with the "-tcp" parameter. 
[*]Remove the AMD graphics card in my system and only keep the Nvidia one. 
[/LIST]

** System information**

MB: Rampage V Extreme (X99)
CPU: Intel i7-5960X
RAM: Crucial Micron, 32 GB
GPU: Nvidia GTX 1080 Ti (primary), AMD Radeon RX 570 (VFIO)

GPU driver: nvidia-driver-440

Wired 1 Gbps local network and up to 1 Gbps internet.

**Steam error log**

```

Installing breakpad exception handler for appid(steam)/version(1599174997)
Installing breakpad exception handler for appid(steam)/version(1599174997)
Loaded SDL version 2.0.13-5919606
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"

(steam:4200): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
/usr/share/themes/Yaru-dark/gtk-2.0/main.rc:775: error: unexpected identifier `direction', expected character `}'

(steam:4200): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
/usr/share/themes/Yaru-dark/gtk-2.0/hacks.rc:28: error: invalid string constant "normal_entry", expected valid string constant
Installing breakpad exception handler for appid(steam)/version(1599174997)
Fontconfig warning: line 5: unknown element "its:rules"
Fontconfig warning: line 6: unknown element "its:translateRule"
Fontconfig warning: line 9: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/10-hinting-slight.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/10-hinting-slight.conf", line 5: unknown element "its:translateRule"
Fontconfig warning: "/etc/fonts/conf.d/10-hinting-slight.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 5: unknown element "its:translateRule"
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 8: unknown element "description"
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 76: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 76: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 84: saw unknown, expected number
Fontconfig warning: "/etc/fonts/conf.d/11-lcdfilter-default.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/11-lcdfilter-default.conf", line 5: unknown element "its:translateRule"
Fontconfig warning: "/etc/fonts/conf.d/11-lcdfilter-default.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/20-unhint-small-vera.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/20-unhint-small-vera.conf", line 5: unknown element "its:translateRule"
Fontconfig warning: "/etc/fonts/conf.d/20-unhint-small-vera.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/30-metric-aliases.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/30-metric-aliases.conf", line 5: unknown element "its:translateRule"
Fontconfig warning: "/etc/fonts/conf.d/30-metric-aliases.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/40-nonlatin.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/40-nonlatin.conf", line 5: unknown element "its:translateRule"
Fontconfig warning: "/etc/fonts/conf.d/40-nonlatin.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/45-generic.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/45-generic.conf", line 5: unknown element "its:translateRule"
Fontconfig warning: "/etc/fonts/conf.d/45-generic.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/45-latin.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/45-latin.conf", line 5: unknown element "its:translateRule"
Fontconfig warning: "/etc/fonts/conf.d/45-latin.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/49-sansserif.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/49-sansserif.conf", line 5: unknown element "its:translateRule"
Fontconfig warning: "/etc/fonts/conf.d/49-sansserif.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 5: unknown element "its:translateRule"
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/51-local.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/51-local.conf", line 5: unknown element "its:translateRule"
Fontconfig warning: "/etc/fonts/conf.d/51-local.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/60-generic.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/60-generic.conf", line 5: unknown element "its:translateRule"
Fontconfig warning: "/etc/fonts/conf.d/60-generic.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/60-latin.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/60-latin.conf", line 5: unknown element "its:translateRule"
Fontconfig warning: "/etc/fonts/conf.d/60-latin.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/65-fonts-persian.conf", line 34: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/65-fonts-persian.conf", line 35: unknown element "its:translateRule"
Fontconfig warning: "/etc/fonts/conf.d/65-nonlatin.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/65-nonlatin.conf", line 5: unknown element "its:translateRule"
Fontconfig warning: "/etc/fonts/conf.d/65-nonlatin.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/69-unifont.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/69-unifont.conf", line 5: unknown element "its:translateRule"
Fontconfig warning: "/etc/fonts/conf.d/70-no-bitmaps.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/70-no-bitmaps.conf", line 5: unknown element "its:translateRule"
Fontconfig warning: "/etc/fonts/conf.d/70-no-bitmaps.conf", line 8: unknown element "description"
Fontconfig warning: "/etc/fonts/conf.d/80-delicious.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/80-delicious.conf", line 5: unknown element "its:translateRule"
Fontconfig warning: "/etc/fonts/conf.d/90-synthetic.conf", line 4: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/conf.d/90-synthetic.conf", line 5: unknown element "its:translateRule"
Could not connect to X session manager: None of the authentication protocols specified are supported
[0912/162603.619202:INFO:crash_reporting.cc(247)] Crash reporting enabled for process: browser
Installing breakpad exception handler for appid(steam)/version(1599174997)
Installing breakpad exception handler for appid(steam)/version(1599174997)
Installing breakpad exception handler for appid(steam)/version(1599174997)
CAppInfoCacheReadFromDiskThread took 0 milliseconds to initialize
[0912/162603.668741:WARNING:crash_reporting.cc(286)] Failed to set crash key: UserID with value: 0
[0912/162603.668813:WARNING:crash_reporting.cc(286)] Failed to set crash key: BuildID with value: 1599167902
[0912/162603.668819:WARNING:crash_reporting.cc(286)] Failed to set crash key: SteamUniverse with value: Public
[0912/162603.668824:WARNING:crash_reporting.cc(286)] Failed to set crash key: Vendor with value: Valve
Installing breakpad exception handler for appid(steam)/version(1599174997)
Installing breakpad exception handler for appid(steam)/version(1599174997)
CApplicationManagerPopulateThread took 0 milliseconds to initialize (will have waited on CAppInfoCacheReadFromDiskThread)
Installing breakpad exception handler for appid(steam)/version(1599174997)
Installing breakpad exception handler for appid(steam)/version(1599174997)
Installing breakpad exception handler for appid(steam)/version(1599174997)
Warning: failed to set thread priority: set failed for 8: -1: setpriority() failed
Warning: failed to set thread priority: set failed for priority 8
Warning: support for elevated priorities is most likely unavailable, suppressing future warnings
Warning: failed to set thread priority: set failed for 8: -1: setpriority() failed
Installing breakpad exception handler for appid(steam)/version(1599174997)
Installing breakpad exception handler for appid(steam)/version(1599174997)
Installing breakpad exception handler for appid(steam)/version(1599174997)
Installing breakpad exception handler for appid(steam)/version(1599174997)
/usr/lib/x86_64-linux-gnu/gio/modules/libgiognutls.so: undefined symbol: g_datagram_based_create_source
Failed to load module: /usr/lib/x86_64-linux-gnu/gio/modules/libgiognutls.so
/usr/lib/x86_64-linux-gnu/gio/modules/libgiognomeproxy.so: undefined symbol: g_task_set_name
Failed to load module: /usr/lib/x86_64-linux-gnu/gio/modules/libgiognomeproxy.so
/usr/lib/x86_64-linux-gnu/gio/modules/libdconfsettings.so: undefined symbol: g_log_structured_standard
Failed to load module: /usr/lib/x86_64-linux-gnu/gio/modules/libdconfsettings.so
/usr/lib/x86_64-linux-gnu/gio/modules/libgvfsdbus.so: undefined symbol: g_date_time_format_iso8601
Failed to load module: /usr/lib/x86_64-linux-gnu/gio/modules/libgvfsdbus.so
/usr/lib/x86_64-linux-gnu/gio/modules/libgioremote-volume-monitor.so: undefined symbol: g_mount_operation_get_is_tcrypt_system_volume
Failed to load module: /usr/lib/x86_64-linux-gnu/gio/modules/libgioremote-volume-monitor.so
Installing breakpad exception handler for appid(steam)/version(1599174997)
/usr/lib/x86_64-linux-gnu/gio/modules/libgiolibproxy.so: undefined symbol: g_task_set_name
Failed to load module: /usr/lib/x86_64-linux-gnu/gio/modules/libgiolibproxy.so
Proceed to auto login
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.

** (steam:4200): WARNING **: Unknown device type 13

** (steam:4200): WARNING **: Could not create object for /org/freedesktop/NetworkManager/Devices/4: unknown object type

** (steam:4200): WARNING **: handle_property_changed: failed to update property 'devices' of object type NMActiveConnection.

** (steam:4200): WARNING **: Unknown device type 14

** (steam:4200): WARNING **: Could not create object for /org/freedesktop/NetworkManager/Devices/1: unknown object type

** (steam:4200): WARNING **: Unknown device type 13

** (steam:4200): WARNING **: Could not create object for /org/freedesktop/NetworkManager/Devices/4: unknown object type

** (steam:4200): WARNING **: Unknown device type 16

** (steam:4200): WARNING **: Could not create object for /org/freedesktop/NetworkManager/Devices/5: unknown object type
[0912/162603.817154:WARNING:crash_reporting.cc(286)] Failed to set crash key: UserID with value: 0
[0912/162603.817237:WARNING:crash_reporting.cc(286)] Failed to set crash key: BuildID with value: 1599167902
[0912/162603.817244:WARNING:crash_reporting.cc(286)] Failed to set crash key: SteamUniverse with value: Public
[0912/162603.817249:WARNING:crash_reporting.cc(286)] Failed to set crash key: Vendor with value: Valve
[0912/162603.817913:INFO:crash_reporting.cc(247)] Crash reporting enabled for process: gpu-process
Could not connect to X session manager: None of the authentication protocols specified are supported
Opted-in Controller Mask for AppId 0: 0
Could not connect to X session manager: None of the authentication protocols specified are supported
Installing breakpad exception handler for appid(steam)/version(1599174997)
[0912/162604.153880:WARNING:crash_reporting.cc(286)] Failed to set crash key: UserID with value: 0
[0912/162604.153950:WARNING:crash_reporting.cc(286)] Failed to set crash key: BuildID with value: 1599167902
[0912/162604.153957:WARNING:crash_reporting.cc(286)] Failed to set crash key: SteamUniverse with value: Public
[0912/162604.153962:WARNING:crash_reporting.cc(286)] Failed to set crash key: Vendor with value: Valve
[0912/162604.155285:INFO:crash_reporting.cc(247)] Crash reporting enabled for process: utility

** (steam:4200): WARNING **: Ignoring invalid property 'autoconnect-priority'

** (steam:4200): WARNING **: Ignoring invalid property 'interface-name'

** (steam:4200): WARNING **: Unknown setting 'proxy'

** (steam:4200): WARNING **: Ignoring invalid property 'route-data'

** (steam:4200): WARNING **: Ignoring invalid property 'address-data'

** (steam:4200): WARNING **: Ignoring invalid property 'route-data'

** (steam:4200): WARNING **: Ignoring invalid property 'address-data'

** (steam:4200): WARNING **: Ignoring invalid property 'route-data'

** (steam:4200): WARNING **: Ignoring invalid property 'address-data'

** (steam:4200): WARNING **: Unknown setting 'proxy'

** (steam:4200): WARNING **: Ignoring invalid property 'route-data'

** (steam:4200): WARNING **: Ignoring invalid property 'address-data'

** (steam:4200): WARNING **: Ignoring invalid property 'interface-name'

** (steam:4200): WARNING **: Unknown setting 'proxy'

** (steam:4200): WARNING **: Ignoring invalid property 'route-data'

** (steam:4200): WARNING **: Ignoring invalid property 'address-data'

** (steam:4200): WARNING **: Ignoring invalid property 'route-data'

** (steam:4200): WARNING **: Ignoring invalid property 'address-data'

** (steam:4200): WARNING **: Ignoring invalid property 'interface-name'

** (steam:4200): WARNING **: Unknown setting 'proxy'

** (steam:4200): WARNING **: Ignoring invalid property 'route-data'

** (steam:4200): WARNING **: Ignoring invalid property 'dns-priority'

** (steam:4200): WARNING **: Ignoring invalid property 'address-data'

** (steam:4200): WARNING **: Ignoring invalid property 'route-data'

** (steam:4200): WARNING **: Ignoring invalid property 'dns-priority'

** (steam:4200): WARNING **: Ignoring invalid property 'address-data'

** (steam:4200): WARNING **: Unknown setting 'bridge'

** (steam:4200): WARNING **: replace_settings: error updating connection /org/freedesktop/NetworkManager/Settings/4 settings: (3) type

** (steam:4200): WARNING **: Ignoring invalid property 'autoconnect-priority'

** (steam:4200): WARNING **: Ignoring invalid property 'interface-name'

** (steam:4200): WARNING **: Unknown setting 'proxy'

** (steam:4200): WARNING **: Ignoring invalid property 'route-data'

** (steam:4200): WARNING **: Ignoring invalid property 'address-data'

** (steam:4200): WARNING **: Ignoring invalid property 'route-data'

** (steam:4200): WARNING **: Ignoring invalid property 'address-data'

** (steam:4200): WARNING **: Ignoring invalid property 'route-data'

** (steam:4200): WARNING **: Ignoring invalid property 'address-data'

** (steam:4200): WARNING **: Unknown setting 'proxy'

** (steam:4200): WARNING **: Ignoring invalid property 'route-data'

** (steam:4200): WARNING **: Ignoring invalid property 'address-data'

** (steam:4200): WARNING **: Ignoring invalid property 'interface-name'

** (steam:4200): WARNING **: Unknown setting 'proxy'

** (steam:4200): WARNING **: Ignoring invalid property 'route-data'

** (steam:4200): WARNING **: Ignoring invalid property 'address-data'

** (steam:4200): WARNING **: Ignoring invalid property 'route-data'

** (steam:4200): WARNING **: Ignoring invalid property 'address-data'

** (steam:4200): WARNING **: Ignoring invalid property 'interface-name'

** (steam:4200): WARNING **: Unknown setting 'proxy'

** (steam:4200): WARNING **: Ignoring invalid property 'route-data'

** (steam:4200): WARNING **: Ignoring invalid property 'dns-priority'

** (steam:4200): WARNING **: Ignoring invalid property 'address-data'

** (steam:4200): WARNING **: Ignoring invalid property 'route-data'

** (steam:4200): WARNING **: Ignoring invalid property 'dns-priority'

** (steam:4200): WARNING **: Ignoring invalid property 'address-data'

** (steam:4200): WARNING **: Unknown setting 'bridge'

** (steam:4200): WARNING **: replace_settings: error updating connection /org/freedesktop/NetworkManager/Settings/4 settings: (3) type
Installing breakpad exception handler for appid(steam)/version(1599174997)

(steam:4200): Gtk-WARNING **: gtk_disable_setlocale() must be called before gtk_init()
Installing breakpad exception handler for appid(steam)/version(1599174997)
Installing breakpad exception handler for appid(steam)/version(1599174997)
Installing breakpad exception handler for appid(steam)/version(1599174997)
Could not connect to X session manager: None of the authentication protocols specified are supported
Could not connect to X session manager: None of the authentication protocols specified are supported
Exiting workitem thread

```

---

### Post by mastablasta on 2020-09-14
don't ask steam community, ask steam.

in any case, are you running any GUI applications as root? is your IP static or dynamic? 

what is the current install you used in the log above? is this from software center?

---

### Post by sldayo on 2020-09-14
Thanks for your reply.

I am not running any GUI apps as root.

Dynamic IP on the WAN and a static local IP is mapped in the router's DNS server.

The current install method was "sudo apt install steam".

```

$ ps -u root
    PID TTY          TIME CMD
      1 ?        00:01:07 systemd
      2 ?        00:00:00 kthreadd
      3 ?        00:00:00 rcu_gp
      4 ?        00:00:00 rcu_par_gp
      6 ?        00:00:00 kworker/0:0H-kblockd
      9 ?        00:00:00 mm_percpu_wq
     10 ?        00:00:01 ksoftirqd/0
     11 ?        00:00:29 rcu_sched
     12 ?        00:00:00 migration/0
     13 ?        00:00:00 idle_inject/0
     14 ?        00:00:00 cpuhp/0
     15 ?        00:00:00 cpuhp/1
     16 ?        00:00:00 idle_inject/1
     17 ?        00:00:00 migration/1
     18 ?        00:00:00 ksoftirqd/1
     20 ?        00:00:00 kworker/1:0H-kblockd
     21 ?        00:00:00 cpuhp/2
     22 ?        00:00:00 idle_inject/2
     23 ?        00:00:00 migration/2
     24 ?        00:00:00 ksoftirqd/2
     26 ?        00:00:00 kworker/2:0H-kblockd
     27 ?        00:00:00 cpuhp/3
     28 ?        00:00:00 idle_inject/3
     29 ?        00:00:00 migration/3
     30 ?        00:00:00 ksoftirqd/3
     32 ?        00:00:00 kworker/3:0H-kblockd
     33 ?        00:00:00 cpuhp/4
     34 ?        00:00:00 idle_inject/4
     35 ?        00:00:00 migration/4
     36 ?        00:00:00 ksoftirqd/4
     38 ?        00:00:00 kworker/4:0H-kblockd
     39 ?        00:00:00 cpuhp/5
     40 ?        00:00:00 idle_inject/5
     41 ?        00:00:00 migration/5
     42 ?        00:00:00 ksoftirqd/5
     44 ?        00:00:00 kworker/5:0H-kblockd
     45 ?        00:00:00 cpuhp/6
     46 ?        00:00:00 idle_inject/6
     47 ?        00:00:00 migration/6
     48 ?        00:00:00 ksoftirqd/6
     50 ?        00:00:00 kworker/6:0H-kblockd
     51 ?        00:00:00 cpuhp/7
     52 ?        00:00:00 idle_inject/7
     53 ?        00:00:00 migration/7
     54 ?        00:00:00 ksoftirqd/7
     56 ?        00:00:00 kworker/7:0H-kblockd
     57 ?        00:00:00 cpuhp/8
     58 ?        00:00:00 idle_inject/8
     59 ?        00:00:00 migration/8
     60 ?        00:00:00 ksoftirqd/8
     62 ?        00:00:00 kworker/8:0H-kblockd
     63 ?        00:00:00 cpuhp/9
     64 ?        00:00:00 idle_inject/9
     65 ?        00:00:00 migration/9
     66 ?        00:00:00 ksoftirqd/9
     68 ?        00:00:00 kworker/9:0H-kblockd
     69 ?        00:00:00 cpuhp/10
     70 ?        00:00:00 idle_inject/10
     71 ?        00:00:00 migration/10
     72 ?        00:00:00 ksoftirqd/10
     74 ?        00:00:00 kworker/10:0H-kblockd
     75 ?        00:00:00 cpuhp/11
     76 ?        00:00:00 idle_inject/11
     77 ?        00:00:00 migration/11
     78 ?        00:00:00 ksoftirqd/11
     80 ?        00:00:00 kworker/11:0H-kblockd
     81 ?        00:00:00 cpuhp/12
     82 ?        00:00:00 idle_inject/12
     83 ?        00:00:00 migration/12
     84 ?        00:00:00 ksoftirqd/12
     86 ?        00:00:00 kworker/12:0H-kblockd
     87 ?        00:00:00 cpuhp/13
     88 ?        00:00:00 idle_inject/13
     89 ?        00:00:00 migration/13
     90 ?        00:00:00 ksoftirqd/13
     92 ?        00:00:00 kworker/13:0H-kblockd
     93 ?        00:00:00 cpuhp/14
     94 ?        00:00:00 idle_inject/14
     95 ?        00:00:00 migration/14
     96 ?        00:00:00 ksoftirqd/14
     98 ?        00:00:00 kworker/14:0H-kblockd
     99 ?        00:00:00 cpuhp/15
    100 ?        00:00:00 idle_inject/15
    101 ?        00:00:00 migration/15
    102 ?        00:00:00 ksoftirqd/15
    104 ?        00:00:00 kworker/15:0H-kblockd
    105 ?        00:00:00 kdevtmpfs
    106 ?        00:00:00 netns
    107 ?        00:00:00 rcu_tasks_kthre
    108 ?        00:00:00 kauditd
    111 ?        00:00:00 khungtaskd
    112 ?        00:00:00 oom_reaper
    113 ?        00:00:00 writeback
    114 ?        00:00:00 kcompactd0
    115 ?        00:00:00 ksmd
    116 ?        00:00:00 khugepaged
    163 ?        00:00:00 kintegrityd
    164 ?        00:00:00 kblockd
    165 ?        00:00:00 blkcg_punt_bio
    179 ?        00:00:00 tpm_dev_wq
    180 ?        00:00:00 ata_sff
    181 ?        00:00:00 md
    182 ?        00:00:00 edac-poller
    183 ?        00:00:00 devfreq_wq
    184 ?        00:00:00 watchdogd
    186 ?        00:00:00 kswapd0
    187 ?        00:00:00 ecryptfs-kthrea
    189 ?        00:00:00 kthrotld
    190 ?        00:00:00 irq/25-aerdrv
    191 ?        00:00:00 irq/26-aerdrv
    192 ?        00:00:00 irq/28-aerdrv
    193 ?        00:00:00 irq/30-aerdrv
    194 ?        00:00:00 acpi_thermal_pm
    195 ?        00:00:00 vfio-irqfd-clea
    200 ?        00:00:00 ipv6_addrconf
    209 ?        00:00:00 kstrp
    212 ?        00:00:04 kworker/u33:0-uvcvideo
    228 ?        00:00:00 charger_manager
    305 ?        00:00:00 nvme-wq
    306 ?        00:00:00 nvme-reset-wq
    307 ?        00:00:00 nvme-delete-wq
    309 ?        00:00:00 cryptd
    310 ?        00:00:00 scsi_eh_0
    311 ?        00:00:00 scsi_tmf_0
    312 ?        00:00:00 scsi_eh_1
    313 ?        00:00:00 scsi_tmf_1
    314 ?        00:00:00 scsi_eh_2
    315 ?        00:00:00 scsi_tmf_2
    316 ?        00:00:00 scsi_eh_3
    317 ?        00:00:00 scsi_tmf_3
    318 ?        00:00:00 scsi_eh_4
    319 ?        00:00:00 scsi_tmf_4
    320 ?        00:00:00 scsi_eh_5
    321 ?        00:00:00 scsi_tmf_5
    328 ?        00:00:00 scsi_eh_6
    329 ?        00:00:00 scsi_tmf_6
    330 ?        00:00:00 scsi_eh_7
    331 ?        00:00:00 scsi_tmf_7
    338 ?        00:00:00 kworker/5:2-mm_percpu_wq
    360 ?        00:00:00 kworker/10:1H-kblockd
    362 ?        00:00:00 kworker/7:1H-kblockd
    364 ?        00:00:00 uas
    365 ?        00:00:00 scsi_eh_8
    366 ?        00:00:00 scsi_tmf_8
    419 ?        00:00:00 kworker/9:1H-kblockd
    420 ?        00:00:00 kworker/1:1H-kblockd
    421 ?        00:00:00 kworker/3:1H-kblockd
    422 ?        00:00:00 kworker/12:1H-kblockd
    487 ?        00:00:00 kdmflush
    494 ?        00:00:00 kcryptd_io/253:
    495 ?        00:00:00 kcryptd/253:0
    496 ?        00:00:04 dmcrypt_write/2
    499 ?        00:00:00 kdmflush
    501 ?        00:00:00 kdmflush
    543 ?        00:00:05 jbd2/dm-1-8
    544 ?        00:00:00 ext4-rsv-conver
    596 ?        00:00:02 systemd-journal
    617 ?        00:00:00 kworker/4:1H-kblockd
    625 ?        00:00:00 kworker/5:1H-kblockd
    631 ?        00:00:01 systemd-udevd
    682 ?        00:00:00 loop0
    707 ?        00:00:00 loop1
    711 ?        00:00:00 loop2
    713 ?        00:00:00 loop3
    714 ?        00:00:00 kworker/14:1H-kblockd
    717 ?        00:00:00 kworker/11:1H-kblockd
    718 ?        00:00:00 kworker/2:1H-kblockd
    719 ?        00:00:00 kworker/6:1H-kblockd
    720 ?        00:00:00 kworker/15:1H-kblockd
    721 ?        00:00:00 loop4
    735 ?        00:00:00 loop5
    736 ?        00:00:00 irq/66-mei_me
    751 ?        00:00:00 cfg80211
    774 ?        00:00:00 loop6
    777 ?        00:00:00 loop7
    811 ?        00:00:00 led_workqueue
    839 ?        00:00:00 wl_event_handle
    847 ?        00:00:00 kworker/u33:1-hci0
    932 ?        00:00:00 nv_queue
    937 ?        00:00:00 nv_queue
    989 ?        00:00:00 nvidia-modeset/
    990 ?        00:00:00 nvidia-modeset/
   1017 ?        00:00:00 kworker/8:1H-kblockd
   1019 ?        00:00:00 kworker/13:1H-kblockd
   1023 ?        00:00:00 loop8
   1040 ?        00:00:00 loop9
   1044 ?        00:00:00 loop10
   1045 ?        00:00:00 loop11
   1046 ?        00:00:00 loop12
   1048 ?        00:00:00 jbd2/nvme0n1p2-
   1049 ?        00:00:00 ext4-rsv-conver
   1052 ?        00:00:00 loop13
   1053 ?        00:00:00 loop14
   1054 ?        00:00:00 loop15
   1055 ?        00:00:00 loop16
   1056 ?        00:00:00 loop17
   1057 ?        00:00:00 loop18
   1058 ?        00:00:00 loop19
   1059 ?        00:00:00 loop20
   1060 ?        00:00:00 kworker/0:1H-kblockd
   1146 ?        00:00:00 accounts-daemon
   1147 ?        00:00:03 acpid
   1154 ?        00:00:00 bluetoothd
   1155 ?        00:00:00 cron
   1162 ?        00:00:17 NetworkManager
   1169 ?        00:00:04 irqbalance
   1172 ?        00:00:00 networkd-dispat
   1179 ?        00:00:01 polkitd
   1188 ?        00:00:12 snapd
   1189 ?        00:00:00 switcheroo-cont
   1191 ?        00:00:01 systemd-logind
   1192 ?        00:00:00 systemd-machine
   1194 ?        00:00:13 udisksd
   1196 ?        00:00:00 wpa_supplicant
   1250 ?        00:00:00 ModemManager
   1257 ?        00:00:00 sshd
   1267 ?        00:00:00 gdm3
   1309 ?        00:00:00 libvirtd
   1310 ?        00:00:00 unattended-upgr
   1311 ?        00:00:00 gdm-session-wor
   1359 ?        00:00:00 none
   1429 tty1     00:00:01 Xorg
   1514 ?        00:00:00 dnsmasq
   1525 ?        00:07:38 irq/67-nvidia
   1527 ?        00:00:00 nvidia
   1528 ?        00:14:48 nv_queue
   1594 ?        00:00:00 upowerd
   1964 ?        00:01:07 expressvpnd
   1968 ?        00:00:00 starter
   1991 ?        00:00:00 charon
   1997 ?        00:00:00 xl2tpd
   2086 ?        00:00:00 gdm-session-wor
   2150 ?        00:00:00 krfcommd
   2194 tty2     01:29:05 Xorg
   2963 ?        00:00:00 boltd
   3440 ?        00:00:01 python3
  10166 ?        00:00:00 kworker/11:0-events
  13373 ?        00:00:01 kworker/4:2-mm_percpu_wq
  18778 ?        00:00:00 loop21
  18891 ?        00:00:00 kworker/14:0-mm_percpu_wq
  23627 ?        00:00:00 kworker/12:0-events
  25295 ?        00:00:00 kworker/8:2-events
  25812 ?        00:00:00 kworker/0:0-mm_percpu_wq
  26205 ?        00:00:00 kworker/6:0-cgroup_destroy
  27650 ?        00:00:01 kworker/0:2-events
  28599 ?        00:00:00 kworker/11:1-events
  31415 ?        00:00:00 kworker/10:0-events
  32489 ?        00:00:00 kworker/9:1-events
  32571 ?        00:00:00 kworker/13:2-events
  32589 ?        00:00:02 kworker/u32:6-kcryptd/253:0
  32685 ?        00:00:00 kworker/1:4-mm_percpu_wq
  32686 ?        00:00:00 kworker/1:5-events
  32697 ?        00:00:00 kworker/2:11-mm_percpu_wq
  33159 ?        00:00:00 kworker/10:2-events
  33555 ?        00:00:00 kworker/2:0
  34403 ?        00:00:00 kworker/4:0
  34911 ?        00:00:00 kworker/3:1-events
  35079 ?        00:00:00 kworker/9:2-mm_percpu_wq
  35326 ?        00:00:01 kworker/u32:3-kcryptd/253:0
  35411 ?        00:00:00 kworker/15:0-mm_percpu_wq
  35469 ?        00:00:01 kworker/u32:5-kcryptd/253:0
  35797 ?        00:00:00 kworker/7:1-mm_percpu_wq
  35817 ?        00:00:00 kworker/13:1-mm_percpu_wq
  35818 ?        00:00:00 cupsd
  35819 ?        00:00:00 cups-browsed
  35856 ?        00:00:00 kworker/8:0-mm_percpu_wq
  36352 ?        00:00:00 kworker/12:1
  36500 ?        00:00:01 kworker/u32:16-kcryptd/253:0
  37614 ?        00:00:00 kworker/15:1
  37759 ?        00:00:00 kworker/5:0-cgroup_destroy
  37772 ?        00:00:00 kworker/7:0
  37790 ?        00:00:00 kworker/u32:11-kcryptd/253:0
  37873 ?        00:00:00 kworker/u32:18-kcryptd/253:0
  38313 ?        00:00:00 kworker/u32:0-events_power_efficient
  38340 ?        00:00:00 kworker/6:2-mm_percpu_wq
  38424 ?        00:00:00 kworker/14:2
  38425 ?        00:00:00 kworker/3:0
  38426 ?        00:00:00 kworker/u32:1-kcryptd/253:0
  38470 ?        00:00:00 kworker/u32:7-kcryptd/253:0
  38541 ?        00:00:00 kworker/u32:4-kcryptd/253:0
  38621 ?        00:00:00 kworker/u32:10-kcryptd/253:0
  38659 ?        00:00:00 kworker/u32:13-kcryptd/253:0
  38909 ?        00:00:00 kworker/u32:14-kcryptd/253:0
  39393 ?        00:00:00 kworker/u32:8-kcryptd/253:0
  39466 ?        00:00:00 kworker/u32:9-kcryptd/253:0
  40315 ?        00:00:00 kworker/u32:12-kcryptd/253:0

```

---

### Post by sldayo on 2020-09-15
I have discovered that Steam somehow works fine on Linux when I am connected to a VPN on this computer, but it works fine without VPN on Windows.

Switching from NetworkManager to systemd-networkd did not help.

---

### Post by mastablasta on 2020-09-15
then the issue is not steam, but the network configuration. somehow you had it configured that it has to connect via VPN. i am not sure how exactly that works. i do know i can't access some sites unless i use company VPN (in windows 10). and if i use VPN, then i also need to use company proxy to access internet or something like that.

---

### Post by sldayo on 2020-09-15
More testing confirms again that Steam does not work without VPN on Linux on my computer. Interestingly, if I set up ExpressVPN on my router/firewall (Ubiquity EdgeRouter PoE), i.e. for all devices connected through the router, then Steam works fine on Linux without setting up VPN specifically on this computer! Internet seems to be more stable in general now that I am using the VPN.

---

### Post by sldayo on 2020-09-17
Although I don't know the exact cause, the issue has finally disappeared.

Steam works fine now after powering off both the router and modem at the same time which resulted in my ISP assigning me a different IP.

I don't know if the new IP itself, its reputation, different routing or something else did it.

Thanks for the help!

---

### Post by mastablasta on 2020-09-17
> **sldayo said:**
> 
I don't know if the new IP itself, its reputation, different routing or something else did it.


yes, that could be it. Previous IP was abused (not necessary, by the IP holder). that's why it worked via VPN.

many here use dynamic IP, but they actually keep same IP. i made a deal with provider to use static.

---

