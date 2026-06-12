---
title: "dell webcam hardy issues"
date: 2009-02-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by galaphile361 on 2009-02-03
Hi all,

The short version of the problem is that my webcam was working pretty well, but now is no longer working at all.

The long version: My Creative LiveCam VideoIM (VF0350) webcam was working on my Latitude D620 laptop running Ubuntu 8.04, with the only problem being a vertical translucent green bar through the center of the picture (as seen by the person on the other end of the Skype call).  To try and fix this, I went through the instructions on [http://ubuntuforums.org/showthread.php?t=945803&highlight=skype+video](http://ubuntuforums.org/showthread.php?t=945803&highlight=skype+video) but ended up GIVING myself the problem that those people were trying to fix - namely, I get the green and blue noise on my webcam - both in Cheese and Skype - so now it's completely useless.  I think if I could figure out how to uninstall that libv4l library, I'd be back to square one, but if anyone else could help me get this completely fixed, that'd be beyond awesome.

I posted this in the Dell forums because I remember reading about people who fixed their green bar problem by simply updating the video driver to .4814 (a la [http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&ServiceTag=&SystemID=LATITUDE%20D620&os=WW1&osl=en&catid=&impid=](http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&ServiceTag=&SystemID=LATITUDE%20D620&os=WW1&osl=en&catid=&impid=)) but I couldn't do that because Wine couldn't figure out how to run that (I got an error about my system having insufficient resources).  So that's when I tried taking the libv4l route.

Any help would be much appreciated.

Thanks,
Daniel

---

