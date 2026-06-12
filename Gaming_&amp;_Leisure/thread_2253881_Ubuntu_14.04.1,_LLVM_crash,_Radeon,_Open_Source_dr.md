---
title: "Ubuntu 14.04.1, LLVM crash, Radeon, Open Source drivers"
date: 2014-11-23
forum: Gaming &amp; Leisure
---

### Post by aquablue25 on 2014-11-23
Sup guys,

most of my 3D games crash at some point or when using high graphical details. This includes but is not limited to: Nexuiz, Xonotic, World of Warcraft (only in D3D9 mode), Resident Evil Revelations and a few other games played natively and via Wine.

I am using a AMD 7850 GDDR5 GPU + the default/recommended Open Source drivers by Ubuntu.

This problem only occures in Ubuntu 14.04.1 64-bit, using the Open Source drivers and the version of Mesa that ships with this version of the OS. The games mentioned above work just fine via the proprietary Catalyst drivers provided by Ubuntu 14.04.1 64-bit.

I also tried Ubuntu 14.10, which ships with new Open Source drivers. The issue seems to be resolved there, which leads me to believe that it's a bug specifically related to 14.04.1 64-bit.

**I am not alone:** [http://www.phoronix.com/forums/printthread.php?t=50038&pp=10&page=118](http://www.phoronix.com/forums/printthread.php?t=50038&pp=10&page=118)

Any ideas how to fix the issue?

Crash-log from WoW (scroll all the way down to find the error):

** Fri Nov 14 12:12:39 2014
Starting '/opt/cxoffice/bin/wineloader' 'winewrapper.exe' '--new-console' '--workdir' '/home/nicole/.cxoffice/World_of_Warcraft/dosdevices/c:/Program Files/World of Warcraft' '--start' '--'
'/home/nicole/.cxoffice/World_of_Warcraft/dosdevices/../drive_c/Program Files/World of Warcraft/Wow.exe'

fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x1590000 0 0x33fdc8 4
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/p11-kit-trust.so: /usr/lib/i386-linux-gnu/pkcs11/p11-kit-trust.so: Kann die Shared-Object-Datei nicht öffnen: Datei oder Verzeichnis nicht gefunden
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: Kann die Shared-Object-Datei nicht öffnen: Datei oder Verzeichnis nicht gefunden
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:WinHttpDetectAutoProxyConfigUrl discovery via DHCP not supported
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:mpr:WNetGetUniversalNameW (L"C:\\Program Files\\World of Warcraft\\data\\data", 0x00000001, 0x179e974, 0x179e970): stub
fixme:d3d11:D3D11CreateDevice stub: adapter (nil), driver_type D3D_DRIVER_TYPE_HARDWARE, swrast (nil), flags 0x1, feature_levels 0x179fac0, levels 0x3, sdk_version 7, device (nil), feature_level 0x179facc, context (nil)
fixme:win:EnumDisplayDevicesW ((null),0,0x179ecf8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x179ec08,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x179f1f8,0x00000000), stub!
fixme:dxgi:dxgi_adapter_CheckInterfaceSupport iface 0x1475d0, guid {9b7e4c0f-342c-4106-a19f-4f2704f689f0}, umd_version (nil) stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x179f0e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x179efe8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x179eee8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x179f5b8,0x00000000), stub!
fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:win:EnumDisplayDevicesW ((null),0,0x179e6f8,0x00000000), stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x179fa30,0,(nil),0x68322f8,0x179fa28,0x179fa8c) stub!
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x179fa30,0,(nil),0x68322f8,0x179fa28,0x179fa8c) stub!
ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so

ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM default
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Audio",0x6e0e998): stub
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:win:EnumDisplayDevicesW ((null),0,0x179ed38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x179ec48,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x179ed28,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x179ec28,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x179ed28,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x179ec28,0x00000000), stub!
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:win:EnumDisplayDevicesW ((null),0,0x179ef78,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x179ee78,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x179ef68,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x179ee68,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x179ef68,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x179ee68,0x00000000), stub!
fixme:imm:ImmReleaseContext (0x6004c, 0x68329c8): stub
fixme:advapi:CreateRestrictedToken (0x23dc, 0x0, 2, 0x20cbbb08, 19, 0x1238923c, 5, 0x179a4d0, 0x179a5d0): stub
fixme:advapi:BuildSecurityDescriptorW ((nil),(nil),1,0x179a0fc,0,(nil),0x12062140,0x179a124,0x179a130) stub!
**LLVM ERROR: ran out of registers during register allocation**

---

### Post by aquablue25 on 2014-11-24
Sup guys,

another question: Is there any official way to update the Open Source drivers that Ubuntu ships with? Are there any official repos for this purpose? What is the recommended way of doing it?

If the issue is LLVM + the Open Source drivers and/or Mesa, using a new graphics stack would improve the situation (that's probably also the reason why Ubuntu 14.10 doesn't have this issue).

I ask because I know that the Xorg-Edgers and Oibaf PPA both offer a simple way to update the default drivers, but I am not sure if they're trustworthy and I also don't know how stable they are. Needless to say that I don't know what kind of impact the changes would have on our stable LTS system.

Cheers,
Aqua

---

### Post by oldrocker99 on 2014-11-24
This might help:
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)

Good luck!

---

