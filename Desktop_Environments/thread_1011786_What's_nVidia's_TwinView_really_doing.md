---
title: "What's nVidia's TwinView really doing?"
date: 2008-12-15
forum: Desktop Environments
---

### Post by knaik on 2008-12-15
So I don't have a usual GPU/monitor config: two cards, three displays, two X screns and I want one to have TwinView/Xinerama (with compiz) and the other to be plain (no dual-head or compiz).
I spent the weekend trying to figure out how all the Xserver stuff works and I really think nVidia's TwinView is really just passing the same info that Xinerama would to the desktop manager or Xserver (I dunno whats handling it).  I assume this because nVidia offers xorg.conf options like "TwinViewXineramaInfoOrder" and "NoTwinViewXineramaInfo"
So my question is, does anyone know the implementation details of TwinView?  What's it talking to or passing its info to?  A library?
I've read lots that says its just setting up one X screen but from the xorg options it provides and how it was setting up my 2 screen desktop, I beg to differ; it's acting too much like Xinerama for me to believe that.

Thanks.  I'm new to the forums but have been using Kubuntu for almost a year now.

---

### Post by CHaoSlayeR on 2009-01-10
Hi knaik,

if anyone knew what the nvidia driver is doing internally to achieve dual head setups the open source drivers nv and nouveau whould be much more up to date as they are now.

Sorry to say that.

C]-[aoZ

---

