---
title: "No sound in steam"
date: 2015-07-06
forum: Gaming &amp; Leisure
---

### Post by brennan3 on 2015-07-06
(SOLVED)I&#8217;m new to Ubuntu and trying my best to learn it and to benefit my switch from windows so sorry if I don&#8217;t understand what you saying :)- My steam has no sound what so ever in trailers no sound and i have downloaded Ark survival evolved and rust to test that there is no sound and there is no sound in any of my games new or old i got steam from the steam site install button thanks for the help :)-Brennan

---

### Post by brennan3 on 2015-07-06
Also im running 14.04 LTS Processor-Intel® Core™ i3-2100 CPU @ 3.10GHz × 4  Card- GeForce GTX 660 and i have a 64 bit system.

---

### Post by MikeCyber on 2015-07-06
in steam videos usually you have to turn up volume. Anyway run it in a terminal and paste the output:
simply type, as it's in standard search path:
steam

---

### Post by brennan3 on 2015-07-06
is this what you wanted?-carousue@BrennansPC:~$ steam
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
carousue@BrennansPC:~$ steam
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1433441724)
Installing breakpad exception handler for appid(steam)/version(1433441724)
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Installing breakpad exception handler for appid(steam)/version(1433441724)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
[0706/084306:ERROR:browser_main_loop.cc(170)] Running without the SUID sandbox! See [https://code.google.com/p/chromium/wiki/LinuxSUIDSandboxDevelopment](https://code.google.com/p/chromium/wiki/LinuxSUIDSandboxDevelopment) for more information on developing with the sandbox on.
Installing breakpad exception handler for appid(steamwebhelper)/version(20150604103540)
Installing breakpad exception handler for appid(steamwebhelper)/version(1433414140)
[0706/084306:ERROR:nss_util.cc(981)] Failed to load NSS libraries.
Installing breakpad exception handler for appid(steamwebhelper)/version(20150604103540)
Installing breakpad exception handler for appid(steamwebhelper)/version(1433441724)
Installing breakpad exception handler for appid(steamwebhelper)/version(1433441724)
Installing breakpad exception handler for appid(steam)/version(1433441724)
Installing breakpad exception handler for appid(steam)/version(1433441724)
Installing breakpad exception handler for appid(steam)/version(1433441724)
Installing breakpad exception handler for appid(steam)/version(1433441724)
Installing breakpad exception handler for appid(steam)/version(1433441724)
FillInMachineIDInfo took a total of 0 milliseconds
Installing breakpad exception handler for appid(steam)/version(1433441724)
Installing breakpad exception handler for appid(steam)/version(1433441724)
Installing breakpad exception handler for appid(steam)/version(1433441724)
Installing breakpad exception handler for appid(steam)/version(1433441724)
Generating new string page texture 2: 48x256, total string texture memory is 49.15 KB
Generating new string page texture 3: 256x256, total string texture memory is 311.30 KB
Installing breakpad exception handler for appid(steam)/version(1433441724)
Installing breakpad exception handler for appid(steam)/version(1433441724)
Installing breakpad exception handler for appid(steam)/version(1433441724)
Installing breakpad exception handler for appid(steam)/version(1433441724)
Adding licenses for the following package(s): 0, 36, 219, 1256, 1295, 2114, 4097, 7609, 8183, 8538, 11734, 12248, 13123, 13152, 13435, 14842, 15579, 16064, 16724, 16966, 17250, 17976, 17983, 18358, 18659, 21311, 21312, 21314, 21321, 21323, 21350, 21351, 21433, 21486, 26510, 27214, 28795, 29006, 30879, 31292, 34045, 34599, 35220, 36077, 44226, 45123, 47144, 47466, 47787, 48754, 50921, 52819, 56355, 58123, 59321, 66701, 68387
roaming config store loaded successfully - 3757 bytes.
migrating temporary roaming config store
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
Failed to init SteamVR because it isn't installed
ExecCommandLine: ""/home/carousue/.local/share/Steam/ubuntu12_32/steam" "
Installing breakpad exception handler for appid(steam)/version(1433441724)
System startup time: 4.13 seconds
Generating new string page texture 70: 128x256, total string texture memory is 442.37 KB
Generating new string page texture 71: 128x256, total string texture memory is 131.07 KB
Generating new string page texture 72: 64x256, total string texture memory is 507.90 KB
Generating new string page texture 73: 8x256, total string texture memory is 516.10 KB
Generating new string page texture 74: 32x256, total string texture memory is 548.86 KB
Installing breakpad exception handler for appid(steam)/version(1433441724)
[0706/084311:ERROR:renderer_main.cc(212)] Running without renderer sandbox
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/carousue/.local/share/Steam/ubuntu12_32/steam-runtime
ExecCommandLine: "/home/carousue/.steam/root/ubuntu12_32/steam steam://open/driverhelperready"
ExecSteamURL: "steam://open/driverhelperready"
^C

---

### Post by MikeCyber on 2015-07-06
Yes but look yourself if you find in there something about sound
A quick google search and some other user said:
I installed pavucontrol  and checked the pulseaudio settings.
You have in other apps/system sound?

---

### Post by brennan3 on 2015-07-06
OK thanks tons i had looked before in the audio settings but it seems my card auto set it to another sound port then my headphones so i was receiving no audio because im using wireless headphones.. it was such a small thing to miss thanks man

---

