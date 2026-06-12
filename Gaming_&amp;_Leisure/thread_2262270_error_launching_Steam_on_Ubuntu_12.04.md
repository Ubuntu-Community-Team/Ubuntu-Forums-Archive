---
title: "error launching Steam on Ubuntu 12.04"
date: 2015-01-23
forum: Gaming &amp; Leisure
---

### Post by rodrigo1406 on 2015-01-23
Hi! I wanna play Counter Strike 1.6 on Ubuntu 12.04.
I managed to install Steam, it updated ok, but crashed when launching,
the console log is:

$ steam
Running Steam on ubuntu 12.04 32-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1422054110)
Installing breakpad exception handler for appid(steam)/version(1422054110)
Installing breakpad exception handler for appid(steam)/version(1422054110)
Installing breakpad exception handler for appid(steamwebhelper)/version(20150123134624)
Installing breakpad exception handler for appid(steamwebhelper)/version(1422020784)
Installing breakpad exception handler for appid(steamwebhelper)/version(20150123134624)
Installing breakpad exception handler for appid(steamwebhelper)/version(1422020784)
Installing breakpad exception handler for appid(steamwebhelper)/version(1422020784)
Installing breakpad exception handler for appid(steam)/version(1422054110)
Installing breakpad exception handler for appid(steam)/version(1422054110)
Installing breakpad exception handler for appid(steam)/version(1422054110)
Installing breakpad exception handler for appid(steam)/version(1422054110)
Installing breakpad exception handler for appid(steam)/version(1422054110)
Installing breakpad exception handler for appid(steam)/version(1422054110)
Installing breakpad exception handler for appid(steam)/version(1422054110)
FillInMachineIDInfo took a total of 0 milliseconds
Installing breakpad exception handler for appid(steam)/version(1422054110)
Installing breakpad exception handler for appid(steam)/version(1422054110)
[0123/233402:ERROR:renderer_main.cc(227)] Running without renderer sandbox
[0123/233402:ERROR:renderer_main.cc(227)] Running without renderer sandbox
Generating new string page texture 12: 48x256, total string texture memory is 49,15 KB
Generating new string page texture 13: 256x256, total string texture memory is 311,30 KB
Generating new string page texture 14: 128x256, total string texture memory is 442,37 KB
Generating new string page texture 15: 384x256, total string texture memory is 835,58 KB
Generating new string page texture 18: 64x256, total string texture memory is 901,12 KB
Generating new string page texture 20: 8x256, total string texture memory is 909,31 KB
Generating new string page texture 21: 16x256, total string texture memory is 925,70 KB
Generating new string page texture 22: 24x256, total string texture memory is 950,27 KB
Generating new string page texture 23: 32x256, total string texture memory is 983,04 KB
Installing breakpad exception handler for appid(steam)/version(1422054110)
Installing breakpad exception handler for appid(steam)/version(1422054110)
Installing breakpad exception handler for appid(steam)/version(1422054110)
Installing breakpad exception handler for appid(steam)/version(1422054110)
`menu_proxy_module_load': /home/rodrigo/.local/share/Steam/ubuntu12_32/steam: undefined symbol: menu_proxy_module_load

(steam:19337): Gtk-WARNING **: Failed to load type module: (null)

Installing breakpad exception handler for appid(steam)/version(1422054110)
Installing breakpad exception handler for appid(steam)/version(1422054110)
Installing breakpad exception handler for appid(steam)/version(1422054110)
Installing breakpad exception handler for appid(steam)/version(1422054110)
Installing breakpad exception handler for appid(steam)/version(1422054110)
Installing breakpad exception handler for appid(steam)/version(1422054110)
Installing breakpad exception handler for appid(steam)/version(1422054110)
Installing breakpad exception handler for appid(steam)/version(1422054110)
Installing breakpad exception handler for appid(steam)/version(1422054110)
Generating new string page texture 31: 1024x256, total string texture memory is 2,03 MB
Installing breakpad exception handler for appid(steam)/version(1422054110)
process  19337: The last reference on a connection was dropped without closing  the connection. This is a bug in an application. See  dbus_connection_unref() documentation for details.
Most likely, the application was supposed to call dbus_connection_close(), since this is a private connection.
Requested Force create but SharedObjectMutex already created
Forced create but already created for SharedObjectEvent
Forced create but already created for SharedObjectEvent
Timed out waiting for mutex in GetInternal()
Installing breakpad exception handler for appid(steam)/version(1422054110)
[2015-01-23 23:34:00] Startup - updater built Jan 23 2015 13:46:31
Looks like steam didn't shutdown cleanly, scheduling immediate update check
[2015-01-23 23:34:00] Checking for update on startup
[2015-01-23 23:34:00] Checking for available updates...
[2015-01-23 23:34:01] Download skipped: /client/steam_client_ubuntu12 version 1422054110, installed version 1422054110
[2015-01-23 23:34:01] Nothing to do
[2015-01-23 23:34:01] Verifying installation...
[2015-01-23 23:34:01] Performing checksum verification of executable files
[2015-01-23 23:34:01] Verification complete
[2015-01-23 23:37:32] Shutdown
$ 

Anybody run into same problem? Looks like this is the core of the message:

Installing breakpad exception handler for appid(steam)/version(1422054110)
process  19337: The last reference on a connection was dropped without closing  the connection. This is a bug in an application. See  dbus_connection_unref() documentation for details.
Most likely, the application was supposed to call dbus_connection_close(), since this is a private connection.
Requested Force create but SharedObjectMutex already created
Forced create but already created for SharedObjectEvent
Forced create but already created for SharedObjectEvent
Timed out waiting for mutex in GetInternal()
Installing breakpad exception handler for appid(steam)/version(1422054110)
[2015-01-23 23:34:00] Startup - updater built Jan 23 2015 13:46:31
Looks like steam didn't shutdown cleanly, scheduling immediate update check

Thanks for any help!

Rodrigo.

---

### Post by mooreted on 2015-01-24
What video card do you have and did you install the drivers for it? The errors below look like problems with the video driver.

[0123/233402:ERROR:renderer_main.cc(227)] Running without renderer sandbox
[0123/233402:ERROR:renderer_main.cc(227)] Running without renderer sandbox

---

### Post by QIII on 2015-01-24
If you are using an ATI card and fglrx driver, you have to uninstall the driver, reboot, re-update Steam, reinstall the driver and reboot.

Really.

---

### Post by rodrigo1406 on 2015-01-24
(how to erase this?)

---

### Post by rodrigo1406 on 2015-01-24
Thanks for the help.

lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 8400 GS Rev. 3] (rev a2)

And the recommended driver looks ok

[IMG]http://dao.url.ph/tree/prtsc.png[/IMG]

---

### Post by mooreted on 2015-01-24
Since you have an older "legacy" video card, you might try one of the older drivers.

[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

---

### Post by efflandt on 2015-01-24
Web search "nvidia-173 ubuntu 12.04"

---

### Post by Seth-666 on 2015-04-22
Hello. i discovered a bug on stea, cs 1.6, when i pres alt+tab my sound is still in the background . what can be the problem, from where ? what should i search for on the web to repaire it...? can somebody tell me?

---

