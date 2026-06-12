---
title: "How can block my Track pad while write"
date: 2016-05-15
forum: Desktop Environments
---

### Post by Orlando_Curieles on 2016-05-15
Hi, Recently i  installed Ubuntu 16.04 on my Dell Inspiron 5559, is working great, i don't see any messages saying this program have a error and closed :)  but when i write my touch pad continue working and lost the cursor, this computer have a big touchpad but cannot found a option to block the touch pad.

 Thanks in advise.

---

### Post by vasa1 on 2016-05-15
See if [https://help.ubuntu.com/community/Lubuntu/Mouse#Touchpad_settings](https://help.ubuntu.com/community/Lubuntu/Mouse#Touchpad_settings) helps.

---

### Post by Orlando_Curieles on 2016-05-15
Thanks for your answer, i try this option
syndaemon -d -t
But don't work :(



[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR]

---

### Post by sudodus on 2016-05-15
In standard Ubuntu you can use this method:

Click on the icon with the cog wheel and wrench.

Click on Mouse & Touchpad

and you arrive at a window like the attached screenshot.

You can turn off (and on again) by clicking on the 'button ON' at the right side, or you can fine-tune with the other options, for example turn off 'Tap to click' and 'Two finger scroll'.

---

### Post by Orlando_Curieles on 2016-05-15
Thanks for your answer but i don't wanna turn off my touch pad, I just want turn off while i write

Regards

---

### Post by sudodus on 2016-05-15
Try if it is enough to turn off 'Tap to click' and 'Two finger scroll' :-)

---

### Post by Orlando_Curieles on 2016-05-15
Yes, you are right, turning off the two finger scroll don't move the mouse pointer while write, but i like the two finger scroll, because i come from mac :D .. is a bug ?

---

### Post by sudodus on 2016-05-16
I'm usually not running standard Ubuntu. Most of the time I'm running Lubuntu, where the syndaemon command works:

```
syndaemon -d
```

I think it works in Xubuntu too. But I think the program in the graphical user interface over-rules such simple command lines in standard Ubuntu. Let us hope ***someone who uses standard Ubuntu regularly*** knows how to fix this problem for you :-)

---

### Post by Keith_Helms on 2016-05-28
I had a similar problem with the touchpad doing things I didn't want while I was typing.  I have a startup script that configures the touchpad and sets the palmdetect options to prevent that.

```
#!/bin/bash

/usr/bin/synclient PalmDetect=1
/usr/bin/synclient PalmMinWidth=5
/usr/bin/synclient RTCornerButton=0
/usr/bin/synclient RBCornerButton=0
/usr/bin/synclient ClickFinger1=0
/usr/bin/synclient ClickFinger2=0
/usr/bin/synclient VertEdgeScroll=0
/usr/bin/synclient HorizEdgeScroll=0
/usr/bin/synclient VertTwoFingerScroll=0
```

---

