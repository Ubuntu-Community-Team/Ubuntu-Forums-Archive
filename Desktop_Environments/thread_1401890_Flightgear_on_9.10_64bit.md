---
title: "Flightgear on 9.10 64bit?"
date: 2010-02-08
forum: Desktop Environments
---

### Post by Rayston on 2010-02-08
I have installed Flightgear just fine on 9.10 Ubuntu. I did it once via Synaptic, and once via a script in the download center on the flightgear.org site that compiles it on your machine for you. 

In both instances the program starts up, gets to the point where I can see the menu and hear the propellor and then it crashes, Below is what I get when I run the self-compiled version in a terminal. 

:~/fgfs$ fgfs
Model Author: Unknown
Creation Date: 2002-01-01
Version: $Id: c172p.xml,v 1.20 2008/09/01 15:14:33 torsten Exp $
Description: Cessna C-172
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
FGMultiplayMgr - No receiver port, Multiplayermode disabled
KI266 dme indicator #0 initialized
Initializing Nasal Electrical System
fgfs: brw_wm_surface_state.c:624: brw_update_renderbuffer_surface: Assertion `intel->is_g4x || (tile_x == 0 && tile_y == 0)' failed.
Aborted

Anyone have any ideas?

---

