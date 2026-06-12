---
title: "Freenx problem after upgrading to breezy"
date: 2005-10-14
forum: Desktop Environments
---

### Post by Heretic09 on 2005-10-14
After apt-getting breezy, everything seems fine except I can no longer seem to be able to connect to my machine via freenx. I get:
NXPROXY - Version 1.5.0

Copyright (C) 2001, 2005 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '516'.
Warning: Connected to remote NXPROXY version 1.4.0 with local version 1.5.0.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Remote proxy doesn't support fake authentication.
Info: Forwarding the real X authorization cookie.
Info: Using cache parameters 4/262144/32768KB/32768KB.
Info: Using image cache parameters 1/1/131072KB.
Info: Using adsl link parameters 8192/8/1/5.
Info: Using pack method '16m-jpeg-7' with session 'unix-kde'.
Info: Using ZLIB data compression level 3.
Info: Using ZLIB data threshold set to 32.
Info: Using ZLIB stream compression level 6.
Info: Using remote ZLIB data compression level 3.
Info: Using remote ZLIB stream compression level 6.
Info: No suitable cache file found.
Info: Starting X protocol compression.
Info: Established X server connection.
Info: Using shared memory support in X server.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting.

Any ideas?

---

### Post by Heretic09 on 2005-10-14
Never mind. Apparently the old version is not compatible with breezy. For the new packages, you would need to get it from this source:

deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) ubuntu-seveas freenx

---

### Post by features on 2005-11-16
I am having this exact issue in Breezy, using these repositories.  I have done al the things suggested in the wiki entries for both breezy and the hoary backports versions.

I have set freenx up with the NoMachine keys option.

Anyone have any ideas?

---

### Post by Daz on 2005-11-18
[QUOTE=features]I am having this exact issue in Breezy, using these repositories.  I have done al the things suggested in the wiki entries for both breezy and the hoary backports versions.

I have set freenx up with the NoMachine keys option.[/QUOTE]

Hi,

Have you followed the instructions on [the wiki]("https://wiki.ubuntu.com/FreeNX") for FreeNX after your upgrade?  (To re-install/upgrade NX) as this generally sorts out most problems.

Let us know if you are still having issues.

Ta.

---

### Post by bookemdano on 2005-11-18
[INDENT][I]Never mind. Apparently the old version is not compatible with breezy. For the new packages, you would need to get it from this source:

deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) ubuntu-seveas freenx[/I][/INDENT]

This site doesn't seem to be up.  Anyone know of another site where freenx can be obtained?

---

### Post by ScreemingBlue on 2005-11-25
[QUOTE=bookemdano][INDENT][I]Never mind. Apparently the old version is not compatible with breezy. For the new packages, you would need to get it from this source:

deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) ubuntu-seveas freenx[/I][/INDENT]

This site doesn't seem to be up.  Anyone know of another site where freenx can be obtained?[/QUOTE]


Try [deb http://seveas.ubuntulinux.nl/ breezy-seveas freenx]("deb http://seveas.ubuntulinux.nl/ breezy-seveas freenx") instead.

Cheers:smile: ;)

---

