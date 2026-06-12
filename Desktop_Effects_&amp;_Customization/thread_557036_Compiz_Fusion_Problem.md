---
title: "Compiz Fusion Problem"
date: 2007-09-22
forum: Desktop Effects &amp; Customization
---

### Post by Aero Live™ on 2007-09-22
Hello,
I'm using Ubuntu Gutsy Tribe 5 for almost 2 weeks now and Compiz Fusion suddenly stopped working since 2 days ago.

If I start Compiz in terminal, I'll get this:

ubuntu@computer-boven:~$ compiz --replace
Checking for Xgl: present.
Checking for nVidia: not present.
Checking for Xgl: present.
Enabling Xgl with fglrx ATi drivers...
/usr/bin/compiz: 376: /usr/local/bin/compiz: not found

XGL is working just fine (the process exists in the Gnome System Monitor
3D Acceleration is working too
I'm using an ATi Radeon 9550SE

Do you guys know how to fix the problem?
(It is obvious a file is missing, but I never had this problem before. Maybe it is because of a software update or something like that)

Thanks in advance,
Dennis


btw, My graphic card is since 14 October on the blacklist because apparently there were some problems with it with Compiz Fusion. I have never experienced any, so I removed it from the blacklist in /usr/bin/compiz:
# T="$T 1002:4153" # ATI Rv350

---

### Post by Nano on 2007-09-22
I had exactly the same problem until I upgraded last night. Now compiz starts but Cube plugin doesn't work anymore :)

And I'm experiencing weird problems with GDM resolution. It keeps starting GDM at a 1900x? resolution instead of the one set in gnome.

---

### Post by Aero Live™ on 2007-09-22
Okay, I got a weird fix. I just found a deb package called Fusion Icon on this forum and when I installed it and ran it, compiz did load correctly?!
I still don't get it to run in terminal, but with Fusion Icon everything works like it was before.

---

### Post by sev(n) on 2007-09-22
I've had the same problem recently too. The wrapper for compiz is all messed up. It looks for compiz.real in /usr/local/bin/ when the binary is actually in /usr/bin/ where it's always been.

```
# nano /usr/bin/compiz
```

Editing these settings fixed it for me

COMPIZ_BIN_PATH="/usr/bin/"
PLUGIN_PATH="/usr/lib/compiz/"
COMPIZ_NAME="compiz.real"

---

### Post by p0intman on 2008-01-23
> **sev(n) said:**
> I've had the same problem recently too. The wrapper for compiz is all messed up. It looks for compiz.real in /usr/local/bin/ when the binary is actually in /usr/bin/ where it's always been.

```
# nano /usr/bin/compiz
```

Editing these settings fixed it for me

COMPIZ_BIN_PATH="/usr/bin/"
PLUGIN_PATH="/usr/lib/compiz/"
COMPIZ_NAME="compiz.real"

Had same issue making edits  above resolves issues

---

