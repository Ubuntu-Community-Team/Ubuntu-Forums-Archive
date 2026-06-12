---
title: "Is steam supporting ubuntu 14.04?"
date: 2016-09-30
forum: Gaming &amp; Leisure
---

### Post by YTS_Chan on 2016-09-30
May I ask is steam supported officially on Ubuntu14.04? From the [requirement page on github]("https://github.com/ValveSoftware/steam-for-linux"), it seems that it must be on Ubuntu 12.04? Should I downgrade in order to install Steam?

I installed steam through Ubuntu Software Center, but it crash on start.

If it is supported, any hints on what is the possible reason? The following is the return message when I am starting my steam in command prompt.

```
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1474415843)
Installing breakpad exception handler for appid(steam)/version(1474415843)
Installing breakpad exception handler for appid(steam)/version(1474415843)
Installing breakpad exception handler for appid(steam)/version(1474415843)
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Installing breakpad exception handler for appid(steam)/version(1474415843)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
[0930/232400:ERROR:main_delegate.cc(779)] Could not load cef_extensions.pak
[0930/232400:ERROR:browser_main_loop.cc(217)] Running without the SUID sandbox! See https://chromium.googlesource.com/chromium/src/+/master/docs/linux_suid_sandbox_development.md for more information on developing with the sandbox on.
Installing breakpad exception handler for appid(steamwebhelper)/version(20160920182018)
Installing breakpad exception handler for appid(steamwebhelper)/version(1474395618)
[0930/232400:ERROR:main_delegate.cc(779)] Could not load cef_extensions.pak
Installing breakpad exception handler for appid(steam)/version(1474415843)
Installing breakpad exception handler for appid(steam)/version(1474415843)
Installing breakpad exception handler for appid(steam)/version(1474415843)
Installing breakpad exception handler for appid(steam)/version(1474415843)
Installing breakpad exception handler for appid(steam)/version(1474415843)
Installing breakpad exception handler for appid(steamwebhelper)/version(20160920182018)
Installing breakpad exception handler for appid(steamwebhelper)/version(1474415843)
Installing breakpad exception handler for appid(steamwebhelper)/version(1474415843)
Installing breakpad exception handler for appid(steam)/version(1474415843)
Created shared memory when not owner SteamController_Shared_mem
Installing breakpad exception handler for appid(steam)/version(1474415843)
Installing breakpad exception handler for appid(steam)/version(1474415843)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
crash_20160930232249_1.dmp[30946]: Uploading dump (out-of-process)
/tmp/dumps/crash_20160930232249_1.dmp
/home/cytsunny/.local/share/Steam/steam.sh: line 713: 30829 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$STEAMEXEPATH" "$@"
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
crash_20160930232249_1.dmp[30946]: Finished uploading minidump (out-of-process): success = yes
crash_20160930232249_1.dmp[30946]: response: CrashID=bp-078b191a-9665-47bb-a9c3-569cc2160930
crash_20160930232249_1.dmp[30946]: file ''/tmp/dumps/crash_20160930232249_1.dmp'', upload yes: ''CrashID=bp-078b191a-9665-47bb-a9c3-569cc2160930''
cytsunny@sunny-desktop:~$ steam --reset
/home/cytsunny/.local/share/Steam/steam.sh: line 444: no match: ssfn*
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1474415843)
Installing breakpad exception handler for appid(steam)/version(1474415843)
Installing breakpad exception handler for appid(steam)/version(1474415843)
Installing breakpad exception handler for appid(steam)/version(1474415843)
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Installing breakpad exception handler for appid(steam)/version(1474415843)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
[0930/232714:ERROR:main_delegate.cc(779)] Could not load cef_extensions.pak
[0930/232714:ERROR:browser_main_loop.cc(217)] Running without the SUID sandbox! See https://chromium.googlesource.com/chromium/src/+/master/docs/linux_suid_sandbox_development.md for more information on developing with the sandbox on.
Installing breakpad exception handler for appid(steamwebhelper)/version(20160920182018)
Installing breakpad exception handler for appid(steamwebhelper)/version(1474395618)
Installing breakpad exception handler for appid(steamwebhelper)/version(20160920182018)
Installing breakpad exception handler for appid(steamwebhelper)/version(1474415843)
[0930/232714:ERROR:main_delegate.cc(779)] Could not load cef_extensions.pak
Installing breakpad exception handler for appid(steamwebhelper)/version(1474415843)
Installing breakpad exception handler for appid(steam)/version(1474415843)
Installing breakpad exception handler for appid(steam)/version(1474415843)
Installing breakpad exception handler for appid(steam)/version(1474415843)
Installing breakpad exception handler for appid(steam)/version(1474415843)
Installing breakpad exception handler for appid(steam)/version(1474415843)
Installing breakpad exception handler for appid(steam)/version(1474415843)
Created shared memory when not owner SteamController_Shared_mem
Installing breakpad exception handler for appid(steam)/version(1474415843)
Installing breakpad exception handler for appid(steam)/version(1474415843)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
crash_20160930232612_1.dmp[31279]: Uploading dump (out-of-process)
/tmp/dumps/crash_20160930232612_1.dmp
/home/cytsunny/.local/share/Steam/steam.sh: line 711: 31221 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$STEAMEXEPATH" "$@"
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
Refresh rate: 1
crash_20160930232612_1.dmp[31279]: Finished uploading minidump (out-of-process): success = yes
crash_20160930232612_1.dmp[31279]: response: CrashID=bp-d5ee5f7a-0e79-46ed-94aa-11f072160930
crash_20160930232612_1.dmp[31279]: file ''/tmp/dumps/crash_20160930232612_1.dmp'', upload yes: ''CrashID=bp-d5ee5f7a-0e79-46ed-94aa-11f072160930''



```

I know many have asked similar question, but I have tried many ways I found on Google. For example, I have switched my display card to NVidia, I have tried [the command from the steam community]("http://steamcommunity.com/app/221410/discussions/0/350542683198244989/"), I have tried installing my graphic card after my steam, but none of this works. I am really frustrated on installing steam. Hope this question is not deleted because of duplication.

---

### Post by efflandt on 2016-10-01
I originally ran steam in 64-bit 12.04 since Jan 2013 and in 64-bit 14.04 since Jan 2014 with nvidia graphics and have no issues. And I was chatting with a friend on steam yesterday who is running 16.04. I am running a GTX 750 Ti with nvidia-367 driver package (367.44) from graphics-drivers/ppa.

Did you install steam using Ubuntu Software Center?
What graphics card do you have and which nvidia driver package are you using?

Since that log does not say why yours crashed, you might open the dump (.dmp) files in /tmp/dumps/ to see if that gives any clue. The only dumps I get are related to virtual reality which I am not using, but those dumps do not cause any problem. For example "Assert( Assertion Failed: BFileExists( /home/efflandt/.local/share/Steam/SteamApps/common/OpenVR/bin/linux64/vrpathreg ) failed ):vr/vrmanager.cpp:19"

Other than the crash dumps, I do not see any errors in your output that are not normal errors. So I cannot guess what your issue is because it usually continues onward from where yours dumps:```
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
ExecCommandLine: ""/home/efflandt/.local/share/Steam/ubuntu12_32/steam" "
Installing breakpad exception handler for appid(steam)/version(1474415843)
System startup time: 39.06 seconds
Generating new string page texture 90: 128x256, total string texture memory is 131.07 KB
```

---

### Post by YTS_Chan on 2016-10-03
I have checked the dumps, but they are binary files...... basically not readable for human.

I am using NVidia GeForce GT 610 as my display card, with NVidia-352 driver package (352.63), which should be latest proprietary version.

In case if I really am not able to install Steam, any alternative to Steam to play native game for Ubuntu?

---

### Post by efflandt on 2016-10-03
I forgot to mention that using Ubuntu Software Center you can install "ghex" to look at the dump files. Since most of it is binary you will not understand most of it, but usually at the end of the .dmp file is an error message that triggered the crash.

If you open the Ubuntu Software Center there are a bunch of games. One amusing one to get you started would be "SuperTuxKart" where you are an animal driving a gokart. Alien Arena is similar to Quake III. Warzone 2100 is similar to Command and Conquer. Or you can look through the other 940 games, most of which are free.

---

### Post by mastablasta on 2016-10-06
steam should work.

if you are looking for some free games check the playdeb ppa. Quite a few games would also work in wine. you can use Playonlinux frontend to help you install them. with GT610 i guess you are not hunting for the latest AAA titles :p

---

