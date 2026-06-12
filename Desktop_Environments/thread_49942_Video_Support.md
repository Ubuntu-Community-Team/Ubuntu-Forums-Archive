---
title: "Video Support"
date: 2005-07-18
forum: Desktop Environments
---

### Post by baaaan on 2005-07-18
I have the Intel 82865G onboard video adapter. I attempted to install Ubuntu, which I was able to do successfully using the Hoary release.

However, I was not able to get any sort of video mode higher than 640x480. I downloaded updated drivers from Intel, but installing them completely borked X Server and it would no longer load.

Is there any plans to offer inherent support for this video adapter? Or will I never be able to use Ubuntu on this system?

Thanks.

Brandon

---

### Post by damonw5 on 2005-07-18
[QUOTE=baaaan]I have the Intel 82865G onboard video adapter. I attempted to install Ubuntu, which I was able to do successfully using the Hoary release.

However, I was not able to get any sort of video mode higher than 640x480. I downloaded updated drivers from Intel, but installing them completely borked X Server and it would no longer load.

Is there any plans to offer inherent support for this video adapter? Or will I never be able to use Ubuntu on this system?

Thanks.

Brandon[/QUOTE]
 Try using the "vesa" driver instead of the one that is currently specified in /etc/X11/xorg.conf. This will at least get you up and running with a higher resolution. Do you need help with editing the file? Let us know.

Also look here for some good ideas regarding your video adapter: [http://www.linuxquestions.org/hcl/showproduct.php?product=813&sort=8&cat=all&page=1](http://www.linuxquestions.org/hcl/showproduct.php?product=813&sort=8&cat=all&page=1)

---

