---
title: "GlxChooseVisual failed apperears when opening steam in 14.10"
date: 2015-01-23
forum: Gaming &amp; Leisure
---

### Post by allen10 on 2015-01-23
I am running xbuntu 14.10 and I have an AMD radeon 6450 the fglrx drivers were installed from synaptic on a fresh install.
Now when I open Steam I get that error and it crashes.
I reinstalled because of openGL problems with the proprietary Drivers from AMD anyway this is my terminal output from when I open steam but I can't make heads or tails of it because I have never had a video card issue. Thanks in advance,

Running Steam on ubuntu 14.10 64-bit
STEAM_RUNTIME is enabled automatically
[2015-01-23 14:45:29] Startup - updater built Jan 19 2015 10:11:32
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadRequest (invalid request code or no such operation)
Major opcode of failed request:  157 (ATIFGLEXTENSION)
Minor opcode of failed request:  66
Serial number of failed request:  13
xerror_handler: X failed, continuing
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadRequest (invalid request code or no such operation)
Major opcode of failed request:  156 (GLX)
Minor opcode of failed request:  19 (X_GLXQueryServerString)
Serial number of failed request:  47
xerror_handler: X failed, continuing
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadRequest (invalid request code or no such operation)
Major opcode of failed request:  156 (GLX)
Minor opcode of failed request:  19 (X_GLXQueryServerString)
Serial number of failed request:  78
xerror_handler: X failed, continuing
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadRequest (invalid request code or no such operation)
Major opcode of failed request:  156 (GLX)
Minor opcode of failed request:  14 (X_GLXGetVisualConfigs)
Serial number of failed request:  109
xerror_handler: X failed, continuing
Looks like steam didn't shutdown cleanly, scheduling immediate update check
[2015-01-23 14:45:29] Checking for update on startup
[2015-01-23 14:45:29] Checking for available updates...
[2015-01-23 14:45:30] Download skipped: /client/steam_client_ubuntu12 version 1421694684, installed version 1421694684
[2015-01-23 14:45:30] Nothing to do
[2015-01-23 14:45:30] Verifying installation...
[2015-01-23 14:45:30] Performing checksum verification of executable files
[2015-01-23 14:45:30] Verification complete
Requested Force create but SharedObjectMutex already created
Forced create but already created for SharedObjectEvent
Forced create but already created for SharedObjectEvent

---

