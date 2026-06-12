---
title: "doomsday help"
date: 2006-09-05
forum: Gaming &amp; Leisure
---

### Post by n_hendrick on 2006-09-05
When I try to run doomsday I get the following error.....

InitGame: No game library was specified.

what am I doing wrong....

---

### Post by n_hendrick on 2006-09-05
okay... I think I found out what I was doing wrong....I wasn't specifying the "-game" "-file" commandline options....but now when I do specify....it just spits this out.....

Z_Create: New 32.0 MB memory volume.
Con_Init: Initializing the console.
SW_Init: Startup message window opened.
Executable: Version 1.9.0-beta3 Dec 31 2005 (DGL).
Parsing configuration files.
W_Init: Init WADfiles.
--- No IWAD has been specified! Important data might be missing. Are you sure you want to continue?
**ERROR** SW_Init: Startup message window opened.
Executable: Version 1.9.0-beta3 Dec 31 2005 (DGL).
Parsing configuration files.
W_Init: Init WADfiles.

W_CheckIWAD: Init aborted.

Z_Shutdown: Used 1 volumes, total 33554432 bytes.

what am I doing wrong...

---

### Post by n_hendrick on 2006-09-05
I got it to work nevermind...I wasn't specifying a user directory.

---

