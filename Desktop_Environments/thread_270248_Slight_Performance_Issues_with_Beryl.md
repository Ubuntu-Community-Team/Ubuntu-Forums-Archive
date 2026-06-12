---
title: "Slight Performance Issues with Beryl"
date: 2006-10-02
forum: Desktop Environments
---

### Post by PRGUY85 on 2006-10-02
Hey there:

I just installed Beryl over my fresh Dapper install (after completely screwing up xorg.conf without backup).  I followed the second option on the following guide:

[http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome](http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome)

All went good after some tries and I got Beryl up and running.  Yet, I am having sluggish performance with multiple processes or windows open.  Also, whenever my Listen Player displays the bubble box when the next song starts to play, the screen goes black and I have to move the mouse and start clicking to the get the desktop back.  It only happens with that bubbly box on Listen.  I would like to fix this as well as the sometimes sluggish performance.  I have an Ati Radeon 9600 XT with regular ati drivers on repos and I changed the texture filter on the beryl manager to Fast.

Let me know.

Thanks.

---

### Post by PRGUY85 on 2006-10-02
I just typed beryl on a terminal and got this:

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0

Also, glxinfo is now showing Direct Rendering: no which is weird since I had it working an hour or so ago.  What do you all recommend?

---

### Post by PRGUY85 on 2006-10-03
Anyone?

---

### Post by icarus.lnx on 2006-11-17
Try using these two guides, these got my Radeon 9000m (r200) working very well with Beryl...still having some performance troubles with a r250 card though for some reason...

[OSS Radeon with Direct Rendering](https://help.ubuntu.com/community/RadeonDriver)
[Edgy AiGLX - Beryl Wiki](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

---

