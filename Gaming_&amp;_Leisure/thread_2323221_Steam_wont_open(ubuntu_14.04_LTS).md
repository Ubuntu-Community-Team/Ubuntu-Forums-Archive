---
title: "Steam wont open(ubuntu 14.04 LTS)"
date: 2016-05-03
forum: Gaming &amp; Leisure
---

### Post by lgt2 on 2016-05-03
I downloaded steam from both the website and the ubuntu store and it dowloaded it, but when i try to open it. It shows the loading icon, but never open i left my computer on for a hour with no screen saver and it never opened

---

### Post by MikeCyber on 2016-05-04
run it in a terminal and paste the output here.
Something alike:
cd ~
./steam

only use sudo when you have to.
also remove .steam in your home before reinstalling etc.

---

### Post by gbemio on 2016-07-16
ladipo@oladipo-HP-ENVY-m4-Notebook-PC:~$ steam
Running Steam on ubuntu 14.04 32-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1468023329)
Installing breakpad exception handler for appid(steam)/version(1468023329)
Installing breakpad exception handler for appid(steam)/version(1468023329)
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
Installing breakpad exception handler for appid(steam)/version(1468023329)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
[0716/165641:ERROR:main_delegate.cc(779)] Could not load cef_extensions.pak
[0716/165641:ERROR:browser_main_loop.cc(217)] Running without the SUID sandbox! See [https://chromium.googlesource.com/chromium/src/+/master/docs/linux_suid_sandbox_development.md](https://chromium.googlesource.com/chromium/src/+/master/docs/linux_suid_sandbox_development.md) for more information on developing with the sandbox on.
Installing breakpad exception handler for appid(steamwebhelper)/version(20160708214346)
Installing breakpad exception handler for appid(steamwebhelper)/version(1468014226)
Installing breakpad exception handler for appid(steamwebhelper)/version(20160708214346)
Installing breakpad exception handler for appid(steamwebhelper)/version(1468023329)
Installing breakpad exception handler for appid(steamwebhelper)/version(1468023329)
[0716/165641:ERROR:main_delegate.cc(779)] Could not load cef_extensions.pak
Installing breakpad exception handler for appid(steam)/version(1468023329)
Installing breakpad exception handler for appid(steam)/version(1468023329)
Installing breakpad exception handler for appid(steam)/version(1468023329)
Installing breakpad exception handler for appid(steam)/version(1468023329)
Installing breakpad exception handler for appid(steam)/version(1468023329)
Installing breakpad exception handler for appid(steam)/version(1468023329)
Created shared memory when not owner SteamController_Shared_mem
Installing breakpad exception handler for appid(steam)/version(1468023329)
Installing breakpad exception handler for appid(steam)/version(1468023329)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
crash_20160716165634_1.dmp[9975]: Uploading dump (out-of-process)
/tmp/dumps/crash_20160716165634_1.dmp
/home/oladipo/.local/share/Steam/steam.sh: line 713:  9916 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$STEAMEXEPATH" "$@"
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
Refresh rate: 1
crash_20160716165634_1.dmp[9975]: Finished uploading minidump (out-of-process): success = yes
crash_20160716165634_1.dmp[9975]: response: CrashID=bp-c36d56b5-8cae-47f2-bf4c-625722160716
crash_20160716165634_1.dmp[9975]: file ''/tmp/dumps/crash_20160716165634_1.dmp'', upload yes: ''CrashID=bp-c36d56b5-8cae-47f2-bf4c-625722160716''

---

