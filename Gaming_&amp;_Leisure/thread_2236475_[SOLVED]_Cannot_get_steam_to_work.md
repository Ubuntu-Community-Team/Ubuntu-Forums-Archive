---
title: "[SOLVED] Cannot get steam to work"
date: 2014-07-27
forum: Gaming &amp; Leisure
---

### Post by zrbecker on 2014-07-27
I installed steam through the Ubuntu Software Center, but I am getting weird errors when it starts up. Can anyone help me diagnose the issue? Below is the messages I get when I run steam.

EDIT: Solved, apparently steam has some issue with the fglrx driver. I switched to the open source driver, let steam do an update thing, switched back to the fglrx driver and everything worked fine.

```
$ steam
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140726224750_1.dmp
/home/zrbecker/.local/share/Steam/steam.sh: line 755: 19551 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
mv: cannot stat ‘/home/zrbecker/.steam/registry.vdf’: No such file or directory
Installing bootstrap /home/zrbecker/.local/share/Steam/bootstrap.tar.xz
Reset complete!
Restarting Steam by request...
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/zrbecker/.local/share/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(0_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140726224752_1.dmp
/home/zrbecker/.local/share/Steam/steam.sh: line 755: 19677 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-1b9c79c4-dae4-4fb7-81f4-94d842140726
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-eb3b34e0-594f-475a-92d8-38d592140726
```

---

### Post by oldrocker99 on 2014-07-27
This is exactly why I use nVidia. When the over-the-top-ridiculous shooter Painkiller:Hell and Damnation came out, it ran for me on the day of release, while ATI users had to wait for a fglrx update to run it at all. This seems typical, I'm afraid, and in fact, some games which don't run at all with fglrx run just fine with the open source drivers (according to the Steam forums).

---

