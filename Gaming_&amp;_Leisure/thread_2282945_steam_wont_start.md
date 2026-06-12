---
title: "steam wont start"
date: 2015-06-18
forum: Gaming &amp; Leisure
---

### Post by dragonknight2010 on 2015-06-18
[COLOR=#000000]sooo steam wouldnt work for me so i went online found a forum saying to install 32b libs now when i click on steam it wont even start up no error from before nothing...any help guys?[/COLOR]


[COLOR=#000000]swazi71@swazi71Comp:~$ steam[/COLOR]
[COLOR=#000000]Running Steam on ubuntu 14.04 64-bit[/COLOR]
[COLOR=#000000]STEAM_RUNTIME is enabled automatically[/COLOR]
[COLOR=#000000]Installing breakpad exception handler for appid(steam)/version(1433441724)[/COLOR]
[COLOR=#000000]Installing breakpad exception handler for appid(steam)/version(1433441724)[/COLOR]
[COLOR=#000000]Gtk-Message: Failed to load module "overlay-scrollbar"[/COLOR]
[COLOR=#000000]Gtk-Message: Failed to load module "unity-gtk-module"[/COLOR]
[COLOR=#000000]Installing breakpad exception handler for appid(steam)/version(1433441724)[/COLOR]
[COLOR=#000000]Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element[/COLOR]
[COLOR=#000000]Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element[/COLOR]
[COLOR=#000000]Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number[/COLOR]
[COLOR=#000000]/home/swazi71/.local/share/Steam/ubuntu12_32/steamwebhelper: error while loading shared libraries: libcap.so.2: cannot open shared object file: No such file or directory[/COLOR]
[COLOR=#000000]/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/steamUI/../common/steam/client_api.cpp (320) : Assertion Failed: ClientAPI_InitGlobalInstance: InternalAPI_Init_Internal failed, most likely because you are missing a 32-bit dependency of steamclient.so (the Steam client is a 32-bit app).[/COLOR]


[COLOR=#000000]Assert( Assertion Failed: ClientAPI_InitGlobalInstance: InternalAPI_Init_Internal failed, most likely because you are missing a 32-bit dependency of steamclient.so (the Steam client is a 32-bit app).[/COLOR]
[COLOR=#000000]):/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/steamUI/../common/steam/client_api.cpp:320[/COLOR]


[COLOR=#000000]Installing breakpad exception handler for appid(steam)/version(1433441724)[/COLOR]
[COLOR=#000000]assert_20150618002242_5.dmp[6353]: Uploading dump (out-of-process)[/COLOR]
[COLOR=#000000]/tmp/dumps/assert_20150618002242_5.dmp[/COLOR]
[COLOR=#000000]/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/steamUI/SteamStartup.cpp (751) : Assertion Failed: ! "There was a problem with your Steam installation.\n" "Please reinstall steam.\n"[/COLOR]
[COLOR=#000000]assert_20150618002242_5.dmp[6353]: Finished uploading minidump (out-of-process): success = no[/COLOR]
[COLOR=#000000]assert_20150618002242_5.dmp[6353]: error: HTTP response code said error[/COLOR]
[COLOR=#000000]assert_20150618002242_5.dmp[6353]: file ''/tmp/dumps/assert_20150618002242_5.dmp'', upload no: ''HTTP response code said error''[/COLOR]
[COLOR=#000000][2015-06-18 00:22:41] Startup - updater built Jun 4 2015 10:35:42[/COLOR]
[COLOR=#000000][2015-06-18 00:22:41] Verifying installation...[/COLOR]
[COLOR=#000000][2015-06-18 00:22:41] Verification complete[/COLOR]
[COLOR=#000000][2015-06-18 00:22:43] Shutdown[/COLOR]

---

### Post by lenzojake on 2015-06-18
So.....your trying to run a 32bit program on a 64bit machine and it's being annoying....
Did you install it directly form the software centre or download it in a .deb file? If all fails you could run the windows version under wine lol :popcorn:

---

### Post by dragonknight2010 on 2015-06-18
i installed it directly i never had a problem with steam till now but then i havent used it in a few months.....

---

### Post by lenzojake on 2015-06-18
What has changed on your computer from the time of installation? Updates, installation of new software, evil monkeys trying to eat your computer?

---

### Post by efflandt on 2015-06-19
What graphics card/chip do you have and are you using a default driver or added driver? Nvidia with nvidia drivers seems to work best for steam. I have been running steam with nvidia graphics since Jan 2013 without any problems in 64-bit 12.04 at that time or 14.04 since January 2015. On my desktop the game files were in my home directory that I copied over to 14.04, but steam installed from scratch on my hybrid Intel/Nvidia graphics laptop also works fine.

64-bit 14.04 should already include 32-bit libs. You did not say what the recommendation you saw said to do. If you have AMD/ATI graphics I hear that you need to install steam before installing fglrx, or I think you end up missing some 32-bit lib(s) related to graphics. The only time I had to add any missing libs was when running 13.10 on my laptop, but the hybrid graphics was not fully developed yet then.

---

### Post by Bucky Ball on 2015-06-19
*Thread moved to **Gaming & Leisure**.*

Please use code tags for terminal output. See the last link in my signature. Thanks.

---

