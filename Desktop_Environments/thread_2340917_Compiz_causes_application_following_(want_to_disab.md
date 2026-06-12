---
title: "Compiz causes application following (want to disable)"
date: 2016-10-23
forum: Desktop Environments
---

### Post by UncleBoarder on 2016-10-23
I'm running...

Mate 16.04
VirtualBox 5.0.24
CCSM 9.12.2

When  I start a Windows VM in VirtualBox and then move to another desktop  while Windows is slowly launching, it will follow me to the new desktop.  If I disable Compiz, this following action stops and the VM boots where  I launched it. That's the action I want... Boot where I launch it, stop  following me. :-)

I use the following CCSM features:
**Desktop**
  Expo
  Desktop Cube
  Rotate Cube
**Effects**
  Animations
  Fading Windows
  Wobble Windows
**Utility**
  Compiz Library Toolbox
  Crash handler
  Mouse position polling
  Regex Matching
  Session Management
  Workarounds
**Window Management**
  Move Window
  Resize Window
  Scale

There  must be some setting in CCSM that causes the application to follow the  active desktop. How do I turn off the following "feature"?

---

### Post by UncleBoarder on 2016-10-30
<bump>

---

### Post by CantankRus on 2016-10-30
I think the best you may be able to do is force your application window to load on a specific workspace
using ccsm > Place Windows.
eg 
in the pic, gimp should always start on the first workspace no matter what workspace I'm on.
Once it's loaded it will switch to that workspace though.

---

### Post by UncleBoarder on 2016-11-07
Really?  Who broke it?  Compiz, VirtualBox, or Ubuntu? 

Because as I said, this used to work without any problem. I would always boot up, launch my XP VM, move to the next desktop, launch my Win7 VM, move to the next desktop, launch my Remmina RDP sessions. Everything stayed where I launched it. This is now broken, who do I complain to, which company?  I hate when "upgrades" are worse then the older implementation with no good reason.

---

