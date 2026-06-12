---
title: "[SOLVED] Problem with the game &amp;quot;PlaneShift&amp;quot;"
date: 2007-08-08
forum: Gaming &amp; Leisure
---

### Post by Akuma Shiro on 2007-08-08
[PlaneShift]("http://www.planeshift.it/") is a OSS MMORPG. When I launch the game, I get in place of text, dots and dashes, like the text is corrupt or something.

I( downloaded and installed the version for x86 Linux (the type of Ubuntu I have) from a .bin file.

They make a version for Windows, but I want to try and stay away from that.

Anyone have any ideas?

PS. When I get home, I will ty and post some screen shots.

---

### Post by theotherbastard on 2007-09-15
I too have been having this problem and am currently trying to work my way through it.

It looks as though whatever Font system it is trying to use is not present or is not working properly.

What I am basing much of my troubleshooting on is data found in the /opt/PlaneShift/pssetup.cfg file.  There are a few lines that deal with fonts.  But, as of yet nothing I have tried has worked.  But I have not given up yet.

---

### Post by theotherbastard on 2007-09-15
Fixed!  Found this in another thead:


Solution: Font multitexturing has been broken, try the following:
Open up the file Planeshift3D/data/config/r3dopengl.cfg in a text editor, and find this line:
Video.OpenGL.FontCache.UseMultiTexturing = yes
and change yes to no.

---

### Post by Het Irv on 2007-09-15
> **theotherbastard said:**
> Fixed!  Found this in another thead:


Solution: Font multitexturing has been broken, try the following:
Open up the file Planeshift3D/data/config/r3dopengl.cfg in a text editor, and find this line:
Video.OpenGL.FontCache.UseMultiTexturing = yes
and change yes to no.

This is my problem but its not working for me.  Can you link the other thread?

I Have an ATI Radion 9200. I don't know if I correctly installed the drivers.

---

