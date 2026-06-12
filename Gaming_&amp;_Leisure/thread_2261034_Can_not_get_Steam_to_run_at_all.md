---
title: "Can not get Steam to run at all"
date: 2015-01-15
forum: Gaming &amp; Leisure
---

### Post by Preston_Thomas on 2015-01-15
I have a fresh install of Ubuntu 14.04 64bit and I have done all the updates and installed my AMD Radeon 6850 driver with no problems.

Upon installing Steam from the offical web site I have encountered an error where when i click on the icon for it to run nothing happens. Looking more into it on the terminal I get this error once i run Steam

>  Running Steam on ubuntu 14.04 64-bitSTEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20150116023250_1.dmp
Finished uploading minidump (out-of-process): success = no
error: libcurl.so: cannot open shared object file: No such file or directory
/home/gamer/.local/share/Steam/steam.sh: line 730: 10603 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$STEAMEXEPATH" "$@"
mv: cannot stat ‘/home/gamer/.steam/registry.vdf’: No such file or directory
Installing bootstrap /home/gamer/.local/share/Steam/bootstrap.tar.xz
Reset complete!
Restarting Steam by request...
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/gamer/.local/share/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(0_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20150116023252_1.dmp
Finished uploading minidump (out-of-process): success = no
error: libcurl.so: cannot open shared object file: No such file or directory
/home/gamer/.local/share/Steam/steam.sh: line 730: 10729 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$STEAMEXEPATH" "$@"

Does anyone know how to fix this problem please ?

thanks

---

### Post by Preston_Thomas on 2015-01-16
Just found the solution here if anyone has the same problem.

[http://askubuntu.com/questions/517596/steam-wont-start-on-ubuntu-14-04-1](http://askubuntu.com/questions/517596/steam-wont-start-on-ubuntu-14-04-1)

---

