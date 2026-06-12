---
title: "Shogo Demo Installation issues"
date: 2005-11-22
forum: Gaming &amp; Leisure
---

### Post by justjuice on 2005-11-22
Hi, has anyone successfully installed the Linux version of the Shogo demo?

I have two issues. The first is the permissions of all the files it has created.  The file owner is 500, so I can't even open the readme file because I don't have permission (even as root).

The second issue is that I found the shogoLauncher file which I can run, and the launcher opens up, but if I click the Launch Game button, I get the following printed out in the terminal, and Shogo does not start up:

./client -autoconfig autoexec.cfg +savedirectory ./ -rez shogodem.rez +renderdll soft.ren +screenwidth 640 +screenheight 480 +Sound16Bit 1 +NumSWVoices 16 +EnableTjuncs 1 +EnableMultiTex 1 -config autoexec.cfg -conskey 291

Any ideas?  Thanks.

---

### Post by hyperair on 2007-05-05
Try running the "shogo" file instead of "shogolauncher". It doesn't work for me either though. >.< If I want to play Shogo I use the Windows version via Wine.

---

