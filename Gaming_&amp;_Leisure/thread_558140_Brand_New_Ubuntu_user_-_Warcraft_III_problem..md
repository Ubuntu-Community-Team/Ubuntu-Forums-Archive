---
title: "Brand New Ubuntu user - Warcraft III problem."
date: 2007-09-23
forum: Gaming &amp; Leisure
---

### Post by tgeorge on 2007-09-23
Ive looked at several other Warcraft III posts with no success. I generally use forums to solve my problems from the other posts people have made. I have looked all weekend for a solution to the problem I am having and have had no success  whatsoever. I have tried running warcraft III a number of ways, including clicking the icon, typing wine warcraft -opengl, and wine warcraft-opengl -window.

Each time I get it to work, and each time I hear sound but see no video. I installed my video drivers with envy. Thinking it was a problem with those, i uninstalled them and reinstalled. No change. Same problem. I removed wine by using a process I found on here, and reinstalled it, running the winecfg file. Again, no success.

Has anyone else ever seen a blank screen and heard sound? I have tried several things over this weekend with no success, and will be thrilled to finally get this thing working. Naturally, I can not press control + alt + bksp, and must manually reboot the computer each time.

On a final note, I am (and was) running wine 0.9.45. I was able to install Itunes and bejeweled with wine and was able to run both of them. These, of course, are not programs that require a high level of graphics. 

I am running a 7900 GT/KO card, with an AMD athlon 64 3000+. 1GB of ram.

Lastly, I have also tried changing the screen resolution in nvidia settings, with no luck at all. Thanks very much for any help any of you can provide, and thanks a TON for the resource. 

-Tommy

---

### Post by Lord Illidan on 2007-09-23
Are you sure that you're using the nvidia drivers? Type glxinfo in a terminal and paste the output here, please.

Oh, and by the way, remove the movies, or rename the folder. Since wine doesn't play them, they could be messing up things. (You can always see them with mplayer afterwards).

EDIT : And btw, welcome to Ubuntu..

---

### Post by tgeorge on 2007-09-23
```
tdg@tdg--ubuntu-desktop:~$ glxinfo | grep -i openglOpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7900 GT/GTO/PCI/SSE2/3DNOW!
OpenGL version string: 2.1.1 NVIDIA 100.14.19
OpenGL extensions:
tdg@tdg--ubuntu-desktop:~$
```

```
tdg@tdg--ubuntu-desktop:~$ glxinfo | grep -i directdirect rendering: Yes
tdg@tdg--ubuntu-desktop:~$ 

```

Thanks for your fast response. That is the output you requested. The movie folder is already renamed. Oddly enough, when not renamed I can see the movies, but when it goes to the menu I hear the sound but see nothing!

---

### Post by Lord Illidan on 2007-09-23
Try this : [http://appdb.winehq.org/appview.php?iVersionId=1177](http://appdb.winehq.org/appview.php?iVersionId=1177)

---

### Post by Lord Illidan on 2007-09-23
Try running just wine war3.exe --opengl

---

### Post by tgeorge on 2007-09-23
Thank you VERY MUCH! It's bizare that I thought I had already done that. Now, it runs from the menu and also from wine war3.exe --opengl in the warcraft III directory. I cant believe how good it actually runs!

I have one more question on this issue. I know there must be a way to increase the resolution from 800x600. Do you mind helping me out with that too? Thanks again!

-Tommy

---

### Post by Lord Illidan on 2007-09-23
It's from the options. Select Video, and then select your desired resolution.

So did the war3 do the trick?

---

### Post by tgeorge on 2007-09-23
yes, the war 3 did the trick. From the options, i only have resolution: 800x600. Clicking on it appears to do nothing, and there are no arrows to change anything. Could this be a wine setting?

---

### Post by tgeorge on 2007-09-23
WOW! :lolflag: **Please** forgive me for being such a noob. I never went to the options menu choice, only options from within F10 in the game. I was on a time crunch though, as I went to my grandparents house for dinner. Ill use that as my excuse!

---

### Post by Lord Illidan on 2007-09-23
You're forgiven! :lolflag:

I love Warcraft 3 (stole my avatar and my name from there), and it plays very well in wine...although I don't play multiplayer.

---

### Post by tgeorge on 2007-09-25
Sorry to bring this post back from the dead but...

I have a problem with warcraft III. It is working almost perfectly now, but sometimes upon running or upon exiting, it crashes the xwindow system. (I think it's the xwindow system) I see garbled bits of my desktop upon launching WC3 and cant control + alt + bksp and have to cold boot. If I am leaving WC3, I sometimes see only a black screen. Sometimes ctrl + alt + bksp works, othertimes not. I have also had issues with the game crashing on battlenet. This has happened to me three times now, and unfortunately one time I was winning. 

Has anyone else had this problem?

---

### Post by Lord Illidan on 2007-09-25
Is it the same resolution as of the desktop?

Also, can you take a screenshot of the winecfg program under the graphics tab? Do it with Alt+Printscreen, and attach it here, like mine.

---

### Post by Unix_Wizard on 2007-09-25
I'm running warcraft3 with NVIDIA 100.14.19. and wine 0.9.45. Nobody can tell I'm running it in ubuntu because the fps is maxed, the quality is identical and the sounds are fast and clear. Maybe you should update you wine and you drivers.

---

### Post by tgeorge on 2007-09-25
Thanks for the reply unix_Wizard. I'm already running 0.9.45 and the 100 nvidia driver. Lord, here is the screenshot as requested. Looks like my screen resolution slider is set higher than yours... I'll try to adjust the dpi accordingly and see what difference it makes.

[ATTACH]44406[/ATTACH]

---

### Post by tgeorge on 2007-09-28
Still experiencing the same problems. I changed winecfg to allow the game to run in a window, and doing that allows it to run but I cant scroll. It also *still* freezes in the window, but at least I can close the window and do not need to restart the system. Any Ideas. I am going to try playing it tonight without running any other apps. I have run it in the past with Pidgin running.

---

