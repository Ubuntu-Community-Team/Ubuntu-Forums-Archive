---
title: "Steam Client is not responding on 14.04"
date: 2015-06-02
forum: Gaming &amp; Leisure
---

### Post by siddharthyadunath on 2015-06-02
I installed the steam-launcher from [HTML]http://store.steampowered.com/about/[/HTML] but when I try to run steam-launcher from the launcher it doesn't respond. I tried running ```
steam
``` from the terminal and I get this message. 
```
sidhu@sidhu-Inspiron-5521:~$ steam
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1431729692)
Installing breakpad exception handler for appid(steam)/version(1431729692)
Installing breakpad exception handler for appid(steam)/version(1431729692)
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Installing breakpad exception handler for appid(steam)/version(1431729692)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
[0602/143931:ERROR:browser_main_loop.cc(170)] Running without the SUID sandbox! See https://code.google.com/p/chromium/wiki/LinuxSUIDSandboxDevelopment for more information on developing with the sandbox on.
Installing breakpad exception handler for appid(steamwebhelper)/version(20150514174016)
Installing breakpad exception handler for appid(steamwebhelper)/version(1431625216)
[0602/143931:ERROR:nss_util.cc(981)] Failed to load NSS libraries.
Installing breakpad exception handler for appid(steamwebhelper)/version(20150514174016)
Installing breakpad exception handler for appid(steamwebhelper)/version(1431729692)
Installing breakpad exception handler for appid(steamwebhelper)/version(1431729692)
Installing breakpad exception handler for appid(steam)/version(1431729692)
Installing breakpad exception handler for appid(steam)/version(1431729692)
Installing breakpad exception handler for appid(steam)/version(1431729692)
Installing breakpad exception handler for appid(steam)/version(1431729692)
Installing breakpad exception handler for appid(steam)/version(1431729692)
Installing breakpad exception handler for appid(steam)/version(1431729692)
FillInMachineIDInfo took a total of 0 milliseconds
Installing breakpad exception handler for appid(steam)/version(1431729692)
Installing breakpad exception handler for appid(steam)/version(1431729692)
Installing breakpad exception handler for appid(steam)/version(1431729692)
Generating new string page texture 2: 48x256, total string texture memory is 49.15 KB
Generating new string page texture 3: 384x256, total string texture memory is 442.37 KB
Installing breakpad exception handler for appid(steam)/version(1431729692)
Installing breakpad exception handler for appid(steam)/version(1431729692)
Adding licenses for the following package(s): 0, 13054, 21310, 21350, 21357, 21391, 21438, 38853, 64700, 64701, 69418
roaming config store loaded successfully - 994 bytes.
migrating temporary roaming config store
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
Installing breakpad exception handler for appid(steam)/version(1431729692)
Failed to init SteamVR because it isn't installed
ExecCommandLine: ""/home/sidhu/.local/share/Steam/ubuntu12_32/steam" "
Installing breakpad exception handler for appid(steam)/version(1431729692)
System startup time: 4.32 seconds
[0602/143935:ERROR:renderer_main.cc(212)] Running without renderer sandbox
Generating new string page texture 71: 128x256, total string texture memory is 573.44 KB
Generating new string page texture 72: 64x256, total string texture memory is 638.98 KB
Generating new string page texture 73: 32x256, total string texture memory is 671.74 KB
Generating new string page texture 74: 512x256, total string texture memory is 1.20 MB
Generating new string page texture 75: 256x256, total string texture memory is 1.46 MB
Generating new string page texture 77: 128x256, total string texture memory is 131.07 KB
Generating new string page texture 78: 128x256, total string texture memory is 1.59 MB

(steam:16461): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:16461): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:16461): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:16461): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:16461): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:16461): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:16461): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:16461): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:16461): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:16461): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:16461): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:16461): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:16461): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:16461): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:16461): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/sidhu/.local/share/Steam/ubuntu12_32/steam-runtime

```

How do I resolve this?

---

### Post by MikeCyber on 2015-06-02
looks like it needs gtk. try in synaptic to fix dependencies.

---

### Post by efflandt on 2015-06-02
What graphics card/chip and are you using default graphics drivers or proprietary drivers? If using a proprietary driver for AMD/ATI graphics I have heard that it work best to install steam first, then the video drivers.

Steam on my 14.04 desktop was installed using **Ubuntu Software Center**, with my home directory copied over from 12.04 (but that uses nvidia graphics). Steam on my laptop was installed from scratch using Ubuntu Software Center and games downloaded fresh (but that has hybrid Intel/Nvidia graphics). Both systems were fresh install of 14.04.1 along with any updates at that time. Not sure if anything broke in 14.04.2 or newer versions (mine says it is now 14.04.2, but has kernel and X from 14.04.1).

If you install **synaptic** from Software Center that has filters for **Broken** packages or **Upgradable (upstream)**.

---

