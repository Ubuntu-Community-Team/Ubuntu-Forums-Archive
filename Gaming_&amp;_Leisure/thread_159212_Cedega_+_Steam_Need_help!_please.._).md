---
title: "Cedega + Steam Need help! please.. :)"
date: 2006-04-12
forum: Gaming &amp; Leisure
---

### Post by jfx on 2006-04-12
Well people i am back.. with a new problem ( it seems some higer power wont let me play CS.16 )

ive tryed thunderduck3141 advice for cedega and well i got it, i installed steam no problems at all but when i try to startup steam i get this output message an NO steam..

> X Error of failed request:  BadImplementation (server does not implement operation)
  Major opcode of failed request:  129 (MIT-SHM)
  Minor opcode of failed request:  5 (X_ShmCreatePixmap)
  Serial number of failed request:  3729
  Current serial number in output stream:  3737
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  55 (X_CreateGC)
  Resource id in failed request:  0x2e0037d
  Serial number of failed request:  3732
  Current serial number in output stream:  3737


Does XGL has anything to do with this problem? i hope not cuz i like it. i search the ubuntu forum and the TransGaming forum, but i could get any direct solutions.. 

Can someone please help me out with this one?

Greets Juny

---

### Post by e^e on 2006-04-13
if i understand correctly, you're trying to use cedega under XGL, which wont work, because XGL doesn't have opengl acceleration yet. You'll have to wait till ati or nvidia releases(if ever) the needed extension( GLX_EXT_texture_from_pixmap) in their opengl library. So try under the usual X server.

---

### Post by jfx on 2006-04-13
Got it.. removed XGL en im playing cs with no problems.. i got a few questions..

first i got ventrilo running, i can hear people but i can't talk got the right codecs installed etc.. i can speak while im playing cs ( ingame )

Second.. when i wan't to play cs and ventrilo is running i don't have any sound in cs and when i have cs running and start ventrilo then i dont have sound in cs..

something wrong with my soundcard or drivers.. i found a few howto's on the forum but the didnt work for me. 

Greets Juny

---

