---
title: "Problem with Steam runtime after Ubuntu upgrade"
date: 2023-03-08
forum: Gaming &amp; Leisure
---

### Post by petrosmith on 2023-03-08
Ubuntu 22.04.2 LTS
Radeon RX 570 Series (POLARIS10, DRM 3.47.0, 5.19.0-35-generic

Steam package from repository, not steam intaller (both ways installed Steam do not launch with similar errors). Steam work well till one of Ubuntu upgrade.
I'v already installed i386 architecture and drivers for MESA, but have not ideas with next movies. 

```
Loaded SDL version 3.0.0-765-gc4db0725e
Gtk-Message: 09:56:43.698: Failed to load module "gail"
Gtk-Message: 09:56:43.699: Failed to load module "atk-bridge"

(steam:21948): Gtk-WARNING **: 09:56:43.705: Unable to locate theme engine in module_path: "adwaita",
/usr/share/themes/Yaru/gtk-2.0/main.rc:775: error: unexpected identifier 'direction', expected character '}'

(steam:21948): Gtk-WARNING **: 09:56:43.723: Unable to locate theme engine in module_path: "adwaita",
/usr/share/themes/Yaru/gtk-2.0/hacks.rc:28: error: invalid string constant "normal_entry", expected valid string constant
XRRGetOutputInfo Workaround: initialized with override: 0 real: 0xf6a889c0
XRRGetCrtcInfo Workaround: initialized with override: 0 real: 0xf6a871f0
libGL error: MESA-LOADER: failed to open radeonsi (search paths /opt/amdgpu/lib/i386-linux-gnu/dri)
libGL error: failed to load driver: radeonsi
libGL error: MESA-LOADER: failed to open swrast (search paths /opt/amdgpu/lib/i386-linux-gnu/dri)
libGL error: failed to load driver: swrast
Steam: An X Error occurred
X Error of failed request:  GLXBadContext
Major opcode of failed request:  149
Serial number of failed request:  39
xerror_handler: X failed, continuing
crash_20230308095643_4.dmp[21957]: Uploading dump (out-of-process)
/tmp/dumps/crash_20230308095643_4.dmp
/home/petro/.steam/debian-installation/steam.sh: &#1089;&#1090;&#1088;&#1086;&#1082;&#1072; 798: 21948 &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; &#1089;&#1077;&#1075;&#1084;&#1077;&#1085;&#1090;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1080;&#1103;                   (&#1086;&#1073;&#1088;&#1072;&#1079; &#1087;&#1072;&#1084;&#1103;&#1090;&#1080; &#1089;&#1073;&#1088;&#1086;&#1096;&#1077;&#1085; &#1085;&#1072; &#1076;&#1080;&#1089;&#1082;) "$STEAMROOT/$STEAMEXEPATH" "$@"
petro@timdesctop:~$ crash_20230308095643_4.dmp[21957]: Finished uploading minidump (out-of-process): success = yes
crash_20230308095643_4.dmp[21957]: response: CrashID=bp-7345cddc-dfbe-45b9-8599-9bb9b2230307
crash_20230308095643_4.dmp[21957]: file ''/tmp/dumps/crash_20230308095643_4.dmp'', upload yes: ''CrashID=bp-7345cddc-dfbe-45b9-8599-9bb9b2230307''
```

---

