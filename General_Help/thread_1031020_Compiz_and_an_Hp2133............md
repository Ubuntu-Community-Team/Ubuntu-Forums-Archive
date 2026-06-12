---
title: "Compiz and an Hp2133..........."
date: 2009-01-04
forum: General Help
---

### Post by jdoc on 2009-01-04
Hi there I have been lurking here for awhile and find the forums helpful and thought you guys and gals may be able to help me now.

 I have been trying to get compiz to work on my 2133 I found luvits tut here
[http://ubuntuforums.org/showthread.php?t=1000966&highlight=Hp+2133+compiz](http://ubuntuforums.org/showthread.php?t=1000966&highlight=Hp+2133+compiz)

 and am able to get as far as the root login I try to enter x -configure with x being my ssd. I get a message stating I do not have permission to perform that action. I am a total ubuntu/linux noob so I may be doing something wrong that is totally obvious if I am please bear with me and any help is greatly appreciated.

---

### Post by Forlong on 2009-01-05
If you are referring to a step in the driver's readme. That's not necessary at all.

After you have installed the via driver, simply add
```
	Driver "via"
```
To the **Section "Device"** of your existing /etc/X11/xorg.conf


P.S. do not follow what is listed under "Notes" in that readme. Run Compiz-Check instead: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)
Never mess with files under /usr/bin !!

---

