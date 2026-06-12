---
title: "Issue with Microsoft fonts"
date: 2008-12-30
forum: General Help
---

### Post by Zippat0 on 2008-12-30
Hello everybody, this is my first post here. I have a problem with Microsoft fonts. When I install "mstcorefonts" or even "xfstt" package for truetype fonts i can not see the fonts very well. I decided to uninstall the packages, because they were not so important for me, but now i have the same problem with Wine. I put here a screenshot to make you understand the problem.

Fonts are disturbed, stained. If I install any of the two packages mentioned i have this problem with every font of the desktop which uses them (like Firefox or screenlets). Any idea?

I have a Nvidia Geforce4 440-MX SE, Ubuntu 8.10, x.org 1.5.2, gpu drivers are downloaded and installed by nvidia website (NVIDIA-Linux-x86-96.43.09-pkg1), everything is installed correctly.


Here is the picture. Have you ever seen anything similar?

---

### Post by xjcannonx on 2008-12-30
looks like your video drivers are old, you should be able to go to System-->Administration-->Hardware Drivers (think thats it) and enable the most recent one...177.xx there is also a newer beta version here [[COLOR="Blue"]http://www.nvidia.com/object/linux_display_ia32_180.17.html[/COLOR]]("http://www.nvidia.com/object/linux_display_ia32_180.17.html") 

I would say to try the 177.xx driver first

---

### Post by Zippat0 on 2009-01-01
Do you think I can install those drivers? Looking [this thread]("http://www.nvnews.net/vbulletin/showthread.php?t=122606") from nvidia forum it seems I can only install 96.43.xx drivers for my gpu :( and it seems to be confirmed by the appendix A linked in that post.

Uh, I also checked System>Administration>... and the drivers suggested there are 96.xx, and I think they are the same I downloaded from nvidia.

---

### Post by Zippat0 on 2009-01-04
Any idea? am I wrong about drivers?

---

### Post by Zippat0 on 2009-01-08
Up.............. .......

---

### Post by undoIT on 2009-01-12
Imagine my surprise this morning at 6:30 AM when I opened my stock trading program Quotetracker in Wine and everything looked like it was in Arabic. Have I been hacked!!!?

Well, actually everything was in Tibetan, just the font is set too small to recognize it right away in Quotetracker. Over the weekend I had installed a Tibetan publishing tool called Pechamaker to attempt to send some Tibetan texts I had typed up years ago to somebody who had requested them. But I realized I wouldn't be able to print to PDF so I ended up using the Windows install in Virtualbox.

I had to delete the Tibetan fonts that had been installed to this folder:

/.wine/drive_c/windows/Fonts

I guess that had gotten set as the system font. Checking that folder for additionally installed fonts may help solve your problem.

---

### Post by gatorbrit on 2009-02-02
Try this...



[http://ubuntuforums.org/showthread.php?t=1009930](http://ubuntuforums.org/showthread.php?t=1009930)

---

### Post by fragos on 2009-02-02
IMHO the best looking basic fonts are in the open source DejaVu family. The most disapointing fonts on my system are those from MS.

---

