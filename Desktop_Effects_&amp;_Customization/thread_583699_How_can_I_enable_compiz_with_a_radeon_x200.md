---
title: "How can I enable compiz with a radeon x200?"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by 7llusion on 2007-10-20
I have completely removed compiz in Gutsy and reinstalled it using the gutsy sources.
I also tried any tutorial on this forum or anywhere else, but it still doesn't work...
I have the fglrx driver with xgl, but compiz still doesn't enable.
What would anyone of you suggest me to install or use to get compiz on Ubuntu Gutsy with an ati integrated x200.
What driver is the best and should I use Xgl or Aiglx?
PS: Vista Aero works flawlessly with this graphics card, please don't tell me my graphics card isn't powerful enough

---

### Post by Good_Newz on 2007-10-21
Ok i am not sure that x200 support compiz yet....apparently new drivers are coming this month that will support it...well if x200 is supported this is how u do it.:
1. Install restricted drivers.
2. Go and edit xorg.conf - > there is a line that says enable compiz change the value from 0 to 1 (remember to make a backup of the config)
3. install xgl server..
4. restart
5. Install compiz manager.
6. Now u should have compiz...

---

### Post by gerfuls on 2007-10-21
follow the guide at [http://ubuntuforums.org/showthread.php?t=585045](http://ubuntuforums.org/showthread.php?t=585045) it should work for your video card too...

---

### Post by 7llusion on 2007-10-21
I've done that, but when even if I'm in xgl and I have compiz, when I enable it terminal tells me this:
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :1.0
anyway around this?

---

