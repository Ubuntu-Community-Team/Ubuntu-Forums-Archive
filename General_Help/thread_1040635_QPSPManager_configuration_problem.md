---
title: "QPSPManager configuration problem"
date: 2009-01-15
forum: General Help
---

### Post by daxdog on 2009-01-15
I have QPSPManager 2.0.2 running on my kubuntu laptop.  It runs fine except when I want to transfer a video.  First of all, I am not sure what to put in the "FFmpeg Location" box on the options tab.  I have tried many things including /usr/local/share/pspvc/bin/ffmpeg and also the PSPVC program.  Putting the ffmpeg file for the option gives me a "Status: encoding failed" error message when I try to convert.  If I put the PSPVC program in the field it will launch over and over.  Even if you convert the file it will just keep taking you back to the PSPVC program.

Any ideas?

---

### Post by lunarcloud on 2009-05-06
Try recompiling pspvc then qpspmanager [https://help.ubuntu.com/community/PSP](https://help.ubuntu.com/community/PSP)

I did as you noted there (linking to pspvc's copy of ffmpeg) in qpspmanager and it worked!

---

