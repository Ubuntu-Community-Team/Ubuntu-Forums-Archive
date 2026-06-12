---
title: "quake 4 opengl failure"
date: 2008-06-01
forum: Gaming &amp; Leisure
---

### Post by derailed1 on 2008-06-01
I just installed quake 4 on gutsy.  It works nicely.  But, I started playing around with the anti aliasing and moved it up to 16x and now the game won't start.  Does anyone know how I can change the AA from the command prompt?  

These are the last few lines of my command prompt right before it shuts down.

Fatal Error: Unable to initialize OpenGL
--------------- BSE Shutdown ----------------
---------------------------------------------
idRenderSystem::Shutdown()
Sys_Error: Unable to initialize OpenGL


I already played half the game but if it comes down to it, I guess I might have to reinstall.  If thats the case, how do I do that? Do I just remove the entire folder and reinstall or is there a particular process.  That is, if I can't start the game in safe mode or change the AA in the command prompt.

---

### Post by derailed1 on 2008-06-03
Ok guys, I got quake 4 to work again.

I did a few things and finally got it to work.  I deleted the quake 4 folder and tried to reinstall.  Still, same problem.  I looked in the hidden folder .quake4 in my home folder and found the config file.  I tried to change the AA setting from 16 to 0 but that didn't work.  So I deleted the .quake4 folder that included that messed up config file.  I reinstalled quake 4 and it worked.

I lost all my save points but I just used a game cheat to get back to where I was.  I tried copy and pasting the old save folder file but that didn't work.

I love linux, you just have to think a little :)  I hope this helped someone.

---

### Post by liegerm on 2008-11-16
If anyone's interested, you can reset the anti-aliasing setting in .quake4/q4base/QuakeConfig.cfg. Just alter the line 'seta r_multiSamples' to read 'seta r_multiSamples "0"' to turn anti-aliasing off.

---

