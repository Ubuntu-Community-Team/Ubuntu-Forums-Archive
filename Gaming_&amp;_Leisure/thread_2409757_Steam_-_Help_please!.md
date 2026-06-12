---
title: "Steam - Help please!"
date: 2019-01-06
forum: Gaming &amp; Leisure
---

### Post by zakebramley on 2019-01-06
I am a linux user without sudo permissions. I can't ask the admin to help me, as he "can't be bothered". I wanted to install steam, so I found the steam.sh file and ran it. It worked! I was able to play a game (8BitMMO).  It was all running smoothly. I didn't have all of the dependencies installed (and couldn't install them as I don't have root) but the steam program seemed to be ignoring that, Until it asked for an update. I updated it, and suddenly it doesn't work any more. Here is what I get when I run the sh file in the terminal:

```
./steam.sh
Running Steam on ubuntu 16.04 64-bit
STEAM_RUNTIME is enabled automatically
Pins up-to-date!
Error: You are missing the following 32-bit libraries, and Steam may not run:
libdrm.so.2
[2019-01-06 16:41:19] Startup - updater built Nov 26 2018 20:15:21
Installing breakpad exception handler for appid(steam)/version(1543346820)
Looks like steam didn't shutdown cleanly, scheduling immediate update check
Installing breakpad exception handler for appid(steam)/version(1543346820)
[2019-01-06 16:41:20] Checking for update on startup
[2019-01-06 16:41:20] Checking for available updates...
[2019-01-06 16:41:20] Downloading manifest: client-download.steampowered.com/client/steam_client_ubuntu12
Installing breakpad exception handler for appid(steam)/version(1543346820)
[2019-01-06 16:41:21] Download skipped: /client/steam_client_ubuntu12 version 1543346820, installed version 1543346820
[2019-01-06 16:41:21] Nothing to do
[2019-01-06 16:41:21] Verifying installation...
[2019-01-06 16:41:21] Performing checksum verification of executable files
[2019-01-06 16:41:30] Verification complete
Failed to load steamui.so - dlerror(): libdrm.so.2: wrong ELF class: ELFCLASS64
[2019-01-06 16:41:33] Shutdown
Installing breakpad exception handler for appid(steam)/version(1543346820)
CWorkThreadPool::~CWorkThreadPool: work processing queue not empty: 3 items discarded.
Installing breakpad exception handler for appid(steam)/version(1543346820)
```

Please help!

---

### Post by oldrocker99 on 2019-01-06
Steam absolutely requires a bunch of 32-bit libraries. Is there NO way to get the admin to give you even one-time sudo access? How big is the system you're on?

---

### Post by QIII on 2019-01-06
Hello!

This is a discussion to have with the administrator.  We will not provide assistance in an attempt to circumvent the admin's policies.

Closed.

---

