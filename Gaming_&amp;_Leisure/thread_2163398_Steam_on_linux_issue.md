---
title: "Steam on linux issue"
date: 2013-07-18
forum: Gaming &amp; Leisure
---

### Post by Megacack on 2013-07-18
This problem is really angering me and making me want to quit linux forever :(. I keep getting this error when starting steam "OpenGL GLX context is not using direct rendering, which may cause performance problems.". This error doesn't allow me to play the games because it's not finding the drivers. Yes, I have installed my Nvidia drivers like one million times. This is what happens when I launch it from terminal

Running Steam on ubuntu 13.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1374006490_client)
libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
Installing breakpad exception handler for appid(steam)/version(1374006490_client)
unlinked 0 orphaned pipes
Gtk-Message: Failed to load module "overlay-scrollbar"
Installing breakpad exception handler for appid(steam)/version(1374006490_client)
[0718/052148:WARNING:proxy_service.cc(958)] PAC support disabled because there is no system implementation
libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
Error: OpenGL GLX context is not using direct rendering, which may cause performance problems.


For more information visit [https://support.steampowered.com/kb_article.php?ref=9938-EYZB-7457](https://support.steampowered.com/kb_article.php?ref=9938-EYZB-7457).
Installing breakpad exception handler for appid(steam)/version(1374006490_client)
Installing breakpad exception handler for appid(steam)/version(1374006490_client)
Installing breakpad exception handler for appid(steam)/version(1374006490_client)
Installing breakpad exception handler for appid(steam)/version(1374006490_client)
Installing breakpad exception handler for appid(steam)/version(1374006490_client)
Generating new string page texture 2: 48x256, total string texture memory is 49.15 KB
Generating new string page texture 3: 256x256, total string texture memory is 311.30 KB
Installing breakpad exception handler for appid(steam)/version(1374006490_client)
Installing breakpad exception handler for appid(steam)/version(1374006490_client)
`menu_proxy_module_load': /home/danny/.local/share/Steam/ubuntu12_32/steam: undefined symbol: menu_proxy_module_load


(steam:4114): Gtk-WARNING **: Failed to load type module: (null)


Adding license for package 0
Adding license for package 1
Adding license for package 218
Adding license for package 461
Adding license for package 470
Adding license for package 683
Adding license for package 1465
Adding license for package 1579
Adding license for package 1610
Adding license for package 1679
Adding license for package 1680
Adding license for package 2207
Adding license for package 2546
Adding license for package 2644
Adding license for package 4067
Adding license for package 4559
Adding license for package 4638
Adding license for package 6108
Adding license for package 6442
Adding license for package 6613
Adding license for package 6810
Adding license for package 7410
Adding license for package 7708
Adding license for package 7877
Adding license for package 8185
Adding license for package 8201
Adding license for package 8886
Adding license for package 11612
Adding license for package 11728
Adding license for package 11729
Adding license for package 11734
Adding license for package 11754
Adding license for package 11815
Adding license for package 11860
Adding license for package 12248
Adding license for package 13054
Adding license for package 13184
Adding license for package 13408
Adding license for package 13437
Adding license for package 14337
Adding license for package 14842
Adding license for package 15103
Adding license for package 16222
Adding license for package 16714
Adding license for package 17079
Adding license for package 18029
Adding license for package 25518
Adding license for package 26117
Adding license for package 26331
roaming config store loaded successfully - 3978 bytes.
migrating temporary roaming config store
Installing breakpad exception handler for appid(steam)/version(1374006490_client)
ExecCommandLine: "/home/danny/.local/share/Steam/ubuntu12_32/steam"
Generating new string page texture 94: 128x256, total string texture memory is 442.37 KB
Generating new string page texture 95: 64x256, total string texture memory is 507.90 KB
Generating new string page texture 100: 1024x256, total string texture memory is 1.56 MB
Generating new string page texture 101: 128x256, total string texture memory is 131.07 KB
Generating new string page texture 102: 32x256, total string texture memory is 1.59 MB
Generating new string page texture 103: 8x256, total string texture memory is 1.60 MB


(steam:4114): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:4114): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:4114): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:4114): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:4114): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:4114): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:4114): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:4114): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.
Generating new string page texture 107: 128x256, total string texture memory is 1.73 MB
Generating new string page texture 108: 256x256, total string texture memory is 1.99 MB
Generating new string page texture 109: 384x256, total string texture memory is 2.38 MB
Generating new string page texture 110: 128x256, total string texture memory is 2.51 MB
Generating new string page texture 111: 24x256, total string texture memory is 2.54 MB
System startup time: 7.33 seconds
libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
CAPIJobRequestUserStats - Server response failed 2
Running Steam on ubuntu 13.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/danny/.local/share/Steam/ubuntu12_32/steam-runtime
ExecCommandLine: "/home/danny/.steam/root/ubuntu12_32/steam steam://open/driverhelperready"
ExecSteamURL: "steam://open/driverhelperready"
Generating new string page texture 119: 256x256, total string texture memory is 2.80 MB



If someone figures the problem out, I will love them FOREVER!

---

### Post by synaptix on 2013-07-18
This may help:

[http://steamcommunity.com/app/221410/discussions/5/828939163894026239/](http://steamcommunity.com/app/221410/discussions/5/828939163894026239/)

---

### Post by ZoiaGuyver on 2013-07-18
I've came across this a few times before, If your running proprietary Nvidia or AMD drivers make sure they are the latest available. Once you have done that you should install ia32-libs (this will give you quite a few files but should fix the problems).

Just do:

sudo apt-get update
sudo apt-get install ia32-libs

Thats fixed it on atleast 3 or 4 machines for me.

---

### Post by Johnb0y on 2013-07-19
> **ZoiaGuyver said:**
> I've came across this a few times before, If your running proprietary Nvidia or AMD drivers make sure they are the latest available. Once you have done that you should install ia32-libs (this will give you quite a few files but should fix the problems).

Just do:

sudo apt-get update
sudo apt-get install ia32-libs

Thats fixed it on atleast 3 or 4 machines for me.

this has resolved a few issues i have had in the past. 

the only thing is i would try changing/using a newer version - run update first then if they fail - install ia32-libs.... :)

---

