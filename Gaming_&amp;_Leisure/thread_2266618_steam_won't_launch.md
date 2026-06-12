---
title: "steam won't launch"
date: 2015-02-24
forum: Gaming &amp; Leisure
---

### Post by wilsonpyc on 2015-02-24
Steam doesn't start properly on 14.04
Only a pop up that says Verfying installation then goes away.

This is what I got from running steam on terminal


Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1424305157)
Installing breakpad exception handler for appid(steam)/version(1424305157)
Installing breakpad exception handler for appid(steam)/version(1424305157)
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Installing breakpad exception handler for appid(steam)/version(1424305157)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Installing breakpad exception handler for appid(steamwebhelper)/version(20150218153139)
Installing breakpad exception handler for appid(steamwebhelper)/version(1424273499)
[0224/181217:ERROR:nss_util.cc(1018)] Failed to load NSS libraries.
Installing breakpad exception handler for appid(steamwebhelper)/version(20150218153139)
Installing breakpad exception handler for appid(steamwebhelper)/version(1424305157)
Installing breakpad exception handler for appid(steamwebhelper)/version(1424305157)
Installing breakpad exception handler for appid(steam)/version(1424305157)
Installing breakpad exception handler for appid(steam)/version(1424305157)
Installing breakpad exception handler for appid(steam)/version(1424305157)
Installing breakpad exception handler for appid(steam)/version(1424305157)
Installing breakpad exception handler for appid(steam)/version(1424305157)
Installing breakpad exception handler for appid(steam)/version(1424305157)
FillInMachineIDInfo took a total of 0 milliseconds
Installing breakpad exception handler for appid(steam)/version(1424305157)
Installing breakpad exception handler for appid(steam)/version(1424305157)
[0224/181217:ERROR:renderer_main.cc(227)] Running without renderer sandbox
[0224/181217:ERROR:renderer_main.cc(227)] Running without renderer sandbox
/home/username/.local/share/Steam/steam.sh: line 757: 13289 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$STEAMEXEPATH" "$@"
Assert( Assertion Failed: iRet > 0 ):/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/webhelper/../common/html/chrome_ipc_server.cpp:408


Installing breakpad exception handler for appid(steamwebhelper)/version(1424305157)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
crash_20150224181218_5.dmp[13353]: Uploading dump (out-of-process)
/tmp/dumps/crash_20150224181218_5.dmp
/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/webhelper/../common/html/chrome_ipc_server.cpp (408) : Assertion Failed: iRet > 0
/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/webhelper/../common/html/chrome_ipc_server.cpp (408) : Assertion Failed: iRet > 0
/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/webhelper/../common/html/chrome_ipc_server.cpp (408) : Assertion Failed: iRet > 0
/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/webhelper/../common/html/chrome_ipc_server.cpp (408) : Assertion Failed: iRet > 0
/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/webhelper/../common/html/chrome_ipc_server.cpp (408) : Assertion Failed: iRet > 0
crash_20150224181218_5.dmp[13353]: Finished uploading minidump (out-of-process): success = yes
crash_20150224181218_5.dmp[13353]: response: CrashID=bp-9d0fcf79-909e-40ed-b9f0-438a72150224
crash_20150224181218_5.dmp[13353]: file ''/tmp/dumps/crash_20150224181218_5.dmp'', upload yes: ''CrashID=bp-9d0fcf79-909e-40ed-b9f0-438a72150224''

---

### Post by Hastur_The_Unspeak on 2015-02-24
Are you on a 32 or 64 bit OS version?

---

### Post by wilsonpyc on 2015-02-24
It's 64 bit

---

### Post by oldrocker99 on 2015-02-24
If you downloaded Steam from the Software Center, try downloading directly from [steampowered.com](steampowered.com). Go to the directory to which you downloaded it, and enter
```
sudo apt-get remove steam
sudo dpkg -i steam_latest.deb
```

I have had far better results with this method of installation. Good luck.

---

### Post by Hastur_The_Unspeak on 2015-02-25
Make sure to enable multilib repositories then. If you're just vanilla downloading it you might run into some issues. I had the same problem with my first steam install when I first got my rig, then I enabled multilib and it was fine.

---

### Post by efflandt on 2015-02-26
You have very strange paths if you are running "steam" in regular 14.04. Is **buildbot** a different username than you? And where did that **buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/** path come from, did you try to build your own steam from source? What video drivers are you running?

I am simply running steam installed from Software Center in 64-bit 14.04 (in January), although, I then copied over my old home directory from 64-bit 12.04 before running steam. I did not need to add any 32-bit libs. Although, I do put the newest libflashplayer.so (from install_flash_player_11_linux.i386.tar.gz) into ~/.local/share/Steam/ubuntu12_32/plugins/ just in case that is still required to play flash videos in 32-bit steam.

Note that nvidia graphics usually works best for steam. For AMD/ATI video I hear that you have to install steam before installing proprietary video drivers. But I could not even get into X until I had nvidia drivers installed new enough for my GTX 750 Ti.

---

### Post by wilsonpyc on 2015-03-01
hmm thanks for all the replies, but so far it is still not working.
I even reinstalled ubuntu...multilb, and graphic card driver, just not working...
My graphics card is GeForce GTX 860M/PCIe/SSE2.

---

