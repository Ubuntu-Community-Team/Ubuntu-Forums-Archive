---
title: "Steam on Ubuntu 14.04"
date: 2014-04-20
forum: Gaming &amp; Leisure
---

### Post by molder-melvin on 2014-04-20
I've recently installed Ubuntu 14.04 and I have been trying to get steam to work.
I went to the Software Center, used the terminal and used the steam website to download it.
Whenever I launch steam nothing happens, but when I launch it from the terminal I get this. Any Help?

Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140420071409_1.dmp
/home/melvin/.local/share/Steam/steam.sh: line 755: 10653 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
mv: cannot stat ‘/home/melvin/.steam/registry.vdf’: No such file or directory
Installing bootstrap /home/melvin/.local/share/Steam/bootstrap.tar.xz
Reset complete!
Restarting Steam by request...
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/melvin/.local/share/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(0_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140420071412_1.dmp
/home/melvin/.local/share/Steam/steam.sh: line 755: 10779 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-6340c17e-d2ee-483d-9679-4d6c82140420
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-e0f1e5d4-37ba-40d1-9801-0bd502140420

---

### Post by MikeCyber on 2014-04-20
Works fine here but I've used the installer from the Steam website. Try to uninstall and use that.

---

### Post by molder-melvin on 2014-04-21
I tried what you said, but I'm pretty new to Ubuntu. I uninstalled using sudo apt-get remove steam. Then went to the steam website and used sudo dpkg -i steam_latest.deb to install it. Got the same error message.

---

### Post by molder-melvin on 2014-04-21
I solved my problem. If others have the same issue go to this forum post it helped me. [http://ubuntuforums.org/showthread.php?t=2209830](http://ubuntuforums.org/showthread.php?t=2209830)

---

### Post by thenox on 2014-09-10
Just wanted to say thanks for posting the link to the forum w/ your solution. I've had similar issues getting Steam to work on Ubuntu. Thanks!

---

