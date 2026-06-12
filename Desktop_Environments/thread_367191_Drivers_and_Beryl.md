---
title: "Drivers and Beryl"
date: 2007-02-21
forum: Desktop Environments
---

### Post by int3rsc0p3x on 2007-02-21
Hey guys,

I've already got ATi drivers installed from this guide: [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

3D Acceleration and Direct Rendering are working when I type fglrxinfo.

If I install beryl using this guide: [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html),
which step can I skip to?

Thanks.

---

### Post by ChlkDstTtr on 2007-02-21
I'd follow this guide: [http://ubuntuforums.org/showthread.php?t=274915](http://ubuntuforums.org/showthread.php?t=274915)

Make sure to follow all the steps until the "Broadcom" section. It sounds like  you've taken care of the steps in the first link, but make sure you make the edits to you xorg.conf and then follow the steps in the "Beryl Installation" section.

Just to forewarn you: A lot of people have been having problems with the most recent SVN and stable releases of Beryl. See the last few pages of this thread ([http://forum.beryl-project.org/viewtopic.php?f=43&t=70&st=0&sk=t&sd=a&start=350](http://forum.beryl-project.org/viewtopic.php?f=43&t=70&st=0&sk=t&sd=a&start=350)) and this thread ([http://www.ubuntuforums.org/showthread.php?t=336205&page=6)](http://www.ubuntuforums.org/showthread.php?t=336205&page=6)). For the last week everything has been working great, but as of an update last night now Beryl will freeze everything up so I'm just waiting for an update.

Josh

---

