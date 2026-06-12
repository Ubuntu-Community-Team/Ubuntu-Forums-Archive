---
title: "Starting Steam creates a seg fault"
date: 2013-12-09
forum: Gaming &amp; Leisure
---

### Post by alex-courtemanche1 on 2013-12-09
Hello,

I'm running 64-bit Ubuntu Linux 13.04 and I'm trying to start Ubuntu but as soon as I start it creates a segmentation fault.

Here it is:
> 
Running Steam on ubuntu 13.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1386125885_client)
/home/acourt/.local/share/Steam/steam.sh: line 755:  6876 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
mv: cannot stat ‘/home/acourt/.steam/registry.vdf’: No such file or directory
Installing bootstrap /home/acourt/.local/share/Steam/bootstrap.tar.xz
Reset complete!
Restarting Steam by request...
Running Steam on ubuntu 13.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/acourt/.local/share/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(1386125885_client)
/home/acourt/.local/share/Steam/steam.sh: line 755:  6993 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@


Anyone have a clue as to what causes this?

---

### Post by venceremos on 2013-12-13
I have the exact same issue. I'm running Kubuntu 13.10 64-bit with fglrx drivers. 

> venc@venc-homelap:~$ fglrxinfo 
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7500M/7600M Series
OpenGL version string: 4.2.12337 Compatibility Profile Context 13.101


Steam reports the following during startup:
> 
venc@venc-homelap:~$ steam
rm: nie mo&#380;na usun&#261;&#263; &#8222;/home/venc/.steam/steam&#8221;: Jest katalogiem
rm: nie mo&#380;na usun&#261;&#263; &#8222;/home/venc/.steam/bin&#8221;: Jest katalogiem
Running Steam on ubuntu 13.10 64-bit
STEAM_RUNTIME is enabled automatically
[2013-12-13 23:36:53] Startup - updater built Dec 11 2013 10:59:29
Installing breakpad exception handler for appid(steam)/version(1386799584_client)
Looks like steam didn't shutdown cleanly, scheduling immediate update check
Installing breakpad exception handler for appid(steam)/version(1386799584_client)
[2013-12-13 23:36:53] Checking for update on startup
[2013-12-13 23:36:53] Checking for available updates...
Installing breakpad exception handler for appid(steam)/version(1386799584_client)
[2013-12-13 23:36:53] Download complete.
[2013-12-13 23:36:53] uninstalled manifest found in /home/venc/.steam/package/steam_client_ubuntu12 (1).
[2013-12-13 23:36:53] Found pending update
[2013-12-13 23:36:53] Installing update...
[2013-12-13 23:36:53] Extracting package...
[2013-12-13 23:36:54] Installing update...
[2013-12-13 23:36:54] Cleaning up...
[2013-12-13 23:36:54] Update complete, launching Steam...
[2013-12-13 23:36:54] Shutdown
Installing breakpad exception handler for appid(steam)/version(1386799584_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20131213233653_1.dmp
/home/venc/.steam/steam.sh: line 755:  7214 Naruszenie ochrony pami&#281;ci   (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Error: Couldn't find bootstrap, it's not safe to reset Steam. Please contact technical support.


any ideas?

---

### Post by pizzalover1974 on 2013-12-15
Well I can see steam active in my taskbar...BUT I right click library or store, e.t.c. and it just sits there like a wet flannel doing nothing. Ubuntu 13.10 broke steam support? If so its a seriously stupid fail. :cry:

I re-installed Windows to get rid of the Wubi GB size restrictions and did a proper dual partition split between Win 7 and Ubuntu. I wanted this to play Steam Linux games and now I cant!!! :(

PS: Im a Win 7 64bit partion with Ubuntu 64bit partion and have a Intel i3 (3ghz dual core), 2 TB Hdd and a Asus Ati 7770 HD card (1 GB).

---

### Post by pizzalover1974 on 2013-12-15
**Update**

Steam Auto updated..seems to have started working now...Must have been fixed quick by steam..Yay!!!

---

### Post by zenolijo on 2014-03-13
Still does not work for me, running Ubuntu 12.04

Have all packages updated and using 2 monitors on a 4850 card

---

### Post by spectatorx on 2014-03-14
It is known problem with steam, it happens since some time. Pretty messed thing.

If you freshly installed steam its first run has to be done on.... gpu open source drivers, not proprietary. If you have proprietary drivers installed remove them, reboot pc, start steam, let steam to update itself, after it you can install proprietary drivers back and have steam running.

---

