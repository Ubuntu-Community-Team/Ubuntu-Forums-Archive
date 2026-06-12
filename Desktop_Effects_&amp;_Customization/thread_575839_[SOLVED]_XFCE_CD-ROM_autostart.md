---
title: "[SOLVED] XFCE CD-ROM autostart"
date: 2007-10-14
forum: Desktop Effects &amp; Customization
---

### Post by Tlon on 2007-10-14
By default, whenever a CD-ROM gets mounted, XFCE opens an app tied to whatever kind of media the disk contains (so if I put in an audio CD, it starts into totem/xine, etc.).  I want it to continue to auto-mount the disks, but I do NOT want it to load any program in response.  How can I kill the autostart option?

---

### Post by Tlon on 2007-10-15
Well, nobody responded, so I did some leg-work.  Here's the fix:

Open up a command prompt and type:

thunar-volman --configure

Use the resultant dialogue window to set your autostarts however you'd like.

---

### Post by santiagoward2000 on 2007-10-15
Good to know I can disable it if I get tired of the autorun.

---

