---
title: "Steam Crashes"
date: 2013-07-14
forum: Gaming &amp; Leisure
---

### Post by soloman469 on 2013-07-14
I have never had this much trouble with Steam at all until I got my new video card. Before, I couldn't run TF2, and Steam ran like a charm. But now since I got that new video card, TF2 runs, but Steam closes randomly, and automatically without warning. Does it have to do with the video card? Help!

UPDATE: I have tried to open Steam, now it doesn't even RUN. I have a feeling this is getting serious...

YET ANOTHER UPDATE: Now every application I open does the same thing like Steam does. Can anyone help me?

---

### Post by soloman469 on 2013-07-14
Uhm... A little help?

---

### Post by soloman469 on 2013-07-15
Help?

---

### Post by oldrocker99 on 2013-07-15
Which drivers do you have installed? I personally, after 5 years of Linux use, use nVidia, but the fglrx drivers for your card should be installed if you're going to use Steam.

EDIT: OK,  your card is six or seven years old, and AMD/ATI lists the latest driver from 10/10/2010. You might want to consider a video upgrade; you can get a **much** better card than this for <$100 USD.

---

### Post by mastablasta on 2013-07-16
run steam or applicaiton from terminal to see what errors are given (if any)

---

### Post by soloman469 on 2013-07-19
Here ya go: 

chikenpotpah@chikenpotpah-OptiPlex-745:~$ export MESA_GLSL_VERSION_OVERRIDE=130 && steam steam://rungameid/440
Running Steam on ubuntu 12.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1373418487_client)
Installing breakpad exception handler for appid(steam)/version(1373418487_client)
Installing breakpad exception handler for appid(steam)/version(1373418487_client)
unlinked 0 orphaned pipes
removing stale semaphore last operated on by process 4141 with name 0eBlobRegistryMutex_FF79EDFD99D620E602215CCE65CAC1E5
removing stale semaphore last operated on by process 4141 with name 0eBlobRegistrySignal_FF79EDFD99D620E602215CCE65CAC1E5
removing stale semaphore last operated on by process 4141 with name 0emSteamEngineInstance
removing stale semaphore last operated on by process 4141 with name 0eSteamEngineLock
Installing breakpad exception handler for appid(steam)/version(1373418487_client)
[0718/221956:WARNING:proxy_service.cc(958)] PAC support disabled because there is no system implementation
Installing breakpad exception handler for appid(steam)/version(1373418487_client)
Installing breakpad exception handler for appid(steam)/version(1373418487_client)
Installing breakpad exception handler for appid(steam)/version(1373418487_client)
Installing breakpad exception handler for appid(steam)/version(1373418487_client)
Generating new string page texture 2: 48x256, total string texture memory is 49.15 KB
Generating new string page texture 3: 256x256, total string texture memory is 311.30 KB
Installing breakpad exception handler for appid(steam)/version(1373418487_client)
Installing breakpad exception handler for appid(steam)/version(1373418487_client)
Installing breakpad exception handler for appid(steam)/version(1373418487_client)
roaming config store loaded successfully - 861 bytes.
migrating temporary roaming config store


(steam:4347): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:4347): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:4347): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:4347): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:4347): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:4347): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:4347): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:4347): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:4347): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:4347): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:4347): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:4347): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:4347): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:4347): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:4347): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


(steam:4347): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.
Adding license for package 0
Adding license for package 218
Adding license for package 8538
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/assert_20130718221955_1.dmp
/home/chikenpotpah/.local/share/Steam/steam.sh: line 704:  4347 Segmentation fault      $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Finished uploading minidump (out-of-process): success = no
error: HTTP response code said error

---

### Post by soloman469 on 2013-07-19
[COLOR=#000000]Uploading dump (out-of-process) [proxy ''][/COLOR]
[COLOR=#000000]/tmp/dumps/assert_20130718221955_1.dmp[/COLOR]
[COLOR=#000000]/home/chikenpotpah/.local/share/Steam/steam.sh: line 704: 4347 Segmentation fault $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"[/COLOR]
[COLOR=#000000]Finished uploading minidump (out-of-process): success = no[/COLOR]
[COLOR=#000000]error: HTTP response code said error

[/COLOR]

---

### Post by soloman469 on 2013-07-19
[COLOR=#000000]Uploading dump (out-of-process) [proxy ''][/COLOR]
[COLOR=#000000]/tmp/dumps/assert_20130718221955_1.dmp[/COLOR]
[COLOR=#000000]/home/chikenpotpah/.local/share/Steam/steam.sh: line 704: 4347 Segmentation fault $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"[/COLOR]
[COLOR=#000000]Finished uploading minidump (out-of-process): success = no[/COLOR]
[COLOR=#000000]error: HTTP response code said error

[/COLOR]

---

### Post by Johnb0y on 2013-07-19
you try using a different display driver - try another opengl one. if this is happening to all apps.... :confused:

---

