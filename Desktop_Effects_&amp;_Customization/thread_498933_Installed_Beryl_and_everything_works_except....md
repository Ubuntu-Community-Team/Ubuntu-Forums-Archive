---
title: "Installed Beryl and everything works except..."
date: 2007-07-12
forum: Desktop Effects &amp; Customization
---

### Post by snwbord2456 on 2007-07-12
Hi, thanks to Vague and Bren for giving me great guides. Afte installing beryl, I can get the cube to rotate and the effects to work, but the close, minimize, and resize options on the top of every window are missing. How do I enable this? Also I had the front keys (I have a dell the media keys with play pause stop and volume up, volume down) tied to my Banshee player and I was wondering how I would do this over? Thanks for all the help Ubuntu is everything I want. This OS is amazing.

---

### Post by snwbord2456 on 2007-07-12
Also I restarted my system, and Berly no longer works, searched the forums, would this

> in xorg.conf
there is an entry under modules,
it said

load "glx"

I removed it. According to the log file, after it was loaded, AIGLX would start.

fix the problem?

---

### Post by snwbord2456 on 2007-07-12
also when I entered: beryl manager I got 

> :~$ beryl manager
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension


---

