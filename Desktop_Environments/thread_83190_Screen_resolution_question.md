---
title: "Screen resolution question"
date: 2005-10-28
forum: Desktop Environments
---

### Post by teddyred on 2005-10-28
This is a newbie question...Have recently installed Breezy and am unable to change screen resolution.
It is set at 640/480 with no other settings available.  Have tried re-installing thinking I missed something during setup.
Other than this I have no problems.  Installation was simple and easy.
Really impressed so far. :-)

---

### Post by Ampersand on 2005-10-28
if you run
```
sudo dpkg-reconfigure xserver-xorg
```
from a terminal, you'll be given the opportunity to set up your video hardware again.

---

### Post by Sendervictorius on 2005-10-28
Check out: [http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

It is for Hoary, but same should apply to Breezy.

---

### Post by ad noiseam on 2005-10-28
Try editing the file located at etc/X11/xorg.conf. you will have to do this as a root user, with this code:

```

sudo gedit /etc/X11/xorg.conf

```

This file contains several choices of resolution and refresh rates. Check on Windows (if you are dual booting) what you are using there, and add it to this file, you will then be able to change your resolution in Ubuntu.

Nicolas

---

