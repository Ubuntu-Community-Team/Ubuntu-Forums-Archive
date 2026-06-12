---
title: "3D games cause blank screen, then desktop"
date: 2008-08-29
forum: Gaming &amp; Leisure
---

### Post by BWPanda on 2008-08-29
I've just downloaded some games from the Ubuntu repositories (namely Frozen Bubble, Neverball/Neverputt and SuperTuxKart).

While Frozen Bubble works, the others don't. When I select them from the menu, the screen goes black/blank (as if loading a full-screen game), but then goes back to the desktop as if nothing happened...
Because Frozen Bubble worked, I'm guessing it's got something to do with the other games being 3D...?

I'm running Hardy on a new Dell Inspiron 530 with an ATI Radeon HD 2600 graphics card. I'm also running dual screens, in case that's got anything to do with it...
Any help would be much appreciated!

---

### Post by eragon100 on 2008-08-29
Have you got the restricted drivers installed? you need them for 3d on the 2XXX series, and can get them by going to System -> Administration -> Hardware Drivers, and selecting the option for installing video drivers. Reboot your computer when it's finished. You might also want to disable desktop effects, because they often cause trouble with 3d games (much more often than not.)

After you have installed the video drivers it should work, but feel free to post again if it doesn't :wink:

---

### Post by BWPanda on 2008-08-29
Hardware drivers says the device driver 'ATI accelerated graphics driver' is enabled and in use.
Visual effects are set to 'None'.
Problem still occurs.

---

### Post by eragon100 on 2008-08-29
Do other 3d games work? Try the great free first person shooter nexuiz.
(I have never played any of the games you mention. I rather kill people :))

---

### Post by Crafty Kisses on 2008-08-29
Sounds like your X is restarting, post the results of this command > glxinfo

---

### Post by BWPanda on 2008-08-29
Thanks eragon, but I'd rather not download a 300Mb file just to test something. Let me know of any other games I could test (preferably under 100Mb) and I'll gladly download them.

> **Codename said:**
> Sounds like your X is restarting, post the results of this command > glxinfo
```
~$ glxinfo
name of display: :0.0


```
That's all I got. It didn't go back to the command prompt (or whatever you call it), the cursor just kept flashing away on the line below "name of...". I had to Ctrl-C to close it.

---

### Post by BWPanda on 2008-08-30
UPDATE: I installed a few more games;
- Gweled (which works fine)
- lbreackout 2 (which also works fine)
- Lincity-NG (which has the same problem as the games mentioned previously (neverball, etc.) but the sound works...!?)
- SuperTux (which works, until you try and enable 'Open GL' from the Options menu, then it just quits)

Hopefully that might help with determining the problem...

---

### Post by eragon100 on 2008-08-30
Try assaultcube, that's also a 3d fps (so you can kill people :lolflag:), but it's only 20 mb or something, definitely less than 100 :wink:

---

### Post by BWPanda on 2008-08-30
I have this thing against non-repository, non-deb downloads...
I'm not against FPS's, in fact I own both UT2004 and CS:S, but will downloading one of your suggested games really help determine why certain games won't work for me? Or are you just trying to get me to kill people? ;)

---

### Post by gmxgeek on 2008-08-30
> **BWPanda said:**
> UPDATE: I installed a few more games;
- Gweled (which works fine)
- lbreackout 2 (which also works fine)
- Lincity-NG (which has the same problem as the games mentioned previously (neverball, etc.) but the sound works...!?)
- SuperTux (which works, until you try and enable 'Open GL' from the Options menu, then it just quits)

Hopefully that might help with determining the problem...

Sounds like you don't have opengl installed..

---

### Post by BWPanda on 2008-08-30
A quick search in Applications > Add/Remove.. for "OpenGL" shows that I have "ATI binary X.Org driver" installed (or at least ticked)...

EDIT: But it's still not working.

---

### Post by BWPanda on 2008-09-08
Still looking for an answer to this please...

---

### Post by BWPanda on 2008-09-18
Anyone?

---

### Post by Erpep on 2008-09-25
Same as you have screen flashes using any 3D program, my Lap is a Dell inspiron 1521, AMD dual, ATI Mob. Radeon X1250. I was tried to many things and Google's like, drivers, reinstallings, bios modifications, and so on, without no success.
 Could we help us, thank you

---

### Post by hessiess on 2008-09-25
ATI's OGL drivers have a history of being bad, the only thing i can suggest is manually upgrading to the newist drivers.

---

### Post by BWPanda on 2008-09-30
Thanks Hessiess!

I downloaded and installed the latest driver from ATI, and even though the [instructions]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8_or_8.9.29") looked scary, I worked my way through it and everything seems fine! My games all work now :D

Thanks!

---

