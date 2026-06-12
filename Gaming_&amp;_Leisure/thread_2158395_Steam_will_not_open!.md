---
title: "Steam will not open!"
date: 2013-06-28
forum: Gaming &amp; Leisure
---

### Post by cpuv2 on 2013-06-28
When i click on steam absolutely nothing happens. Is there something i can do about this?

---

### Post by Kjellson on 2013-06-29
Try to open it through a terminal. Just open a terminal and enter "steam" and see what happens. You´ll probably get some code, copy and paste it into this thread.

---

### Post by cpuv2 on 2013-06-29
$ steam
Running Steam on ubuntu 12.04 32-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)

---

### Post by mentorious on 2013-06-29
Type
```
[COLOR=#333333][FONT=Consolas]steam --reset[/FONT][/COLOR]
```

and paste the output here :)

---

### Post by cpuv2 on 2013-07-01
i have pretty old hardware btw im running off a pentium 4 and an intel chipset but thats not my problem. i did the code it said steam is running so i went into the system monitor and its running for some reason. but still refuses to open.

---

### Post by efflandt on 2013-07-02
That 0_client should likely be a number larger than zero, but not sure where that number comes from. Very often steam issues are video driver related.

This is an example of terminal output just successfully starting steam and quitting from within it:```
Running Steam on ubuntu 12.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1372695573_client)
Installing breakpad exception handler for appid(steam)/version(1372695573_client)
unlinked 0 orphaned pipes
Installing breakpad exception handler for appid(steam)/version(1372695573_client)
[0702/011804:WARNING:proxy_service.cc(958)] PAC support disabled because there is no system implementation
Installing breakpad exception handler for appid(steam)/version(1372695573_client)
Installing breakpad exception handler for appid(steam)/version(1372695573_client)
Installing breakpad exception handler for appid(steam)/version(1372695573_client)
Installing breakpad exception handler for appid(steam)/version(1372695573_client)
Generating new string page texture 2: 48x256, total string texture memory is 49.15 KB
Generating new string page texture 3: 256x256, total string texture memory is 311.30 KB
Installing breakpad exception handler for appid(steam)/version(1372695573_client)
Installing breakpad exception handler for appid(steam)/version(1372695573_client)
Installing breakpad exception handler for appid(steam)/version(1372695573_client)
`menu_proxy_module_load': /home/efflandt/.local/share/Steam/ubuntu12_32/steam: undefined symbol: menu_proxy_module_load

(steam:10249): Gtk-WARNING **: Failed to load type module: (null)


(steam:10249): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:10249): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:10249): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:10249): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:10249): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:10249): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:10249): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:10249): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:10249): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:10249): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:10249): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:10249): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:10249): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:10249): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:10249): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:10249): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.
Adding license for package 0
Adding license for package 34
Adding license for package 37
Adding license for package 8538
Adding license for package 26827
Adding license for package 28890
roaming config store loaded successfully - 921 bytes.
migrating temporary roaming config store
Installing breakpad exception handler for appid(steam)/version(1372695573_client)
ExecCommandLine: "/home/efflandt/.local/share/Steam/ubuntu12_32/steam"
Generating new string page texture 72: 128x256, total string texture memory is 442.37 KB
Generating new string page texture 73: 128x256, total string texture memory is 131.07 KB
Generating new string page texture 74: 32x256, total string texture memory is 475.14 KB
Generating new string page texture 75: 8x256, total string texture memory is 483.33 KB
Installing breakpad exception handler for appid(steam)/version(1372695573_client)
Generating new string page texture 77: 64x256, total string texture memory is 548.86 KB
System startup time: 6.10 seconds
Generating new string page texture 90: 24x256, total string texture memory is 573.44 KB
Running Steam on ubuntu 12.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/efflandt/.local/share/Steam/ubuntu12_32/steam-runtime
unlinked 2 orphaned pipes
CAsyncIOManager: 0 threads terminating.  0 reads, 0 writes, 0 deferrals.
CAsyncIOManager: 9612 single object sleeps, 0 multi object sleeps
CAsyncIOManager: 0 single object alertable sleeps, 1 multi object alertable sleeps
[2013-07-02 01:18:03] Startup - updater built Jun 29 2013 11:13:20
[2013-07-02 01:18:03] Opted in to client beta 'publicbeta' via beta file
[2013-07-02 01:18:03] Verifying installation...
[2013-07-02 01:18:03] Verification complete
Shutting down. . .
[2013-07-02 01:18:23] Shutdown
```

---

