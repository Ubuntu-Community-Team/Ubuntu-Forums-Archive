---
title: "What's your glmark2 score?"
date: 2013-04-01
forum: Gaming &amp; Leisure
---

### Post by Ranko Kohime on 2013-04-01
Having only recently returned to the PC as a gaming platform, (after having left for the consoles many years ago), I'm debating whether to add a gaming desktop to my collection, so I'm interested in getting a comparison between my current laptop, and some of the newer equipment out there.

My laptop is a Lenovo E420, with the i3-2310M, HD3000 graphics.  It scored 854 under glmark2, in windowed mode with Cinnamon running.

I'd like to see everyone's scores, (please include what graphic card you have), and I'm most interested in the AMD APU's (for budgetary reasons).  I'd sure like to see what the GTX 680 & HD 7970 can do, if only to salivate at.  (I'm under the impression that these are the current top-end chipsets from each manufacturer)


If you've never used glmark2, try it.  It takes ~5 minutes on my system.
```
sudo apt-get install glmark2 && glmark2
```

[S]For better performance numbers, **SAVE YOUR WORK AS YOU WILL BE LOGGED OUT BY THIS**, switch to a TTY, (Ctrl+Alt+F1), then run the following:[/S]

```
[S]sudo service gdm stop || sudo service lightdm stop; xinit /usr/bin/glmark2 --fullscreen; sudo service gdm start || sudo service lightdm start[/S]
```

Please note: --fullscreen seems not to be available for the version of glmark2 in 12.04 repos.  If it gives you an error, omit that switch.  Also, some people have reported that either xinit or glmark2 defaults to vsync, which can cause your score to max out at 60, regardless of how powerful your hardware is.

[HR][/HR]The following is a list of all the scores posted in the thread.

*DE indicates whether a Desktop Environment is running or not.

**Scores this low generally indicate driver issues, resulting in software rendering.

[COLOR=#333333][FONT=arial]† These scores are likely to be wrong.[/FONT][/COLOR]

(I) Indicates an Integrated chipset.  All Intel are integrated.

[TABLE="class: grid, width: 500, align: center"]
[TR]
[TD]Manufacturer[/TD]
[TD]Model[/TD]
[TD]Resolution[/TD]
[TD="align: center"]DE?*[/TD]
[TD="align: center"]Score[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD="align: center"][/TD]
[TD="align: center"][/TD]
[/TR]
[TR]
[TD]AMD/ATI[/TD]
[TD]Radeon 9000[/TD]
[TD]800x600[/TD]
[TD="align: center"]No[/TD]
[TD="align: center"]1**[/TD]
[/TR]
[TR]
[TD]AMD/ATI[/TD]
[TD]Radeon HD 5750[/TD]
[TD]800x600[/TD]
[TD="align: center"]?[/TD]
[TD="align: center"]5,341[/TD]
[/TR]
[TR]
[TD]AMD/ATI[/TD]
[TD]Radeon HD 5770[/TD]
[TD]800x600[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]2,370[/TD]
[/TR]
[TR]
[TD]AMD/ATI[/TD]
[TD]Radeon HD 5870[/TD]
[TD]800x600[/TD]
[TD="align: center"]?[/TD]
[TD="align: center"]3,799[/TD]
[/TR]
[TR]
[TD]AMD/ATI[/TD]
[TD]Radeon HD 6250 (I)[/TD]
[TD]800x600[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]363[/TD]
[/TR]
[TR]
[TD]AMD/ATI[/TD]
[TD]Radeon HD 6250 (I)[/TD]
[TD]800x600[/TD]
[TD="align: center"]No[/TD]
[TD="align: center"]516[/TD]
[/TR]
[TR]
[TD]AMD/ATI[/TD]
[TD]Radeon HD 6250 (I)[/TD]
[TD]1280x720[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]231[/TD]
[/TR]
[TR]
[TD]AMD/ATI[/TD]
[TD]Radeon HD 6250 (I)[/TD]
[TD]1280x720[/TD]
[TD="align: center"]No[/TD]
[TD="align: center"]310[/TD]
[/TR]
[TR]
[TD]AMD/ATI[/TD]
[TD]Radeon HD 6520G (I)[/TD]
[TD]800x600[/TD]
[TD="align: center"]?[/TD]
[TD="align: center"]819[/TD]
[/TR]
[TR]
[TD]AMD/ATI[/TD]
[TD]Radeon HD 6450[/TD]
[TD]1920x1080[/TD]
[TD="align: center"]?[/TD]
[TD="align: center"]868[/TD]
[/TR]
[TR]
[TD]AMD/ATI[/TD]
[TD]Radeon HD 7600M[/TD]
[TD]800x600[/TD]
[TD="align: center"]Yes?[/TD]
[TD="align: center"]1,613[/TD]
[/TR]
[TR]
[TD]AMD/ATI[/TD]
[TD]HD 7640G (A8-4500M APU)[/TD]
[TD]800x600[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]1,323[/TD]
[/TR]
[TR]
[TD]AMD/ATI[/TD]
[TD]Radeon HD 7700M[/TD]
[TD]800x600[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]1,024[/TD]
[/TR]
[TR]
[TD]AMD/ATI[/TD]
[TD]Radeon HD 7750[/TD]
[TD]1280x1024[/TD]
[TD="align: center"]?[/TD]
[TD="align: center"]3,986[/TD]
[/TR]
[TR]
[TD]AMD/ATI[/TD]
[TD]Radeon HD 7750[/TD]
[TD]1280x1024[/TD]
[TD="align: center"]?[/TD]
[TD="align: center"]2,291[/TD]
[/TR]
[TR]
[TD]AMD/ATI[/TD]
[TD]Radeon HD 7850[/TD]
[TD]800x600[/TD]
[TD="align: center"]No[/TD]
[TD="align: center"]7,985[/TD]
[/TR]
[TR]
[TD]AMD/ATI[/TD]
[TD]Radeon HD 7850[/TD]
[TD]1920x1080[/TD]
[TD="align: center"]No[/TD]
[TD="align: center"]5,119[/TD]
[/TR]
[TR]
[TD]AMD/ATI[/TD]
[TD]Radeon HD 7970[/TD]
[TD]1440x900[/TD]
[TD="align: center"]No[/TD]
[TD="align: center"]8,784[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD="align: center"][/TD]
[TD="align: center"][/TD]
[/TR]
[TR]
[TD]Intel[/TD]
[TD]GM45[/TD]
[TD]800x600[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]192[/TD]
[/TR]
[TR]
[TD]Intel[/TD]
[TD]GM45[/TD]
[TD]800x600[/TD]
[TD="align: center"]Yes?[/TD]
[TD="align: center"]194[/TD]
[/TR]
[TR]
[TD]Intel[/TD]
[TD]GM45[/TD]
[TD]?[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]144[/TD]
[/TR]
[TR]
[TD]Intel[/TD]
[TD]GM45[/TD]
[TD]1366x768[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]154[/TD]
[/TR]
[TR]
[TD]Intel[/TD]
[TD]GM45[/TD]
[TD]800x600?[/TD]
[TD="align: center"]Yes?[/TD]
[TD="align: center"]355[/TD]
[/TR]
[TR]
[TD]Intel[/TD]
[TD]945GM[/TD]
[TD]800x600[/TD]
[TD="align: center"]?[/TD]
[TD="align: center"]36[/TD]
[/TR]
[TR]
[TD]Intel[/TD]
[TD]945GME[/TD]
[TD]800x600?[/TD]
[TD="align: center"]Yes?[/TD]
[TD="align: center"]29[/TD]
[/TR]
[TR]
[TD]Intel[/TD]
[TD]i3 (Unknown)[/TD]
[TD]800x600?[/TD]
[TD="align: center"]Yes?[/TD]
[TD="align: center"]478[/TD]
[/TR]
[TR]
[TD]Intel[/TD]
[TD]i3-2310M (HD3000)  (Unity 12.10?)[/TD]
[TD]800x600[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]854[/TD]
[/TR]
[TR]
[TD]Intel[/TD]
[TD]i3-2310M (HD3000)  (KDE LM 15)[/TD]
[TD]800x600[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]1,175[/TD]
[/TR]
[TR]
[TD]Intel[/TD]
[TD]? (HD3000)[/TD]
[TD]800x600?[/TD]
[TD="align: center"]Yes?[/TD]
[TD="align: center"]960[/TD]
[/TR]
[TR]
[TD]Intel[/TD]
[TD]? (HD3000)[/TD]
[TD]800x600[/TD]
[TD="align: center"]No[/TD]
[TD="align: center"]409[/TD]
[/TR]
[TR]
[TD]Intel[/TD]
[TD]? (HD4000)[/TD]
[TD]800x600?[/TD]
[TD="align: center"]Yes?[/TD]
[TD="align: center"]1,467[/TD]
[/TR]
[TR]
[TD]Intel[/TD]
[TD]Celeron M 353[/TD]
[TD]800x600[/TD]
[TD="align: center"]No[/TD]
[TD="align: center"]18[/TD]
[/TR]
[TR]
[TD]Intel[/TD]
[TD]i5-2500K (HD3000)[/TD]
[TD]800x600[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]1,269[/TD]
[/TR]
[TR]
[TD]Intel[/TD]
[TD]i7-3610QM (HD4000)[/TD]
[TD]800x600[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]1,519[/TD]
[/TR]
[TR]
[TD]Intel[/TD]
[TD]i7-4750HQ  (HD5200)[/TD]
[TD]800x600[/TD]
[TD="align: center"]?[/TD]
[TD="align: center"]2,945[/TD]
[/TR]
[TR]
[TD]Intel[/TD]
[TD]i7-4750HQ  (HD5200)[/TD]
[TD]1920x1080[/TD]
[TD="align: center"]?[/TD]
[TD="align: center"]947[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD="align: center"][/TD]
[TD="align: center"][/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GeForce 6150SE nForce 430[/TD]
[TD]800x600[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]113[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GeForce 8400GS[/TD]
[TD]800x600[/TD]
[TD="align: center"]No[/TD]
[TD="align: center"]572[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GeForce 8400GS[/TD]
[TD]800x600[/TD]
[TD="align: center"]No[/TD]
[TD="align: center"]750[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GeForce 8400GS[/TD]
[TD]800x600[/TD]
[TD="align: center"]No[/TD]
[TD="align: center"]836[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]Geforce 9300M GS[/TD]
[TD]800x600[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]336[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]Geforce 9300M GS[/TD]
[TD]?[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]419[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]Geforce 9300M GS[/TD]
[TD]800x600[/TD]
[TD="align: center"]No[/TD]
[TD="align: center"]481[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GeForce 9600gt[/TD]
[TD]800x600[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]1,048[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GeForce 9600gt[/TD]
[TD]800x600[/TD]
[TD="align: center"]No[/TD]
[TD="align: center"]4,318[COLOR=#333333][FONT=arial]†[/FONT][/COLOR][/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GeForce GT 750M[/TD]
[TD]800x600[/TD]
[TD="align: center"]?[/TD]
[TD="align: center"]4,382[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]Geforce GT 750M[/TD]
[TD]1920x1080[/TD]
[TD="align: center"]?[/TD]
[TD="align: center"]2,210[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GTX 550 Ti (310.14)[/TD]
[TD]800x600[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]4,899[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GTX 550 Ti (310.14)[/TD]
[TD]1280x720[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]3,303[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GTX 550 Ti (310.14)[/TD]
[TD]1920x1080[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]1,816[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GTX 560 Ti (331.20)[/TD]
[TD]800x600[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]13,855[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GTX 560 Ti (331.20)[/TD]
[TD]1920x1080[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]3,297[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GTX 650[/TD]
[TD]800x600[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]9,043[COLOR=#333333][FONT=arial]†[/FONT][/COLOR][/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GTX 650 Ti[/TD]
[TD]?[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]2,675[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GTX 650 Ti[/TD]
[TD]?[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]2,620[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GTX 650 Ti Boost[/TD]
[TD]800x600[/TD]
[TD="align: center"]?[/TD]
[TD="align: center"]7,919[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GTX 650 Ti Boost[/TD]
[TD]2560x1440[/TD]
[TD="align: center"]?[/TD]
[TD="align: center"]2,570[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GTX 660M[/TD]
[TD]800x600[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]5,900[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GTX 680[/TD]
[TD]800x600[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]8,563[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GTX 680[/TD]
[TD]1920x1080[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]4,646[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GTX 760[/TD]
[TD]800x600[/TD]
[TD="align: center"]Yes[/TD]
[TD="align: center"]11,471[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GeForce GTX 780M[/TD]
[TD]800x600[/TD]
[TD="align: center"]No[/TD]
[TD="align: center"]8,352[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GeForce GTX 780M[/TD]
[TD]1920x1080[/TD]
[TD="align: center"]No[/TD]
[TD="align: center"]2,721[/TD]
[/TR]
[/TABLE]

---

### Post by cprofitt on 2013-04-01
Here are my scores:

[LIST]
[*]T500 - **355** (Intel GM45)
[*]W520 - **960** (Intel Sandy Bridge)
[*]T530 - **1467** (Intel Ivy Bridge)
[*]Self Built Desktop -  **2893** (GeForce 8800 GTX 320MB) - Yes, my six year old desktop blows away all the Intel cards.
[/LIST]

---

### Post by Ranko Kohime on 2013-04-02
That's not even funny.  :P

On the other hand, I just ran glmark2 on my normally headless (though it still has a video card) former desktop/now file server, which has an ATI Radeon 9000, just for giggles.  It scored 1.  :biggrin:

---

### Post by sanderj on 2013-04-02
My Samsung laptop (Intel CPU i3, Intel GPU) says:

> 
$ glmark2 
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) Ironlake Mobile 
    GL_VERSION:    2.1 Mesa 9.0.3
=======================================================

...

glmark2 Score: 478


---

### Post by ManamiVixen on 2013-04-02
Everybody, when you do the test, make sure there are no other programs that require 3D acceleration with the GPU running. Like say Compiz and Unity. If they are running, it wil skew the results. Be sure to use a non-composited desktop like LXDE or Gnome-Sesion-Fallback with no effects to get an accurate reading.

---

### Post by myromance123 on 2013-04-02
> I'd sure like to see what the GTX 680 & HD 7970 can do
I hope I can answer this, at least for the 680. I have an Asus GeForce GTX 680 2GB GDDR5, using Nvidia's 310.14 drivers in Ubuntu 12.10 64Bit [Desktop System].

I even did a video of the benchmarking if you'd like to see it :)
[https://www.youtube.com/watch?v=tb5AF_oetMs]("https://www.youtube.com/watch?v=tb5AF_oetMs")

Here's the summary of my test results:

Fullscreen score: **4646**
Windowed-mode score: **8563**

As you can see, in windowed-mode the results are almost **TWICE** the fullscreen results. This is with Unity and Compiz enabled in the background. Sorry it's not like Manami Vixen suggested, but I don't want to install different DE's as it usually causes me troubles later down the road.

Note that the fullscreen is at 1920x1080. I'm not sure what resolution the windowed-mode version is in (looks like 800x600 but I could be wrong). I just ran glmark2 for the windowed-mode one.

For fullscreen:
```
glmark2 --fullscreen
```

Hope this information is useful :)

---

### Post by Ranko Kohime on 2013-04-02
I didn't realize that it had a fullscreen mode.  For reference, my test was in windowed mode.  I also discovered that the window does indeed default to 800x600.

And I don't think it should be necessary to install a different DE.  I managed to run it with the Display Manager stopped, by the following (--fullscreen was an unrecognized option for glmark2 on my test unit, which is different from the Lenovo in my OP)

```
xinit /usr/bin/glmark2
```

I'll add that to my OP.

ETA: --fullscreen option apparently isn't available in the 12.04 version, which is 2011.09-0ubuntu1.

---

### Post by sanderj on 2013-04-02
On my Netbook with Ubuntu 11.10, the lmark2 score is ... 29 ... :o

I must say there are "i915_program_error: Exceeded max nr indirect texture lookups" errors, so that might have an impact on the score.


```
sander@netbook:~$ time glmark2 
=======================================================
    glmark2 2011.09
=======================================================
    OpenGL Information
    GL_VENDOR:     Tungsten Graphics, Inc
    GL_RENDERER:   Mesa DRI Intel(R) 945GME x86/MMX/SSE2
    GL_VERSION:    1.4 Mesa 7.11
=======================================================
<snip>
=======================================================
                                  glmark2 Score: 29 
=======================================================
```

---

### Post by myromance123 on 2013-04-03
At least for Ubuntu 12.10 you'll need to do this instead:
```
sudo service lightdm stop
```

**_With the Unity DE on and Compiz enabled, revised score below._**

With Unredirect Fullscreen Windows _disabled_:
Fullscreen Score: **4646**
Windowed-mode Score: **8563**

With Unredirect Fullscreen Windows _enabled_:
Fullscreen Score: **3536**
Windowed-mode Score: **8648**

**_With the Unity DE off and Compiz disabled._**
I tried running glmark2 in the TTY with lightdm disabled, and this is what I got:
```
failed. Results may be bounded above by refresh rate
glmark2 score: 60
```

I tried running glmark2 fullscreen as well in the TTY, but it's unable to. It returns the following error:
```
X Error of failed request: BadAtom (Invalid Atom parameter)
Xinit: connection to X server lost
```

Unless I'm missing something, it looks like glmark2 can't be run from the TTY without the DE at the moment in Ubuntu 12.10.

Sorry it's not what you're looking for, I did try to get it working. Tried multiple times.

---

### Post by Ranko Kohime on 2013-04-03
No problem, the scores with Unity running still give me a baseline to compare.  The GTX 680 is only about 10 times more powerful than my laptop, as opposed to the dozens that discriminators of integrated graphics make it sound like.  :)

And I had forgotten about lightdm, I haven't been using Unity since trying out Gnome 3 when 12.10 came out.  I'll add that to the OP, as well.

---

### Post by Ranko Kohime on 2013-04-03
> **sanderj said:**
> On my Netbook with Ubuntu 11.10, the lmark2 score is ... 29 ... :o
My EeePC 701SD didn't give any errors, but it did score 18.  :lolflag:

My server, (which was formerly my desktop), with a Radeon 9000, scored 1.  :popcorn:

---

### Post by oldrocker99 on 2013-04-03
Here's what I got, using MATE (Metacity) in the windowed mode:

=======================================================
    glmark2 2011.09
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 650 Ti/PCIe/SSE2
    GL_VERSION:    4.3.0 NVIDIA 313.26
=======================================================
[build] use-vbo=false:  FPS: 4369
[build] use-vbo=true:  FPS: 12634
[texture] texture-filter=nearest:  FPS: 11933
[texture] texture-filter=linear:  FPS: 10837
[texture] texture-filter=mipmap:  FPS: 13408
[shading] shading=gouraud:  FPS: 9778
[shading] shading=blinn-phong-inf:  FPS: 9819
[shading] shading=phong:  FPS: 9688
[bump] bump-render=high-poly:  FPS: 6769
[bump] bump-render=normals:  FPS: 12314
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;:  FPS: 7133
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;:  FPS: 4486
[pulsar] light=false:quads=5:texture=false:  FPS: 11188
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4:  FPS: 3140
[conditionals] fragment-steps=0:vertex-steps=0:  FPS: 9162
[conditionals] fragment-steps=5:vertex-steps=0:  FPS: 8391
[conditionals] fragment-steps=0:vertex-steps=5:  FPS: 9158
[function] fragment-complexity=low:fragment-steps=5:  FPS: 9066
[function] fragment-complexity=medium:fragment-steps=5:  FPS: 8726
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5:  FPS: 9061
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5:  FPS: 9020
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5:  FPS: 8866
=======================================================
                                  glmark2 Score: 9043 
=======================================================


Can't say I'm disappointed...

---

### Post by myromance123 on 2013-04-04
> **oldrocker99 said:**
> 
=======================================================
                                  glmark2 Score: 9043 
=======================================================
Wow, that scored better than my card. I wonder if it's because of Compiz or the Nvidia drivers more. My **8563** versus your **9043**... Lost a good 500 there [-o<

I tested it on my HP DV3500 laptop with Ubuntu 13.04 32Bit and an Nvidia 9300M GS using 313 drivers.

**_With DE and Compiz on:_**
Fullscreen mode **(1280x800)**:
```

=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce 9300M GS/PCIe/SSE2
    GL_VERSION:    3.3.0 NVIDIA 313.26
=======================================================
<snip>
=======================================================
                                  glmark2 Score: 419 
=======================================================
```

Windowed mode:
```
=======================================================
                                  glmark2 Score: 336 
=======================================================
```

**_With DE and Compiz off:_**
800x600 only, unable to do fullscreen:
```
<snip>
=======================================================
                                  glmark2 Score: 481 
=======================================================
```

My fullscreen resolution is 1280x800 for the HP DV3500.

EDIT: Ranko, why not summarize all the graphics scores here so far, and put them into your OP. That way anyone browsing this, could get a good idea of the information collected so far.
Maybe something like
GPU: [Manufacturer] [Model Number]
F-Score:
W-Score:
where F-Score is fullscreen, and W-Score is for windowed-mode. Just a simple summary idea :)

---

### Post by Ranko Kohime on 2013-04-05
> **myromance123 said:**
> Ranko, why not summarize all the graphics scores here so far, and put them into your OP. That way anyone browsing this, could get a good idea of the information collected so far.
Will do.

---

### Post by efflandt on 2013-04-07
Stopping lightdm and using xinit to run glmark2 does not yield useful results for me. Apparently xinit sync's to vblank or something by default. So using the default 800x600 ends up 60 FPS and -s 1920x1080 (since 12.04 does not have --fullscreen) ends up 59 FPS (although, individual tests are all 60 FPS) for computer in my sig.

When running regular Unity desktop in 64-bit 12.04 with GTX 550 Ti and nvidia 310.14 windowed:
default 800x600: 4899
1280x720: 3303
1920x1080: 1816 (extends slightly off right & bottom of screen due to Unity and top bar) 

Acer W500P tablet PC w/AMD C-50 1 GHz 2 core 2 GB, Radeon HD 6250 booted from SD w/common /home, 800x600 window:
64-bit Ubuntu (Unity) 12.04: 363
64-bit Lubuntu (LXDE) 12.04: 516
1280x720 window (on 1280x800 display): 231 Ubuntu vs. 310 Lubuntu

So I guess Unity and Compiz do slow things a bit, but not that I would notice on my desktop PC.

---

### Post by Hexxus on 2013-04-09
haha... after I get the drivers on my Alienware with a 660M on it I'll run and post. :P

---

### Post by myromance123 on 2013-04-10
> **Hexxus said:**
> haha... after I get the drivers on my Alienware with a 660M on it I'll run and post. :P

Wow! What Alienware system is it? One of the laptops? Dude, please do some videos showing your gaming system and maybe some games running in whatever Linux OS you're using. I'd really love to see it, if you don't mind that is :)

Btw, nicely done table Ranko. Very neat and professional looking!

---

### Post by Perfect Storm on 2013-04-10
> **Hexxus said:**
> haha... after I get the drivers on my Alienware with a 660M on it I'll run and post. :P

Perhaps one of these? [http://ubuntuforums.org/showthread.php?t=2133774](http://ubuntuforums.org/showthread.php?t=2133774)

---

### Post by myromance123 on 2013-04-10
> **Artificial Intelligence said:**
> Perhaps one of these? [http://ubuntuforums.org/showthread.php?t=2133774](http://ubuntuforums.org/showthread.php?t=2133774)

If it really is one of those new Ubuntu Alienware X51s, then I really can't wait to see! They may not have the best specs for price, but the small form factor and the low power requirement is really neat. I wonder if they include their own program for handling the lights, like they do with the Windows one.

---

### Post by Ranko Kohime on 2013-04-10
> **efflandt said:**
> Stopping lightdm and using xinit to run glmark2 does not yield useful results for me. Apparently xinit sync's to vblank or something by default. So using the default 800x600 ends up 60 FPS and -s 1920x1080 (since 12.04 does not have --fullscreen) ends up 59 FPS (although, individual tests are all 60 FPS) for computer in my sig.
Updated my OP to reflect this finding.  I entered your scores into my table, and I treated LXDE as a non-DE, as it should be within a few points of what xinit SHOULD achieve, were it to not be vsync'd.

---

### Post by roly33 on 2013-04-22
Here's my Score Ubuntu 13.04 running Unity

_Windowed_

glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Mobile Intel® GM45 Express Chipset 
    GL_VERSION:    2.1 Mesa 9.1.1
=======================================================
[build] use-vbo=false: FPS: 192 FrameTime: 5.208 ms
=======================================================
                                  glmark2 Score: 192 
=======================================================

_Fullscreen 1366x768_

 glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Mobile Intel® GM45 Express Chipset 
    GL_VERSION:    2.1 Mesa 9.1.1
=======================================================
[build] use-vbo=false: FPS: 154 FrameTime: 6.494 ms
=======================================================
                                  glmark2 Score: 154 
=======================================================


Roland

---

### Post by oldrocker99 on 2013-04-22
Updated, with a fullscreen score:

oldrocker99@oldrocker99-desktop ~ $ glmark2 --fullscreen
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 650 Ti/PCIe/SSE2
    GL_VERSION:    4.3.0 NVIDIA 313.30
=======================================================
[build] use-vbo=false: FPS: 3065 FrameTime: 0.326 ms
[build] use-vbo=true: FPS: 3984 FrameTime: 0.251 ms
[texture] texture-filter=nearest: FPS: 3367 FrameTime: 0.297 ms
[texture] texture-filter=linear: FPS: 3302 FrameTime: 0.303 ms
[texture] texture-filter=mipmap: FPS: 3322 FrameTime: 0.301 ms
[shading] shading=gouraud: FPS: 3417 FrameTime: 0.293 ms
[shading] shading=blinn-phong-inf: FPS: 3411 FrameTime: 0.293 ms
[shading] shading=phong: FPS: 3411 FrameTime: 0.293 ms
[bump] bump-render=high-poly: FPS: 3107 FrameTime: 0.322 ms
[bump] bump-render=normals: FPS: 3848 FrameTime: 0.260 ms
[bump] bump-render=height: FPS: 3807 FrameTime: 0.263 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 2118 FrameTime: 0.472 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 1407 FrameTime: 0.711 ms
[pulsar] light=false:quads=5:texture=false: FPS: 2532 FrameTime: 0.395 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 1077 FrameTime: 0.929 ms
[desktop] effect=shadow:windows=4: FPS: 1519 FrameTime: 0.658 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 624 FrameTime: 1.603 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 777 FrameTime: 1.287 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 733 FrameTime: 1.364 ms
[ideas] speed=duration: FPS: 2517 FrameTime: 0.397 ms
[jellyfish] <default>: FPS: 1508 FrameTime: 0.663 ms
[terrain] <default>: FPS: 228 FrameTime: 4.386 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 3480 FrameTime: 0.287 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 3085 FrameTime: 0.324 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 3480 FrameTime: 0.287 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 3479 FrameTime: 0.287 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 3283 FrameTime: 0.305 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 3483 FrameTime: 0.287 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 3483 FrameTime: 0.287 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 3397 FrameTime: 0.294 ms
=======================================================
                                  glmark2 Score: 2675 
=======================================================

I still don't have any complaints.

---

### Post by oldrocker99 on 2013-04-25
Hmmm...I may have a complaint.

Kubuntu 13.04, desktop effects disabled for full-screen windows:



oldrocker99@oldrocker99-Desktop:~$ glmark2 --fullscreen
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 650 Ti/PCIe/SSE2
    GL_VERSION:    4.3.0 NVIDIA 313.30
=======================================================
[build] use-vbo=false: FPS: 2932 FrameTime: 0.341 ms
[build] use-vbo=true: FPS: 4019 FrameTime: 0.249 ms
[texture] texture-filter=nearest: FPS: 3515 FrameTime: 0.284 ms
[texture] texture-filter=linear: FPS: 3489 FrameTime: 0.287 ms
[texture] texture-filter=mipmap: FPS: 3492 FrameTime: 0.286 ms
[shading] shading=gouraud: FPS: 3134 FrameTime: 0.319 ms
[shading] shading=blinn-phong-inf: FPS: 3137 FrameTime: 0.319 ms
[shading] shading=phong: FPS: 3134 FrameTime: 0.319 ms
[bump] bump-render=high-poly: FPS: 2864 FrameTime: 0.349 ms
[bump] bump-render=normals: FPS: 3503 FrameTime: 0.285 ms
[bump] bump-render=height: FPS: 3506 FrameTime: 0.285 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 2258 FrameTime: 0.443 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 1616 FrameTime: 0.619 ms
[pulsar] light=false:quads=5:texture=false: FPS: 2612 FrameTime: 0.383 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 1235 FrameTime: 0.810 ms
[desktop] effect=shadow:windows=4: FPS: 1747 FrameTime: 0.572 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 636 FrameTime: 1.572 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 768 FrameTime: 1.302 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 716 FrameTime: 1.397 ms
[ideas] speed=duration: FPS: 2598 FrameTime: 0.385 ms
[jellyfish] <default>: FPS: 1778 FrameTime: 0.562 ms
[terrain] <default>: FPS: 282 FrameTime: 3.546 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 3274 FrameTime: 0.305 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 3050 FrameTime: 0.328 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 3270 FrameTime: 0.306 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 3272 FrameTime: 0.306 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 3110 FrameTime: 0.322 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 3274 FrameTime: 0.305 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 3274 FrameTime: 0.305 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 3118 FrameTime: 0.321 ms
=======================================================
                                  glmark2 Score: 2620 
=======================================================

SLIGHTLY less than my previous post (2675), which used Mint 14 (12.10) and MATE.

Oh, well. Skyrim still runs nicely...

---

### Post by Ranko Kohime on 2013-04-25
KDE is heavy, to my understanding.

ETA: Table is updated.

---

### Post by ppjdee on 2013-04-26
My craptastic score lol Using Unity Ubuntu 13.04
=======================================================
    glmark2 2012.08 **_Windowed _**
=======================================================
    OpenGL Information
    GL_VENDOR:     X.Org
    GL_RENDERER:   Gallium 0.4 on AMD JUNIPER    edit: ATI Radeon HD 5770
    GL_VERSION:    3.0 Mesa 9.1.1
=======================================================
=======================================================
                                  glmark2 Score: 2370 
=======================================================

---

### Post by roly33 on 2013-04-28
After installing intel Drivers from Software Centre I've re done glmark and got a 2 point bump from my original in windowed mode, but lost 50 points in fullscreen mode

Windowed
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Mobile Intel® GM45 Express Chipset 
    GL_VERSION:    2.1 Mesa 9.1.1
=======================================================
[build] use-vbo=false: FPS: 192 FrameTime: 5.208 ms
[build] use-vbo=true: FPS: 196 FrameTime: 5.102 ms
=======================================================
                                  glmark2 Score: 194 
=======================================================

Fullscreen

=======================================================
roland@steelers:~$ glmark2 --fullscreen
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Mobile Intel® GM45 Express Chipset 
    GL_VERSION:    2.1 Mesa 9.1.1
=======================================================
[build] use-vbo=false: FPS: 145 FrameTime: 6.897 ms
[build] use-vbo=true: FPS: 144 FrameTime: 6.944 ms
=======================================================
                                  glmark2 Score: 144 
=======================================================

Roland

---

### Post by oldrocker99 on 2013-04-29
This is getting interesting:

This is on a Acer C7 Chromebook, running Chrubuntu 12.04, LXDE, windowed:

oldrocker99@ChrUbuntu:~$ glmark2
=======================================================
    glmark2 2011.09
=======================================================
    OpenGL Information
    GL_VENDOR:     Tungsten Graphics, Inc
    GL_RENDERER:   Mesa DRI Intel(R) Sandybridge Mobile 
    GL_VERSION:    3.0 Mesa 8.0.4
=======================================================
[build] use-vbo=false:  FPS: 554
[build] use-vbo=true:  FPS: 739
[texture] texture-filter=nearest:  FPS: 708
[texture] texture-filter=linear:  FPS: 703
[texture] texture-filter=mipmap:  FPS: 792
[shading] shading=gouraud:  FPS: 422
[shading] shading=blinn-phong-inf:  FPS: 397
[shading] shading=phong:  FPS: 346
[bump] bump-render=high-poly:  FPS: 304
[bump] bump-render=normals:  FPS: 428
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;:  FPS: 227
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;:  FPS: 124
[pulsar] light=false:quads=5:texture=false:  FPS: 361
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4:  FPS: 113
[conditionals] fragment-steps=0:vertex-steps=0:  FPS: 353
[conditionals] fragment-steps=5:vertex-steps=0:  FPS: 352
[conditionals] fragment-steps=0:vertex-steps=5:  FPS: 352
[function] fragment-complexity=low:fragment-steps=5:  FPS: 353
[function] fragment-complexity=medium:fragment-steps=5:  FPS: 352
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5:  FPS: 352
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5:  FPS: 352
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5:  FPS: 321
=======================================================
                                  glmark2 Score: 409 
======================================================

I will say that 0AD, Warzone, and Torchlight are all playable on this mighty mite.

---

### Post by BashfulSimian on 2013-05-27
Hey all. Running windowed, 12.04

=======================================================
    glmark2 2011.09
=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   AMD Radeon HD 7600M Series
    GL_VERSION:    4.2.12172 Compatibility Profile Context 9.00.11
=======================================================
...
=======================================================
                                  glmark2 Score: 1613 
=======================================================

---

### Post by playing_with_matches on 2013-06-18
Figure I share my results: 13.04 windowed, using cinnamon 

    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce 6150SE nForce 430/integrated/SSE2/3DNOW!
    GL_VERSION:    2.1.2 NVIDIA 304.88

SCORE: 113

---

### Post by seth51jan on 2013-06-28
13.04 windowed, running unity/compiz. I'm going to run this again after a driver update.

AMD Phenom II x4 945 ~3050 MHz
2x4gb DDR3-1333 7-7-7-21 OC'ed to 1366Mhz
PNY NVIDIA GeForce 9600gt 512mb GDDR3 core clock 650Mhz (motherboard only supports PCI-E v1.0) - It's 5 years old and still kicking!
MSI GF615M-P33 motherboard..nForce 430 chipset fml
WD Caviar Blue 1TB SATA HDD 64mb cache
Hitachi 250GB SATA HDD 16mb cache (contains win7)

```

=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce 9600 GT/PCIe/SSE2
    GL_VERSION:    3.3.0 NVIDIA 304.88
=======================================================
[build] use-vbo=false: FPS: 1220 FrameTime: 0.820 ms
[build] use-vbo=true: FPS: 1267 FrameTime: 0.789 ms
[texture] texture-filter=nearest: FPS: 1296 FrameTime: 0.772 ms
[texture] texture-filter=linear: FPS: 1358 FrameTime: 0.736 ms
[texture] texture-filter=mipmap: FPS: 1273 FrameTime: 0.786 ms
[shading] shading=gouraud: FPS: 1105 FrameTime: 0.905 ms
[shading] shading=blinn-phong-inf: FPS: 1193 FrameTime: 0.838 ms
[shading] shading=phong: FPS: 1088 FrameTime: 0.919 ms
[bump] bump-render=high-poly: FPS: 820 FrameTime: 1.220 ms
[bump] bump-render=normals: FPS: 1326 FrameTime: 0.754 ms
[bump] bump-render=height: FPS: 1406 FrameTime: 0.711 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 1111 FrameTime: 0.900 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 851 FrameTime: 1.175 ms
[pulsar] light=false:quads=5:texture=false: FPS: 1303 FrameTime: 0.767 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 608 FrameTime: 1.645 ms
[desktop] effect=shadow:windows=4: FPS: 738 FrameTime: 1.355 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 497 FrameTime: 2.012 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 642 FrameTime: 1.558 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 661 FrameTime: 1.513 ms
[ideas] speed=duration: FPS: 1025 FrameTime: 0.976 ms
[jellyfish] <default>: FPS: 760 FrameTime: 1.316 ms
[terrain] <default>: FPS: 156 FrameTime: 6.410 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 1240 FrameTime: 0.806 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 1087 FrameTime: 0.920 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 1306 FrameTime: 0.766 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 1282 FrameTime: 0.780 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 1115 FrameTime: 0.897 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 1230 FrameTime: 0.813 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 1222 FrameTime: 0.818 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 1267 FrameTime: 0.789 ms
=======================================================
                                  glmark2 Score: 1048 
=======================================================

```

Updated to NVIDIA 313.30 drivers, Gnome Fallback (no effects, windowed). HUGE difference, in fact my score quadrupled from before.

```

=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce 9600 GT/PCIe/SSE2
    GL_VERSION:    3.3.0 NVIDIA 313.30
=======================================================
[build] use-vbo=false: FPS: 4053 FrameTime: 0.247 ms
[build] use-vbo=true: FPS: 6901 FrameTime: 0.145 ms
[texture] texture-filter=nearest: FPS: 8323 FrameTime: 0.120 ms
[texture] texture-filter=linear: FPS: 5941 FrameTime: 0.168 ms
[texture] texture-filter=mipmap: FPS: 6434 FrameTime: 0.155 ms
[shading] shading=gouraud: FPS: 4284 FrameTime: 0.233 ms
[shading] shading=blinn-phong-inf: FPS: 4288 FrameTime: 0.233 ms
[shading] shading=phong: FPS: 3935 FrameTime: 0.254 ms
[bump] bump-render=high-poly: FPS: 1871 FrameTime: 0.534 ms
[bump] bump-render=normals: FPS: 7176 FrameTime: 0.139 ms
[bump] bump-render=height: FPS: 6837 FrameTime: 0.146 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 4182 FrameTime: 0.239 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 2018 FrameTime: 0.496 ms
[pulsar] light=false:quads=5:texture=false: FPS: 5635 FrameTime: 0.177 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 1531 FrameTime: 0.653 ms
[desktop] effect=shadow:windows=4: FPS: 2707 FrameTime: 0.369 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 611 FrameTime: 1.637 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 753 FrameTime: 1.328 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 751 FrameTime: 1.332 ms
[ideas] speed=duration: FPS: 4004 FrameTime: 0.250 ms
[jellyfish] <default>: FPS: 3199 FrameTime: 0.313 ms
[terrain] <default>: FPS: 198 FrameTime: 5.051 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 6366 FrameTime: 0.157 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 3940 FrameTime: 0.254 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 6367 FrameTime: 0.157 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 6032 FrameTime: 0.166 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 4292 FrameTime: 0.233 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 5995 FrameTime: 0.167 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 5992 FrameTime: 0.167 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 4931 FrameTime: 0.203 ms
=======================================================
                                  glmark2 Score: 4318 
=======================================================


```

---

### Post by Ranko Kohime on 2013-07-20
Table updated.

Soon, I will be adding my own numbers from the HD 7850 I have sitting here, collecting dust.  (motherboard and processor have been ordered, but not here yet)

---

### Post by sinantalebi on 2013-07-31
A8-4500M
HD 7640G
with Desktop Environment(using 8 tabs in firefox)
glmark2 Score: 1323
Desktop Resolution: 1920x1080 but i guess the window was on 800x600, interestingly my 7730m got a lower score then my 7640G. 

```

=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   AMD Radeon HD 7640G
    GL_VERSION:    4.2.12337 Compatibility Profile Context 13.101
=======================================================
[build] use-vbo=false: FPS: 1330 FrameTime: 0.752 ms
[build] use-vbo=true: FPS: 1867 FrameTime: 0.536 ms
[texture] texture-filter=nearest: FPS: 1650 FrameTime: 0.606 ms
[texture] texture-filter=linear: FPS: 1585 FrameTime: 0.631 ms
[texture] texture-filter=mipmap: FPS: 1684 FrameTime: 0.594 ms
[shading] shading=gouraud: FPS: 1618 FrameTime: 0.618 ms
[shading] shading=blinn-phong-inf: FPS: 1641 FrameTime: 0.609 ms
[shading] shading=phong: FPS: 1578 FrameTime: 0.634 ms
[bump] bump-render=high-poly: FPS: 1360 FrameTime: 0.735 ms
[bump] bump-render=normals: FPS: 1822 FrameTime: 0.549 ms
[bump] bump-render=height: FPS: 1829 FrameTime: 0.547 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 1333 FrameTime: 0.750 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 840 FrameTime: 1.190 ms
[pulsar] light=false:quads=5:texture=false: FPS: 1470 FrameTime: 0.680 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 631 FrameTime: 1.585 ms
[desktop] effect=shadow:windows=4: FPS: 762 FrameTime: 1.312 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 313 FrameTime: 3.195 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 431 FrameTime: 2.320 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 381 FrameTime: 2.625 ms
[ideas] speed=duration: FPS: 1224 FrameTime: 0.817 ms
[jellyfish] <default>: FPS: 986 FrameTime: 1.014 ms
[terrain] <default>: FPS: 135 FrameTime: 7.407 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 1749 FrameTime: 0.572 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 1626 FrameTime: 0.615 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 1745 FrameTime: 0.573 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 1714 FrameTime: 0.583 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 1486 FrameTime: 0.673 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 1697 FrameTime: 0.589 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 1723 FrameTime: 0.580 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 1480 FrameTime: 0.676 ms


```

```

=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   AMD Radeon HD 7700M Series 
    GL_VERSION:    4.3.12438 Compatibility Profile Context 13.20.5
=======================================================
[build] use-vbo=false: FPS: 869 FrameTime: 1.151 ms
[build] use-vbo=true: FPS: 1570 FrameTime: 0.637 ms
[texture] texture-filter=nearest: FPS: 1249 FrameTime: 0.801 ms
[texture] texture-filter=linear: FPS: 1241 FrameTime: 0.806 ms
[texture] texture-filter=mipmap: FPS: 1280 FrameTime: 0.781 ms
[shading] shading=gouraud: FPS: 1249 FrameTime: 0.801 ms
[shading] shading=blinn-phong-inf: FPS: 1251 FrameTime: 0.799 ms
[shading] shading=phong: FPS: 1242 FrameTime: 0.805 ms
[bump] bump-render=high-poly: FPS: 931 FrameTime: 1.074 ms
[bump] bump-render=normals: FPS: 1369 FrameTime: 0.730 ms
[bump] bump-render=height: FPS: 1358 FrameTime: 0.736 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 1067 FrameTime: 0.937 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 755 FrameTime: 1.325 ms
[pulsar] light=false:quads=5:texture=false: FPS: 1129 FrameTime: 0.886 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 483 FrameTime: 2.070 ms
[desktop] effect=shadow:windows=4: FPS: 512 FrameTime: 1.953 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 192 FrameTime: 5.208 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 393 FrameTime: 2.545 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 271 FrameTime: 3.690 ms
[ideas] speed=duration: FPS: 730 FrameTime: 1.370 ms
[jellyfish] <default>: FPS: 907 FrameTime: 1.103 ms
[terrain] <default>: FPS: 135 FrameTime: 7.407 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 1337 FrameTime: 0.748 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 1324 FrameTime: 0.755 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 1325 FrameTime: 0.755 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 1338 FrameTime: 0.747 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 1285 FrameTime: 0.778 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 1328 FrameTime: 0.753 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 1295 FrameTime: 0.772 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 1327 FrameTime: 0.754 ms
=======================================================
                                  glmark2 Score: 1024 
=======================================================

```

---

### Post by Sazhen86 on 2013-07-31
Intel(R) Core(TM) i7-3610QM CPU @ 2.30GHz (Ivy Bridge) HD4000

Running in a window under unity

```
=======================================================
    glmark2 2011.09
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) Ivybridge Mobile 
    GL_VERSION:    3.0 Mesa 9.0.3
=======================================================
=======================================================
                                  glmark2 Score: 1519 
=======================================================


```

---

### Post by skyborg007 on 2013-08-04
Radeon HD 7970 Fullscreen 1440x900  from XFCE4
score: 8784

---

### Post by Ranko Kohime on 2013-08-04
Table updated, and now with my own rather impressive score from my HD 7850.  :D

Also, something I noticed was that my first test came up in the mid-3000 range (window).  I re-installed the catalyst driver due to a kernel update, and came up with these numbers today.

800x600: 7985
1920x1080: 5119

---

### Post by java-lang-runtime on 2013-08-04
Linux 3.8.0-27-generic #40-Ubuntu SMP Tue Jul 9 00:19:35 UTC 2013 i686 i686 i686 GNU/Linux

Desktop was 1920x1080, 

Windowed mode:

```
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GT 750M/PCIe/SSE2
    GL_VERSION:    4.3.0 NVIDIA 319.32
=======================================================

=======================================================
                                  glmark2 Score: 4832 
=======================================================
```

Fullscreen:

```
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GT 750M/PCIe/SSE2
    GL_VERSION:    4.3.0 NVIDIA 319.32
=======================================================

=======================================================
                                  glmark2 Score: 2210 
=======================================================

```

---

### Post by R33D3M33R on 2013-08-05
Kubuntu 13.04, KDE 4.10.5, HD 7750. Desktop resolution is 1280x1024, but I seriously doubt the benchmark ran at this resolution, more likely 800x600. Also, the table values for GTX 650 (9000+) and GeForce 9600gt (4000+) are unrealistic. 

```
$ glmark2 --fullscreen
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   AMD Radeon HD 7700 Series 
    GL_VERSION:    4.2.12173 Compatibility Profile Context 9.01.8
=======================================================
[build] use-vbo=false: FPS: 2445 FrameTime: 0.409 ms
[build] use-vbo=true: FPS: 6990 FrameTime: 0.143 ms
[texture] texture-filter=nearest: FPS: 5622 FrameTime: 0.178 ms
[texture] texture-filter=linear: FPS: 5616 FrameTime: 0.178 ms
[texture] texture-filter=mipmap: FPS: 5748 FrameTime: 0.174 ms
[shading] shading=gouraud: FPS: 5583 FrameTime: 0.179 ms
[shading] shading=blinn-phong-inf: FPS: 5589 FrameTime: 0.179 ms
[shading] shading=phong: FPS: 4871 FrameTime: 0.205 ms
[bump] bump-render=high-poly: FPS: 3593 FrameTime: 0.278 ms
[bump] bump-render=normals: FPS: 6698 FrameTime: 0.149 ms
[bump] bump-render=height: FPS: 6342 FrameTime: 0.158 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 2626 FrameTime: 0.381 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 1146 FrameTime: 0.873 ms
[pulsar] light=false:quads=5:texture=false: FPS: 4049 FrameTime: 0.247 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 1034 FrameTime: 0.967 ms
[desktop] effect=shadow:windows=4: FPS: 1711 FrameTime: 0.584 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 414 FrameTime: 2.415 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1226 FrameTime: 0.816 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 464 FrameTime: 2.155 ms
[ideas] speed=duration: FPS: 3544 FrameTime: 0.282 ms
[jellyfish] <default>: FPS: 2170 FrameTime: 0.461 ms
[terrain] <default>: FPS: 226 FrameTime: 4.425 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 5577 FrameTime: 0.179 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 4555 FrameTime: 0.220 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 5498 FrameTime: 0.182 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 5560 FrameTime: 0.180 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 4119 FrameTime: 0.243 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 5523 FrameTime: 0.181 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 5535 FrameTime: 0.181 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 5507 FrameTime: 0.182 ms
=======================================================
                                  glmark2 Score: 3986 
=======================================================
```

---

### Post by oldrocker99 on 2013-08-05
Chrubuntu 13.04, Lubuntu-desktop, fullscreen.

Glmark2 score: 201.

---

### Post by Ranko Kohime on 2013-08-07
Table updated, now with some commas to make the numbers a little more human readable, plus notation on two scores that do seem out of place.


@R33D3M33R: I recorded your number at your native desktop resolution, as it seems to be inline with the power of your card.  I suspect a window'd test would show a significantly higher score.

@oldrocker99: What's your hardware?   :P

---

### Post by oldrocker99 on 2013-08-07
My desktop: AMD Phenom II 965, not overclocked
                  nVidia 650Ti (2GB vRAM) (using nVidia proprietary drivers)
                  16GB 1333 RAM

My Acer C7 Chromebook: Intel 847 Celeron, Sandy Bridge graphics (1st generation), OSS drivers (the only drivers available for Linux for Intel intergrated graphics are OSS).
                2GB RAM (sooner or later, I'll add another 8GB)
                Larger battery for ~5 hours using Linux.

The Chromebook is better than a tablet, as far as I'm concerned. The games are certainly better. Dominions 4 (the new version of My Favorite Game) is bering developed in Linux, then ported to other OSes, for example. No Android or iOS versioon coming out. Calibre makes it a nifty ebook reader, as well. And it has a real keyboard. I use Lubuntu-desktop for the maximum speed on this surprisigly powerful little slab. 300GB storage is also pretty nice. I've barely turned on my Nexus 7 since I put Ubuntu on a $200 Chromebook.

The [http://chromeos-cr48.blogspot.com/2013/05/chrubuntu-one-script-to-rule-them-all_31.html](http://chromeos-cr48.blogspot.com/2013/05/chrubuntu-one-script-to-rule-them-all_31.html) page has all the information you need to install whichever distro (12.04, 12.10, 13.04, and, for the adventurous, 13.10) and whichever flavor (ubuntu-desktop, lubuntu-desktop, kubuntu-desktop,xubuntu-desktop) you want. It's one hell of a cool script, run twice; once to prepare the drive to install GNU/Linux, then run again to directly download the proper **updated** packages for that desktop. When you reboot, you have everything in its latest versions. Pretty cool.

---

### Post by R33D3M33R on 2013-08-07
> **Ranko Kohime said:**
> Table updated, now with some commas to make the numbers a little more human readable, plus notation on two scores that do seem out of place.


@R33D3M33R: I recorded your number at your native desktop resolution, as it seems to be inline with the power of your card.  I suspect a window'd test would show a significantly higher score.

@oldrocker99: What's your hardware?   :P

So I did a Windowed test:

```
 glmark2 --size 1280x1024                                                                                                                                   
=======================================================                                                                                                                             
    glmark2 2012.08                                                                                                                                                                 
=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   AMD Radeon HD 7700 Series 
    GL_VERSION:    4.2.12173 Compatibility Profile Context 9.01.8
=======================================================
[build] use-vbo=false: FPS: 1693 FrameTime: 0.591 ms
[build] use-vbo=true: FPS: 3355 FrameTime: 0.298 ms
[texture] texture-filter=nearest: FPS: 3003 FrameTime: 0.333 ms
[texture] texture-filter=linear: FPS: 3001 FrameTime: 0.333 ms
[texture] texture-filter=mipmap: FPS: 3042 FrameTime: 0.329 ms
[shading] shading=gouraud: FPS: 2998 FrameTime: 0.334 ms
[shading] shading=blinn-phong-inf: FPS: 2998 FrameTime: 0.334 ms
[shading] shading=phong: FPS: 2777 FrameTime: 0.360 ms
[bump] bump-render=high-poly: FPS: 2311 FrameTime: 0.433 ms
[bump] bump-render=normals: FPS: 3294 FrameTime: 0.304 ms
[bump] bump-render=height: FPS: 3198 FrameTime: 0.313 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 1960 FrameTime: 0.510 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 1000 FrameTime: 1.000 ms
[pulsar] light=false:quads=5:texture=false: FPS: 2398 FrameTime: 0.417 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 893 FrameTime: 1.120 ms
[desktop] effect=shadow:windows=4: FPS: 1386 FrameTime: 0.722 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 399 FrameTime: 2.506 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1148 FrameTime: 0.871 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 455 FrameTime: 2.198 ms
[ideas] speed=duration: FPS: 2487 FrameTime: 0.402 ms
[jellyfish] <default>: FPS: 1677 FrameTime: 0.596 ms
[terrain] <default>: FPS: 219 FrameTime: 4.566 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 2983 FrameTime: 0.335 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 2673 FrameTime: 0.374 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 2970 FrameTime: 0.337 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 2983 FrameTime: 0.335 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 2515 FrameTime: 0.398 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 2978 FrameTime: 0.336 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 2973 FrameTime: 0.336 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 2974 FrameTime: 0.336 ms
=======================================================
                                  glmark2 Score: 2291 
=======================================================


```

This means that the previous benchmark was 100% 800x600. The size parameter seems to have no effect in fullscreen and it always defaults to 800x600 instead of desktop native resolution. Pretty weird. Maybe you should write this in the first post. Also, DE was running both times (KDE).

---

### Post by suseno on 2013-08-11
==================================
    glmark2 2012.08
==================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce 8600 GT/PCIe/SSE2
    GL_VERSION:    3.3.0 NVIDIA 325.15
==================================
                                  glmark2 Score: **1269** 
==================================

CPU: Intel® Core™ i5-2500K
Memory: 7.7 GiB PC 12800 dual channel enabled
Ditros: Ubuntu 13.04 64 bit Raring Ringtail
Kernel version: 3.8.0-27-generic
Desktop Enviroment: Unity 7.0.0
Full Screen: No (Windowed)
Resolution: 800 x 600

---

### Post by amirgeva on 2013-09-20
glmark2 2012.08
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 650 Ti BOOST/PCIe/SSE2
    GL_VERSION:    4.3.0 NVIDIA 319.49



Windowed  (default) : 7919
Full screen (2560x1440):  2570

---

### Post by daniel88 on 2013-09-29
Here's mine. 
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   AMD Radeon HD 6520G
    GL_VERSION:    4.2.12002 Compatibility Profile Context 9.01
=======================================================
[build] use-vbo=false: FPS: 1112 FrameTime: 0.899 ms
[build] use-vbo=true: FPS: 1348 FrameTime: 0.742 ms
[texture] texture-filter=nearest: FPS: 1029 FrameTime: 0.972 ms
[texture] texture-filter=linear: FPS: 1018 FrameTime: 0.982 ms
[texture] texture-filter=mipmap: FPS: 1083 FrameTime: 0.923 ms
[shading] shading=gouraud: FPS: 1009 FrameTime: 0.991 ms
[shading] shading=blinn-phong-inf: FPS: 1010 FrameTime: 0.990 ms
[shading] shading=phong: FPS: 1009 FrameTime: 0.991 ms
[bump] bump-render=high-poly: FPS: 838 FrameTime: 1.193 ms
[bump] bump-render=normals: FPS: 1313 FrameTime: 0.762 ms
[bump] bump-render=height: FPS: 1302 FrameTime: 0.768 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 651 FrameTime: 1.536 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 321 FrameTime: 3.115 ms
[pulsar] light=false:quads=5:texture=false: FPS: 787 FrameTime: 1.271 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 198 FrameTime: 5.051 ms
[desktop] effect=shadow:windows=4: FPS: 237 FrameTime: 4.219 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 139 FrameTime: 7.194 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 325 FrameTime: 3.077 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 169 FrameTime: 5.917 ms
[ideas] speed=duration: FPS: 841 FrameTime: 1.189 ms
[jellyfish] <default>: FPS: 334 FrameTime: 2.994 ms
[terrain] <default>: FPS: 50 FrameTime: 20.000 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 1088 FrameTime: 0.919 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 1088 FrameTime: 0.919 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 1088 FrameTime: 0.919 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 1092 FrameTime: 0.916 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 948 FrameTime: 1.055 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 1089 FrameTime: 0.918 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 1088 FrameTime: 0.919 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 980 FrameTime: 1.020 ms
=======================================================
                                  glmark2 Score: 819 
=======================================================

---

### Post by Twidi on 2013-10-15
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) Haswell Mobile 
    GL_VERSION:    3.0 Mesa 9.2.1
=======================================================

Windowed (800x600) : 2945 
Fullscreen (1920x1080) : 947


(Intel Iris Pro HD 5200 Graphics, 3.11.0-12-generic, x86_64, Intel i7-4750HQ 4x2 cores, 16Go RAM)

---

### Post by ruddi on 2013-10-16
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 760/PCIe/SSE2
    GL_VERSION:    4.4.0 NVIDIA 331.13
=======================================================
=================
  glmark2 Score: 11471 
=================

Windowed with compiz unity in the background 
Ubuntu 13.04

---

### Post by dannyboy79 on 2013-10-17
Don't laugh at me, lol. I've been dieing to upgrade but funds are just too damn tight
```
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce 8400GS/PCIe/SSE2
    GL_VERSION:    3.3.0 NVIDIA 319.32
=======================================================

                                  glmark2 Score: 572 
```

Xubuntu 12.04.3, windowed mode
Specs: 
E4300
AsRock 775Dual-VSTA
GeForce 8400GS
2GB DDRII

I wonder if 319.60 would help me at all? Where in the world did Rubbi get 331.13? I just checked Nvidia site and 313.60 is the latest I could find.

---

### Post by ruddi on 2013-10-17
It is beta drivers but they work great.
[http://www.nvidia.com/download/driverResults.aspx/68326/en-us](http://www.nvidia.com/download/driverResults.aspx/68326/en-us)

Got them with tha xorg-edgers ppa
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by dannyboy79 on 2013-10-26
i ran it again after OC'ing my E4300 to 2.4Ghz, here's the new results. I may even look into NVControl to OC my GPU. I sure wish I could just afford a new build but I can't and I've been stuck with this one for so many years. LOL
```
=======================================================
    glmark2 2011.09
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce 8400GS/PCIe/SSE2
    GL_VERSION:    3.3.0 NVIDIA 319.60
=======================================================
[build] use-vbo=false:  FPS: 676
[build] use-vbo=true:  FPS: 1124
[texture] texture-filter=nearest:  FPS: 1174
[texture] texture-filter=linear:  FPS: 1163
[texture] texture-filter=mipmap:  FPS: 1421
[shading] shading=gouraud:  FPS: 900
[shading] shading=blinn-phong-inf:  FPS: 755
[shading] shading=phong:  FPS: 549
[bump] bump-render=high-poly:  FPS: 421
[bump] bump-render=normals:  FPS: 965
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;:  FPS: 482
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;:  FPS: 208
[pulsar] light=false:quads=5:texture=false:  FPS: 813
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4:  FPS: 223
[conditionals] fragment-steps=0:vertex-steps=0:  FPS: 938
[conditionals] fragment-steps=5:vertex-steps=0:  FPS: 507
[conditionals] fragment-steps=0:vertex-steps=5:  FPS: 926
[function] fragment-complexity=low:fragment-steps=5:  FPS: 755
[function] fragment-complexity=medium:fragment-steps=5:  FPS: 463
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5:  FPS: 733
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5:  FPS: 735
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5:  FPS: 571
=======================================================
                                  glmark2 Score: 750 
=======================================================
```

---

### Post by dannyboy79 on 2013-10-26
now I OC'd my GPU along with my E4300 and I am now getting the following.
```
=======================================================
    glmark2 2011.09
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce 8400GS/PCIe/SSE2
    GL_VERSION:    3.3.0 NVIDIA 319.60
=======================================================
[build] use-vbo=false:  FPS: 746
[build] use-vbo=true:  FPS: 1208
[texture] texture-filter=nearest:  FPS: 1210
[texture] texture-filter=linear:  FPS: 1200
[texture] texture-filter=mipmap:  FPS: 1415
[shading] shading=gouraud:  FPS: 934
[shading] shading=blinn-phong-inf:  FPS: 786
[shading] shading=phong:  FPS: 582
[bump] bump-render=high-poly:  FPS: 482
[bump] bump-render=normals:  FPS: 1145
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;:  FPS: 557
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;:  FPS: 235
[pulsar] light=false:quads=5:texture=false:  FPS: 1043
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4:  FPS: 259
[conditionals] fragment-steps=0:vertex-steps=0:  FPS: 1133
[conditionals] fragment-steps=5:vertex-steps=0:  FPS: 583
[conditionals] fragment-steps=0:vertex-steps=5:  FPS: 1096
[function] fragment-complexity=low:fragment-steps=5:  FPS: 882
[function] fragment-complexity=medium:fragment-steps=5:  FPS: 531
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5:  FPS: 858
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5:  FPS: 858
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5:  FPS: 660
=======================================================
                                  glmark2 Score: 836 
=======================================================

```
Xubuntu 12.04.3, windowed mode
Specs: 
E4300 OC'd to 2.4Ghz
AsRock 775Dual-VSTA
GeForce 8400GS OC'd to 580Mhz and Memory to 720Mhz for 3D Clock Frequencies
2GB DDRII

---

### Post by Ranko Kohime on 2013-10-27
> **Twidi said:**
> =======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) Haswell Mobile 
    GL_VERSION:    3.0 Mesa 9.2.1
=======================================================

Windowed (800x600) : 2945 
Fullscreen (1920x1080) : 947


(Intel Iris Pro HD 5200 Graphics, 3.11.0-12-generic, x86_64, Intel i7-4750HQ 4x2 cores, 16Go RAM)
I'm jelly.  I wish you could upgrade the CPU in laptops.  :(

---

### Post by Ranko Kohime on 2013-10-27
And table is updated.  Thanks for the scores!

---

### Post by irab on 2013-10-30
Setup:
MetaBox P157SM Laptop
Processor: i7-4900MQ
Graphics: NVIDIA GeForce GTX 780M 4GB GDDR5
RAM: 32GB DDR3 1600Mhz RAM
X11: LXDE Desktop

1920x1080 = 2721
800x600 = 8532

EDIT:

    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 780M/PCIe/SSE2
    GL_VERSION:    4.3.0 NVIDIA 319.32

---

### Post by Pako Pako on 2013-11-01
OpenGL Information
GL_VENDOR:     Tungsten Graphics, Inc
GL_RENDERER:   Mesa DRI Intel(R) 945GM x86/MMX/SSE2
GL_VERSION:    1.4 Mesa 8.0.4
glmark2 Score: 36 
Intel Core 1 Duo 1.2 GHz, Xubuntu, 1280x800 desktop (I presume 800 x 600 windowed?)

Ran into a problem with it on my old single-core CPU:

```
OpenGL Information
GL_VENDOR:     NVIDIA Corporation
GL_RENDERER:   GeForce FX Go5200 32M/64M/AGP/SSE2
GL_VERSION:    2.1.2 NVIDIA 173.14.30
=======================================================
[Suite] Precompilation
[Benchmark] Vertex array                FPS: 83
[Benchmark] Vertex buffer object        FPS: 103
glmark2: symbol lookup error: glmark2: undefined symbol: glGenerateMipmap
```

---

### Post by dannyboy79 on 2013-11-02
how are people running it in full screen mode?

---

### Post by DanglingPointer on 2013-11-03
Hi Ranko,

I see you haven't got an AMD HD 5870 in your table.  I've just run the test and got a glmark2 Score of [SIZE=3]**3799**[/SIZE].
It ran on window mode which I'm assuming is 800x600.
It is a desktop.

System Variables:
OS: Ubuntu 12.04 64bit
GPU: AMD HD 5870, 1GB
RAM: 16GB
Driver: Propriety FGLRX non-beta post-release updates from repository.
DE: Desktop
Resolution: 800x600 (default window mode)

Terminal results pasted underneath.

** Failed to set swap interval. Results may be bounded above by refresh rate.
=======================================================
    glmark2 2011.09
=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   ATI Radeon HD 5800 Series
    GL_VERSION:    4.2.12217 Compatibility Profile Context 12.104
=======================================================
[build] use-vbo=false:  FPS: 1866
[build] use-vbo=true:  FPS: 4143
[texture] texture-filter=nearest:  FPS: 4128
[texture] texture-filter=linear:  FPS: 4120
[texture] texture-filter=mipmap:  FPS: 4135
[shading] shading=gouraud:  FPS: 4068
[shading] shading=blinn-phong-inf:  FPS: 4062
[shading] shading=phong:  FPS: 4048
[bump] bump-render=high-poly:  FPS: 2811
[bump] bump-render=normals:  FPS: 4168
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;:  FPS: 4254
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;:  FPS: 3340
[pulsar] light=false:quads=5:texture=false:  FPS: 3799
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4:  FPS: 763
[conditionals] fragment-steps=0:vertex-steps=0:  FPS: 4263
[conditionals] fragment-steps=5:vertex-steps=0:  FPS: 4332
[conditionals] fragment-steps=0:vertex-steps=5:  FPS: 4230
[function] fragment-complexity=low:fragment-steps=5:  FPS: 4245
[function] fragment-complexity=medium:fragment-steps=5:  FPS: 4226
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5:  FPS: 4206
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5:  FPS: 4263
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5:  FPS: 4124
=======================================================
                                  glmark2 Score: 3799 
=======================================================

---

### Post by dannyboy79 on 2013-11-16
Ok, I just purchased a new tower which came with an HD5750. This test is run using the current stable release of the AMD driver from their website, catalyst 13.4 i believe it is. DISREGARD THIS it's not OC'd [It's OC'd from stock Core Clock speed from 550Mhz to 700Mhz and Memory clock speed from 800Mhz to 1150Mhz] and my new score when it runs in 800x600 (i can't figure out how to get it to run fullscreen) is 
```
=======================================================
    glmark2 2011.09
=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   ATI Radeon HD 5700 Series 
    GL_VERSION:    4.2.12217 Compatibility Profile Context 12.104
=======================================================
[build] use-vbo=false:  FPS: 2858
[build] use-vbo=true:  FPS: 5873
[texture] texture-filter=nearest:  FPS: 5788
[texture] texture-filter=linear:  FPS: 5746
[texture] texture-filter=mipmap:  FPS: 6382
[shading] shading=gouraud:  FPS: 4996
[shading] shading=blinn-phong-inf:  FPS: 4988
[shading] shading=phong:  FPS: 5762
[bump] bump-render=high-poly:  FPS: 3423
[bump] bump-render=normals:  FPS: 8065
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;:  FPS: 5476
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;:  FPS: 2689
[pulsar] light=false:quads=5:texture=false:  FPS: 6568
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4:  FPS: 2062
[conditionals] fragment-steps=0:vertex-steps=0:  FPS: 7065
[conditionals] fragment-steps=5:vertex-steps=0:  FPS: 5304
[conditionals] fragment-steps=0:vertex-steps=5:  FPS: 5126
[function] fragment-complexity=low:fragment-steps=5:  FPS: 5139
[function] fragment-complexity=medium:fragment-steps=5:  FPS: 5453
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5:  FPS: 6716
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5:  FPS: 6835
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5:  FPS: 5203
=======================================================
                                  glmark2 Score: 5341 
=======================================================
```

BTW, to the OP, I was running a desktop at the time of the test. running Xubuntu (XFCE 4.10)

---

### Post by cRaZyBisCuiT on 2013-11-17
With running XFCE in fullscreen:
```

arch@8470p:~$ uname -a
Linux 8470p 3.11.0-13-generic #20-Ubuntu SMP Wed Oct 23 07:38:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
arch@8470p:~$ cat /proc/cpuinfo 
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 58
model name    : Intel(R) Core(TM) i5-3320M CPU @ 2.60GHz

```

```

arch@8470p:~$  glmark2 --fullscreen
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) Ivybridge Mobile 
    GL_VERSION:    3.0 Mesa 9.2.1
=======================================================
[build] use-vbo=false: FPS: 583 FrameTime: 1.715 ms
[build] use-vbo=true: FPS: 635 FrameTime: 1.575 ms
[texture] texture-filter=nearest: FPS: 606 FrameTime: 1.650 ms
[texture] texture-filter=linear: FPS: 606 FrameTime: 1.650 ms
[texture] texture-filter=mipmap: FPS: 611 FrameTime: 1.637 ms
[shading] shading=gouraud: FPS: 548 FrameTime: 1.825 ms
[shading] shading=blinn-phong-inf: FPS: 549 FrameTime: 1.821 ms
[shading] shading=phong: FPS: 549 FrameTime: 1.821 ms
[bump] bump-render=high-poly: FPS: 437 FrameTime: 2.288 ms
[bump] bump-render=normals: FPS: 631 FrameTime: 1.585 ms
[bump] bump-render=height: FPS: 611 FrameTime: 1.637 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 352 FrameTime: 2.841 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 195 FrameTime: 5.128 ms
[pulsar] light=false:quads=5:texture=false: FPS: 528 FrameTime: 1.894 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 180 FrameTime: 5.556 ms
[desktop] effect=shadow:windows=4: FPS: 283 FrameTime: 3.534 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 364 FrameTime: 2.747 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 372 FrameTime: 2.688 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 385 FrameTime: 2.597 ms
[ideas] speed=duration: FPS: 517 FrameTime: 1.934 ms
[jellyfish] <default>: FPS: 355 FrameTime: 2.817 ms
[terrain] <default>: FPS: 51 FrameTime: 19.608 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 517 FrameTime: 1.934 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 520 FrameTime: 1.923 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 520 FrameTime: 1.923 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 523 FrameTime: 1.912 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 517 FrameTime: 1.934 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 521 FrameTime: 1.919 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 519 FrameTime: 1.927 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 522 FrameTime: 1.916 ms
=======================================================
                                  glmark2 Score: 470 
=======================================================

```

---

### Post by Ranko Kohime on 2013-11-21
> **cRaZyBisCuiT said:**
> With running XFCE in fullscreen:
What resolution are you running?

Otherwise, table is updated, with an updated score from my Thinkpad: 1175 vs. 854 it scored last time I checked, quite the improvement!  I can only chalk that up to driver improvements, thanks to the community.  ;)

---

### Post by oldrocker99 on 2013-11-21
> **dannyboy79 said:**
> how are people running it in full screen mode?

If you're running 12.04, there is no fullscreen mode; the 12.10 and later versions have added a --fullscreen switch.

---

### Post by dannyboy79 on 2013-11-22
> **oldrocker99 said:**
> If you're running 12.04, there is no fullscreen mode; the 12.10 and later versions have added a --fullscreen switch.
ah ok. thanks

something really weird, i thought i'd try out the latest AMD beta driver, version 13.11 over 13.4 and something must be wrong with it OR maybe it's just something wrong with the glmark2 program interfacing with the new driver but here's my new result. notice the error about failed to set swap interval?
```

** Failed to set swap interval. Results may be bounded above by refresh rate.
=======================================================
    glmark2 2011.09
=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   ATI Radeon HD 5700 Series 
    GL_VERSION:    4.3.12614 Compatibility Profile Context 13.25.18
=======================================================
[build] use-vbo=false:  FPS: 60
[build] use-vbo=true:  FPS: 60
[texture] texture-filter=nearest:  FPS: 59
[texture] texture-filter=linear:  FPS: 59
[texture] texture-filter=mipmap:  FPS: 59
[shading] shading=gouraud:  FPS: 60
[shading] shading=blinn-phong-inf:  FPS: 59
[shading] shading=phong:  FPS: 59
[bump] bump-render=high-poly:  FPS: 59
[bump] bump-render=normals:  FPS: 59
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;:  FPS: 59
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;:  FPS: 60
[pulsar] light=false:quads=5:texture=false:  FPS: 60
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4:  FPS: 59
[conditionals] fragment-steps=0:vertex-steps=0:  FPS: 59
[conditionals] fragment-steps=5:vertex-steps=0:  FPS: 59
[conditionals] fragment-steps=0:vertex-steps=5:  FPS: 59
[function] fragment-complexity=low:fragment-steps=5:  FPS: 59
[function] fragment-complexity=medium:fragment-steps=5:  FPS: 59
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5:  FPS: 59
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5:  FPS: 59
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5:  FPS: 59
=======================================================
                                  glmark2 Score: 59 
=======================================================

```
whereas with the latest stable release I was getting 5,341 LOL  I tested out Serious Sam 3 BFE momentarily and am still pulling around 30FPS so maybe it's just an issue with glmark2 and the new AMD beta linux driver?

BTW, to the OP, I was running a desktop at the time of the test. running Xubuntu (XFCE 4.10)

---

### Post by Ranko Kohime on 2013-11-22
The new driver is causing glmark2 to vsync.  So yeah, the score is limited to ~60.

---

### Post by dannyboy79 on 2013-11-23
Ok, this latest AMD BETA driver V9.4 may be a regression as far as performance. You guys saw that the 13.11beta6 driver resulted in locked FPS at 60*, it's post #61 above. Well now I am using the latest AMD drive V9.4 and I get the following:
```

** Failed to set swap interval. Results may be bounded above by refresh rate.
=======================================================
    glmark2 2011.09
=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   ATI Radeon HD 5700 Series 
    GL_VERSION:    4.3.12614 Compatibility Profile Context 13.25.18
=======================================================
[build] use-vbo=false:  FPS: 3963
[build] use-vbo=true:  FPS: 658
[texture] texture-filter=nearest:  FPS: 674
[texture] texture-filter=linear:  FPS: 647
[texture] texture-filter=mipmap:  FPS: 752
[shading] shading=gouraud:  FPS: 788
[shading] shading=blinn-phong-inf:  FPS: 772
[shading] shading=phong:  FPS: 644
[bump] bump-render=high-poly:  FPS: 500
[bump] bump-render=normals:  FPS: 870
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;:  FPS: 501
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;:  FPS: 498
[pulsar] light=false:quads=5:texture=false:  FPS: 677
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4:  FPS: 1272
[conditionals] fragment-steps=0:vertex-steps=0:  FPS: 631
[conditionals] fragment-steps=5:vertex-steps=0:  FPS: 504
[conditionals] fragment-steps=0:vertex-steps=5:  FPS: 503
[function] fragment-complexity=low:fragment-steps=5:  FPS: 521
[function] fragment-complexity=medium:fragment-steps=5:  FPS: 529
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5:  FPS: 749
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5:  FPS: 567
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5:  FPS: 516
=======================================================
                                  glmark2 Score: 806 
=======================================================

```

I was getting a glmark2 score of 5,341 when I was running the last stable released AMD driver which was version 13.4. I am not sure how to take all these benchmarks, I just want to use the best driver to get the most out of this old HD5750.

---

### Post by DanglingPointer on 2013-11-23
> **dannyboy79 said:**
> Ok, this latest AMD BETA driver V9.4 may be a regression as far as performance. You guys saw that the 13.11beta6 driver resulted in locked FPS at 60*, it's post #61 above. Well now I am using the latest AMD drive V9.4 and I get the following:
```

** Failed to set swap interval. Results may be bounded above by refresh rate.
=======================================================
    glmark2 2011.09
=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   ATI Radeon HD 5700 Series 
    GL_VERSION:    4.3.12614 Compatibility Profile Context 13.25.18
=======================================================
[build] use-vbo=false:  FPS: 3963
[build] use-vbo=true:  FPS: 658
[texture] texture-filter=nearest:  FPS: 674
[texture] texture-filter=linear:  FPS: 647
[texture] texture-filter=mipmap:  FPS: 752
[shading] shading=gouraud:  FPS: 788
[shading] shading=blinn-phong-inf:  FPS: 772
[shading] shading=phong:  FPS: 644
[bump] bump-render=high-poly:  FPS: 500
[bump] bump-render=normals:  FPS: 870
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;:  FPS: 501
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;:  FPS: 498
[pulsar] light=false:quads=5:texture=false:  FPS: 677
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4:  FPS: 1272
[conditionals] fragment-steps=0:vertex-steps=0:  FPS: 631
[conditionals] fragment-steps=5:vertex-steps=0:  FPS: 504
[conditionals] fragment-steps=0:vertex-steps=5:  FPS: 503
[function] fragment-complexity=low:fragment-steps=5:  FPS: 521
[function] fragment-complexity=medium:fragment-steps=5:  FPS: 529
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5:  FPS: 749
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5:  FPS: 567
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5:  FPS: 516
=======================================================
                                  glmark2 Score: 806 
=======================================================

```

I was getting a glmark2 score of 5,341 when I was running the last stable released AMD driver which was version 13.4. I am not sure how to take all these benchmarks, I just want to use the best driver to get the most out of this old HD5750.

Perhaps try running the Unigine benchmarks from Phoronix instead as they would run tests much more similar to game engines.  glmark2 is outdated I'd say.

---

### Post by dannyboy79 on 2013-11-23
yeah, i have been considering that. As a side note, i had a hell of a time trying to get the newest AMD beta v9.4 driver working and gave up and actually had to restore my / root partition image from a backup due to the opengl 32bit and 64bit library symlinks getting all screwed up and I spent 4 hours trying to correct the issue but it was just too far over my head.

---

### Post by DanglingPointer on 2013-11-23
> **dannyboy79 said:**
> yeah, i have been considering that. As a side note, i had a hell of a time trying to get the newest AMD beta v9.4 driver working and gave up and actually had to restore my / root partition image from a backup due to the opengl 32bit and 64bit library symlinks getting all screwed up and I spent 4 hours trying to correct the issue but it was just too far over my head.

Well if you're still keen perhaps run through your experience at the Hardware forum?

I too ran into a couple of problems with the new driver not installing correctly when installing via deb packages following the instructions here [http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx)
But I was able to get around it. :D

I have to go to do several errands, but when I get back I may outline what I did at the hardware forum just in case others have had similar problems.

---

### Post by dubritton on 2013-11-24
With my two Asus AMD Radeon HD 7850's running the latest beta drivers (13.11) with an AMD-fx 8150 on Unity DE.
Windowed:
=======================================================
                                  glmark2 Score: 1188 
=======================================================

Fullscreen:
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   AMD Radeon HD 7800 Series  
    GL_VERSION:    4.3.12614 Compatibility Profile Context 13.25.18
=======================================================
=======================================================
                                  glmark2 Score: 4072 
=======================================================

---

### Post by Ranko Kohime on 2013-11-25
Did you perhaps omit a number from the windowed test?  It should be higher than a fullscreen test.

---

### Post by dubritton on 2013-11-25
No, I did not omit any numbers - that struck me as strange too.

---

### Post by efflandt on 2013-11-26
I wonder how relevant glmark2 is to actual gaming or comparison between different Ubuntu versions, especially since different Ubuntu versions have a different number of tests and 12.04 glmark2 does not have --fullscreen.

For example glmark2 in 64-bit 13.10 on i7-4700MQ laptop nvidia-experimental-310 (319.60) w/Unity DE:
Intel HD 4600: 800x600 **173**, 1920x1080 (fullscreen) **88**
GTX 765M (optirun): 800x600 **235**, 1920x1080 (fullscreen) **95**

Except for the terrain test, that made most other glmark2 tests faster than 60 Hz refresh rate even with Intel full screen. Yet in another thread here about GPUTest the GTX 765M did some (not all) benchmarks slightly faster the GTX 550 Ti (319.32 driver in 12.04) on my desktop and Intel was dismal (ave. 1 fps or less some tests, unable to run some tests). Team Fortress 2 with high graphics at 1080p is unplayable with Intel (very slow with short repeating sound loops), but runs smoothly with GTX 765M.

Another point of reference is Unigine Valley Benchmark 1.0 at default settings (which would not even run on integrated Intel) where GTX 550 Ti averaged 20.6 fps vs 18.2 for GTX 765M at 1080p fullscreen for both. That is much closer than the wide difference in glmark2 scores. Although, admittedly in some simple tests (like glxspheres/glxspheres64) the GTX 550 Ti is much faster than the GTX 765M which is much faster than Intel graphics.

---

### Post by DanglingPointer on 2013-11-26
Perhaps we should start a thread for Unigine Valley instead?

---

### Post by Ranko Kohime on 2013-11-27
> **dubritton said:**
> No, I did not omit any numbers - that struck me as strange too.
That IS strange.  I have a 7850 as well, and it can do over 8,000 by itself.  Crossfire should do at least as well, and should be close to double.

---

### Post by Ranko Kohime on 2013-11-27
> **DanglingPointer said:**
> Perhaps we should start a thread for Unigine Valley instead?
Start a thread for Unigine, full stop.  Valley and Heaven are just maps on the Unigine "game" engine.  (They market it as a game engine, but I've never heard of a game that actually used it)

That being said, I've never been able to run Unigine on either Intel or AMD graphics, in Linux.

---

### Post by DanglingPointer on 2013-11-27
> **Ranko Kohime said:**
> Start a thread for Unigine, full stop.  Valley and Heaven are just maps on the Unigine "game" engine.  (They market it as a game engine, but I've never heard of a game that actually used it)

That being said, I've never been able to run Unigine on either Intel or AMD graphics, in Linux.

There's Relics of Anoraht (Alpha phase) and Oil Rush (available on Steam).  

Their engine is used mostly for professional simulators though.  It is used here in Australia for Steamship simulations ([https://unigine.com/press-releases/20130709-ai3d-steamship-simulator/](https://unigine.com/press-releases/20130709-ai3d-steamship-simulator/)).  It is used for helicopter simulators, armoured/tank simulators from what I can see around the net...
[http://www.phoronix.com/scan.php?page=news_item&px=MTUyODA](http://www.phoronix.com/scan.php?page=news_item&px=MTUyODA)
[https://unigine.com/press-releases/130430-trinity-interactive/](https://unigine.com/press-releases/130430-trinity-interactive/)

---

### Post by dannyboy79 on 2013-12-02
> **DanglingPointer said:**
> Perhaps we should start a thread for Unigine Valley instead?
im game to do that, i actually just used phoronix test suite, it easily installs almost any test you can think of whether it's for CPU, I/O, Memory or GFX, its so easy to install the test and run it. I just did a video showing the difference between an HD5750 and an HD7770 Black Edition using Unigine's Valley which I am uploading tomorrow (cause it's part of a series I do called Tech Tuesday's w/ Ubu) 

To the OP, i sent you a PM asking how to create the boxes (or excel columns and rows) like you did on page 1 of this thread cause I want to do the same for the GPUTest thread I started.

---

### Post by DanglingPointer on 2013-12-03
I've published a few to OpenBenchmark.org for the 290X.  If I'm not mistaken any test with *vault* is my rig.  If AMD releases another beta I'll publish again.

---

### Post by cRaZyBisCuiT on 2013-12-03
[TABLE="class: grid, width: 500"]
[TR]
[TD]**Manufacturer**[/TD]
[TD]**Model**
(driver)[/TD]
[TD][B]Resolution
[/B](fullscreen)[/TD]
[TD][B]DE?*
(which?)
[/B]
[/TD]
[TD]**Score **(window)[/TD]
[TD]**Score **(fullscreen)[/TD]
[TD]**CPU**[/TD]
[/TR]
[TR]
[TD]Nvidia[/TD]
[TD]GTX 560 Ti (331.20)[/TD]
[TD]1920x1080
[/TD]
[TD]Yes
(Xfce 4.10)
[/TD]
[TD]13855[/TD]
[TD]3297[/TD]
[TD]Q6600
(4 x 2,4 GHZ)[/TD]
[/TR]
[/TABLE]


Seems like decent nVidia graphics cards could easyly beat ATI cards that should be quite superior (like ATI 7970). Who says ATIs drivers are catching up? Very slowly maybe.

Since it's also important to know which CPU a user has (it could limit the results) we should maybe add that information. To prevent several entries for the same card I propose to use a table like I did.

---

### Post by Ranko Kohime on 2013-12-04
> **DanglingPointer said:**
> ...and Oil Rush (available on Steam).
That would explain why Oil Rush doesn't start for me.

---

### Post by tulisqiya on 2013-12-06
This I do not understand

---

### Post by bkuberek on 2013-12-29
AMD Radeon HD 6450
at 1920x1080
glmark2 Score: 868

---

### Post by sound74145 on 2014-01-21
_**Alienware M18xR2 System Summary**_
[SIZE=1]Intel Quad Core i7-3720QM CPU @ 2.60GHz boost limit 4Ghz
L1 Cache: 32KiB, L2 Cache: 256KiB, L3 Cache: 6MiB 
System Memory: 24GiB SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
HDD0: 500GB, HDD1: 750GB, HDD2: 1TB, mSATA:  
Graphics: nVidia GeForce GTX 660M PCI Express x8 Gen3
Total available graphics memory: 4095MB 
Dedicated video memory: 2048MB GDDR5
CUDA Cores: 384
Display Ports: VGA-0, LVDS-0, DP-0, DP-1 HDMI-0, HDMI-1
OS: Ubuntu 12.04 LTS with CUDA parallel processing compiled kernel[/SIZE]
[I]glmark would not run full screen. At least in in my current 3 display configuration at work. 
I ran glmark2 in the background on desktop 3 while working in an XP virtual machine on desktop 4.
Will try again sometime when I'm not busy see if the score changes.[/I]
=======================================================
    glmark2 2011.09
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 660M/PCIe/SSE2
    GL_VERSION:    4.2.0 NVIDIA 304.88
=======================================================
[build] use-vbo=false:  FPS: 5724
[build] use-vbo=true:  FPS: 7500
[texture] texture-filter=nearest:  FPS: 7639
[texture] texture-filter=linear:  FPS: 7537
[texture] texture-filter=mipmap:  FPS: 8344
[shading] shading=gouraud:  FPS: 6089
[shading] shading=blinn-phong-inf:  FPS: 6118
[shading] shading=phong:  FPS: 5415
[bump] bump-render=high-poly:  FPS: 3257
[bump] bump-render=normals:  FPS: 7654
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;:  FPS: 4593
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;:  FPS: 2195
[pulsar] light=false:quads=5:texture=false:  FPS: 6143
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4:  FPS: 1797
[conditionals] fragment-steps=0:vertex-steps=0:  FPS: 6582
[conditionals] fragment-steps=5:vertex-steps=0:  FPS: 4967
[conditionals] fragment-steps=0:vertex-steps=5:  FPS: 6591
[function] fragment-complexity=low:fragment-steps=5:  FPS: 6538
[function] fragment-complexity=medium:fragment-steps=5:  FPS: 5491
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5:  FPS: 7382
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5:  FPS: 6543
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5:  FPS: 5710
=======================================================
                                  glmark2 Score: 5900 
=======================================================

---

### Post by Ranko Kohime on 2014-01-23
And, OP updated.

---

### Post by Willyweasel on 2014-01-30
System Specs:
CPU: AMD FX-6300 (overclocked to 4.3ghz)
GPU: AMD HD 7870
MOBO: Gigabyte GA-970A-DS3P
RAM: 8gb gskill 1333 ddr3 (overclocked to 1600) 
Distro: Kubuntu 13.10
Resolution: 1920x1080
Desktop environment was running 
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   AMD Radeon HD 7800 Series 
    GL_VERSION:    4.3.12618 Compatibility Profile Context 13.251
=======================================================
[build] use-vbo=false: FPS: 5748 FrameTime: 0.174 ms
[build] use-vbo=true: FPS: 10584 FrameTime: 0.094 ms
[texture] texture-filter=nearest: FPS: 8780 FrameTime: 0.114 ms
[texture] texture-filter=linear: FPS: 8776 FrameTime: 0.114 ms
[texture] texture-filter=mipmap: FPS: 8940 FrameTime: 0.112 ms
[shading] shading=gouraud: FPS: 8951 FrameTime: 0.112 ms
[shading] shading=blinn-phong-inf: FPS: 8940 FrameTime: 0.112 ms
[shading] shading=phong: FPS: 8692 FrameTime: 0.115 ms
[bump] bump-render=high-poly: FPS: 6580 FrameTime: 0.152 ms
[bump] bump-render=normals: FPS: 10254 FrameTime: 0.098 ms
[bump] bump-render=height: FPS: 9979 FrameTime: 0.100 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 4844 FrameTime: 0.206 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 2185 FrameTime: 0.458 ms
[pulsar] light=false:quads=5:texture=false: FPS: 6448 FrameTime: 0.155 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 1920 FrameTime: 0.521 ms
[desktop] effect=shadow:windows=4: FPS: 2348 FrameTime: 0.426 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 918 FrameTime: 1.089 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1604 FrameTime: 0.623 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1167 FrameTime: 0.857 ms
[ideas] speed=duration: FPS: 4172 FrameTime: 0.240 ms
[jellyfish] <default>: FPS: 4135 FrameTime: 0.242 ms
[terrain] <default>: FPS: 367 FrameTime: 2.725 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 8781 FrameTime: 0.114 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 8306 FrameTime: 0.120 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 8607 FrameTime: 0.116 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 8749 FrameTime: 0.114 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 7767 FrameTime: 0.129 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 8673 FrameTime: 0.115 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 8680 FrameTime: 0.115 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 8653 FrameTime: 0.116 ms
=======================================================
                                  glmark2 Score: 6484 
=======================================================

---

### Post by dannyboy79 on 2014-02-07
Just built me a new machine. Using stock ubuntu 13.10 with i5-4670k (igpu HD4600) the default driver which is i915. I did OC my chip from 3.4Ghz to 4.0Ghz (using a CM 120V for cooling). G-Skill sniper 8GB 2133Mhz ram. I don't use any compositing and I run XFCE 4.10. Here's the results of 800x600 and 1440x900. Desktop (XFCE was running with chrome, steam, and terminal open as well)
**800x600**
```
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) Haswell Desktop 
    GL_VERSION:    3.0 Mesa 9.2.1
=======================================================
[build] use-vbo=false: FPS: 3163 FrameTime: 0.316 ms
[build] use-vbo=true: FPS: 3581 FrameTime: 0.279 ms
[texture] texture-filter=nearest: FPS: 4056 FrameTime: 0.247 ms
[texture] texture-filter=linear: FPS: 3936 FrameTime: 0.254 ms
[texture] texture-filter=mipmap: FPS: 3936 FrameTime: 0.254 ms
[shading] shading=gouraud: FPS: 3100 FrameTime: 0.323 ms
[shading] shading=blinn-phong-inf: FPS: 3103 FrameTime: 0.322 ms
[shading] shading=phong: FPS: 3057 FrameTime: 0.327 ms
[bump] bump-render=high-poly: FPS: 1542 FrameTime: 0.649 ms
[bump] bump-render=normals: FPS: 4073 FrameTime: 0.246 ms
[bump] bump-render=height: FPS: 3795 FrameTime: 0.264 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 1879 FrameTime: 0.532 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 867 FrameTime: 1.153 ms
[pulsar] light=false:quads=5:texture=false: FPS: 2797 FrameTime: 0.358 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 844 FrameTime: 1.185 ms
[desktop] effect=shadow:windows=4: FPS: 1459 FrameTime: 0.685 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 573 FrameTime: 1.745 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1407 FrameTime: 0.711 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 492 FrameTime: 2.033 ms
[ideas] speed=duration: FPS: 2299 FrameTime: 0.435 ms
[jellyfish] <default>: FPS: 1586 FrameTime: 0.631 ms
[terrain] <default>: FPS: 191 FrameTime: 5.236 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 3302 FrameTime: 0.303 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 3418 FrameTime: 0.293 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 3393 FrameTime: 0.295 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 3401 FrameTime: 0.294 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 3442 FrameTime: 0.291 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 3397 FrameTime: 0.294 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 3334 FrameTime: 0.300 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 3384 FrameTime: 0.296 ms
=======================================================
                                  glmark2 Score: 2626 
=======================================================

```
**1440x900**
```

ubu@saucy-haswell:~/phoronix-test-suite$ glmark2 --fullscreen
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) Haswell Desktop 
    GL_VERSION:    3.0 Mesa 9.2.1
=======================================================
[build] use-vbo=false: FPS: 1419 FrameTime: 0.705 ms
[build] use-vbo=true: FPS: 1515 FrameTime: 0.660 ms
[texture] texture-filter=nearest: FPS: 1514 FrameTime: 0.661 ms
[texture] texture-filter=linear: FPS: 1510 FrameTime: 0.662 ms
[texture] texture-filter=mipmap: FPS: 1533 FrameTime: 0.652 ms
[shading] shading=gouraud: FPS: 1345 FrameTime: 0.743 ms
[shading] shading=blinn-phong-inf: FPS: 1342 FrameTime: 0.745 ms
[shading] shading=phong: FPS: 1333 FrameTime: 0.750 ms
[bump] bump-render=high-poly: FPS: 939 FrameTime: 1.065 ms
[bump] bump-render=normals: FPS: 1566 FrameTime: 0.639 ms
[bump] bump-render=height: FPS: 1470 FrameTime: 0.680 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 685 FrameTime: 1.460 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 320 FrameTime: 3.125 ms
[pulsar] light=false:quads=5:texture=false: FPS: 1075 FrameTime: 0.930 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 333 FrameTime: 3.003 ms
[desktop] effect=shadow:windows=4: FPS: 556 FrameTime: 1.799 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 760 FrameTime: 1.316 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1058 FrameTime: 0.945 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 803 FrameTime: 1.245 ms
[ideas] speed=duration: FPS: 1058 FrameTime: 0.945 ms
[jellyfish] <default>: FPS: 627 FrameTime: 1.595 ms
[terrain] <default>: FPS: 91 FrameTime: 10.989 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 1274 FrameTime: 0.785 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 1306 FrameTime: 0.766 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 1272 FrameTime: 0.786 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 1273 FrameTime: 0.786 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 1304 FrameTime: 0.767 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 1275 FrameTime: 0.784 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 1276 FrameTime: 0.784 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 1299 FrameTime: 0.770 ms
=======================================================
                                  glmark2 Score: 1104 
=======================================================
```

---

### Post by dannyboy79 on 2014-02-16
Just built me a new machine. Using xubuntu 13.10 with kernel 3.13 (mainline) AND Oibaf's PPA with i5-4670k (igpu HD4600). I did OC my chip from 3.4Ghz to 4.0Ghz (using a CM 120V for cooling). G-Skill sniper 8GB 2133Mhz ram. I don't use any compositing and I run XFCE 4.10. Desktop (XFCE was running with chrome, guvcview, thunar, synergy, and terminal open as well) 
**800x600**
```

=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) Haswell Desktop 
    GL_VERSION:    3.0 Mesa 10.2.0-devel (git-1020d89 saucy-oibaf-ppa)
=======================================================
[build] use-vbo=false: FPS: 3444 FrameTime: 0.290 ms
[build] use-vbo=true: FPS: 3539 FrameTime: 0.283 ms
[texture] texture-filter=nearest: FPS: 4045 FrameTime: 0.247 ms
[texture] texture-filter=linear: FPS: 4022 FrameTime: 0.249 ms
[texture] texture-filter=mipmap: FPS: 4037 FrameTime: 0.248 ms
[shading] shading=gouraud: FPS: 3118 FrameTime: 0.321 ms
[shading] shading=blinn-phong-inf: FPS: 3120 FrameTime: 0.321 ms
[shading] shading=phong: FPS: 3068 FrameTime: 0.326 ms
[bump] bump-render=high-poly: FPS: 1587 FrameTime: 0.630 ms
[bump] bump-render=normals: FPS: 4256 FrameTime: 0.235 ms
[bump] bump-render=height: FPS: 4012 FrameTime: 0.249 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 2205 FrameTime: 0.454 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 946 FrameTime: 1.057 ms
[pulsar] light=false:quads=5:texture=false: FPS: 2925 FrameTime: 0.342 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 917 FrameTime: 1.091 ms
[desktop] effect=shadow:windows=4: FPS: 1508 FrameTime: 0.663 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1085 FrameTime: 0.922 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1276 FrameTime: 0.784 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1180 FrameTime: 0.847 ms
[ideas] speed=duration: FPS: 2604 FrameTime: 0.384 ms
[jellyfish] <default>: FPS: 1639 FrameTime: 0.610 ms
[terrain] <default>: FPS: 211 FrameTime: 4.739 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 3465 FrameTime: 0.289 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 3574 FrameTime: 0.280 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 3445 FrameTime: 0.290 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 3451 FrameTime: 0.290 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 3410 FrameTime: 0.293 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 3444 FrameTime: 0.290 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 3406 FrameTime: 0.294 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 3379 FrameTime: 0.296 ms
=======================================================
                                  glmark2 Score: 2743 
=======================================================


```
**1440x900**
```

=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) Haswell Desktop 
    GL_VERSION:    3.0 Mesa 10.2.0-devel (git-1020d89 saucy-oibaf-ppa)
=======================================================
[build] use-vbo=false: FPS: 1443 FrameTime: 0.693 ms
[build] use-vbo=true: FPS: 1482 FrameTime: 0.675 ms
[texture] texture-filter=nearest: FPS: 1474 FrameTime: 0.678 ms
[texture] texture-filter=linear: FPS: 1471 FrameTime: 0.680 ms
[texture] texture-filter=mipmap: FPS: 1448 FrameTime: 0.691 ms
[shading] shading=gouraud: FPS: 1266 FrameTime: 0.790 ms
[shading] shading=blinn-phong-inf: FPS: 1280 FrameTime: 0.781 ms
[shading] shading=phong: FPS: 1301 FrameTime: 0.769 ms
[bump] bump-render=high-poly: FPS: 918 FrameTime: 1.089 ms
[bump] bump-render=normals: FPS: 1528 FrameTime: 0.654 ms
[bump] bump-render=height: FPS: 1484 FrameTime: 0.674 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 756 FrameTime: 1.323 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 331 FrameTime: 3.021 ms
[pulsar] light=false:quads=5:texture=false: FPS: 1058 FrameTime: 0.945 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 347 FrameTime: 2.882 ms
[desktop] effect=shadow:windows=4: FPS: 544 FrameTime: 1.838 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 950 FrameTime: 1.053 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1046 FrameTime: 0.956 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1013 FrameTime: 0.987 ms
[ideas] speed=duration: FPS: 1047 FrameTime: 0.955 ms
[jellyfish] <default>: FPS: 618 FrameTime: 1.618 ms
[terrain] <default>: FPS: 102 FrameTime: 9.804 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 1246 FrameTime: 0.803 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 1278 FrameTime: 0.782 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 1246 FrameTime: 0.803 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 1250 FrameTime: 0.800 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 1272 FrameTime: 0.786 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 1248 FrameTime: 0.801 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 1247 FrameTime: 0.802 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 1264 FrameTime: 0.791 ms
=======================================================
                                  glmark2 Score: 1098 
=======================================================
```

**1920x1080**
```
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) Haswell Desktop 
    GL_VERSION:    3.0 Mesa 10.2.0-devel (git-1020d89 saucy-oibaf-ppa)
=======================================================
[build] use-vbo=false: FPS: 896 FrameTime: 1.116 ms
[build] use-vbo=true: FPS: 914 FrameTime: 1.094 ms
[texture] texture-filter=nearest: FPS: 897 FrameTime: 1.115 ms
[texture] texture-filter=linear: FPS: 900 FrameTime: 1.111 ms
[texture] texture-filter=mipmap: FPS: 911 FrameTime: 1.098 ms
[shading] shading=gouraud: FPS: 815 FrameTime: 1.227 ms
[shading] shading=blinn-phong-inf: FPS: 815 FrameTime: 1.227 ms
[shading] shading=phong: FPS: 816 FrameTime: 1.225 ms
[bump] bump-render=high-poly: FPS: 650 FrameTime: 1.538 ms
[bump] bump-render=normals: FPS: 925 FrameTime: 1.081 ms
[bump] bump-render=height: FPS: 899 FrameTime: 1.112 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 451 FrameTime: 2.217 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 200 FrameTime: 5.000 ms
[pulsar] light=false:quads=5:texture=false: FPS: 649 FrameTime: 1.541 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 222 FrameTime: 4.505 ms
[desktop] effect=shadow:windows=4: FPS: 334 FrameTime: 2.994 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 678 FrameTime: 1.475 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 676 FrameTime: 1.479 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 685 FrameTime: 1.460 ms
[ideas] speed=duration: FPS: 654 FrameTime: 1.529 ms
[jellyfish] <default>: FPS: 382 FrameTime: 2.618 ms
[terrain] <default>: FPS: 67 FrameTime: 14.925 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 762 FrameTime: 1.312 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 779 FrameTime: 1.284 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 763 FrameTime: 1.311 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 764 FrameTime: 1.309 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 778 FrameTime: 1.285 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 763 FrameTime: 1.311 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 763 FrameTime: 1.311 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 774 FrameTime: 1.292 ms
=======================================================
                                  glmark2 Score: 686 
=======================================================
```

---

### Post by dannyboy79 on 2014-02-17
Just got an EVGA GTX 760. The ACX Active Cooling Superclocking 2GB Version with Double BIOS. Nvidia Proprietary driver 331.38, nvidia-settings all stock. Using xubuntu 13.10 with kernel 3.11.0-17-generic, i5-4670k (igpu HD4600). I did OC my chip from 3.4Ghz to 4.0Ghz (using a CM 120V for cooling). G-Skill sniper 8GB 2133Mhz ram. I don't use any compositing and I run XFCE 4.10. Desktop Manager was running with 1 xfce-terminal open
Here's the results
**800x600**
```
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 760/PCIe/SSE2
    GL_VERSION:    4.4.0 NVIDIA 331.38
=======================================================
[build] use-vbo=false: FPS: 10219 FrameTime: 0.098 ms
[build] use-vbo=true: FPS: 15302 FrameTime: 0.065 ms
[texture] texture-filter=nearest: FPS: 13930 FrameTime: 0.072 ms
[texture] texture-filter=linear: FPS: 13849 FrameTime: 0.072 ms
[texture] texture-filter=mipmap: FPS: 14383 FrameTime: 0.070 ms
[shading] shading=gouraud: FPS: 12898 FrameTime: 0.078 ms
[shading] shading=blinn-phong-inf: FPS: 13007 FrameTime: 0.077 ms
[shading] shading=phong: FPS: 12801 FrameTime: 0.078 ms
[bump] bump-render=high-poly: FPS: 9204 FrameTime: 0.109 ms
[bump] bump-render=normals: FPS: 15393 FrameTime: 0.065 ms
[bump] bump-render=height: FPS: 15210 FrameTime: 0.066 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 11342 FrameTime: 0.088 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 7830 FrameTime: 0.128 ms
[pulsar] light=false:quads=5:texture=false: FPS: 14090 FrameTime: 0.071 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 4672 FrameTime: 0.214 ms
[desktop] effect=shadow:windows=4: FPS: 7815 FrameTime: 0.128 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1531 FrameTime: 0.653 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1825 FrameTime: 0.548 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1769 FrameTime: 0.565 ms
[ideas] speed=duration: FPS: 12432 FrameTime: 0.080 ms
[jellyfish] <default>: FPS: 8527 FrameTime: 0.117 ms
[terrain] <default>: FPS: 856 FrameTime: 1.168 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 13440 FrameTime: 0.074 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 13053 FrameTime: 0.077 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 13442 FrameTime: 0.074 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 13289 FrameTime: 0.075 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 12941 FrameTime: 0.077 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 13291 FrameTime: 0.075 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 13298 FrameTime: 0.075 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 13205 FrameTime: 0.076 ms
=======================================================
                                  glmark2 Score: 10828 
=======================================================

```
**192x1080**
```
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 760/PCIe/SSE2
    GL_VERSION:    4.4.0 NVIDIA 331.38
=======================================================
[build] use-vbo=false: FPS: 5838 FrameTime: 0.171 ms
[build] use-vbo=true: FPS: 6093 FrameTime: 0.164 ms
[texture] texture-filter=nearest: FPS: 5611 FrameTime: 0.178 ms
[texture] texture-filter=linear: FPS: 5615 FrameTime: 0.178 ms
[texture] texture-filter=mipmap: FPS: 5664 FrameTime: 0.177 ms
[shading] shading=gouraud: FPS: 5289 FrameTime: 0.189 ms
[shading] shading=blinn-phong-inf: FPS: 5298 FrameTime: 0.189 ms
[shading] shading=phong: FPS: 5251 FrameTime: 0.190 ms
[bump] bump-render=high-poly: FPS: 4924 FrameTime: 0.203 ms
[bump] bump-render=normals: FPS: 5949 FrameTime: 0.168 ms
[bump] bump-render=height: FPS: 5874 FrameTime: 0.170 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 3804 FrameTime: 0.263 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 2257 FrameTime: 0.443 ms
[pulsar] light=false:quads=5:texture=false: FPS: 5123 FrameTime: 0.195 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 1762 FrameTime: 0.568 ms
[desktop] effect=shadow:windows=4: FPS: 2625 FrameTime: 0.381 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1563 FrameTime: 0.640 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1753 FrameTime: 0.570 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1702 FrameTime: 0.588 ms
[ideas] speed=duration: FPS: 4421 FrameTime: 0.226 ms
[jellyfish] <default>: FPS: 2962 FrameTime: 0.338 ms
[terrain] <default>: FPS: 436 FrameTime: 2.294 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 5278 FrameTime: 0.189 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 4857 FrameTime: 0.206 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 5278 FrameTime: 0.189 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 5163 FrameTime: 0.194 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 4802 FrameTime: 0.208 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 5151 FrameTime: 0.194 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 5153 FrameTime: 0.194 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 4934 FrameTime: 0.203 ms
=======================================================
                                  glmark2 Score: 4347 
=======================================================

```

---

### Post by knpoe on 2014-02-23
*Default settings* *run* 
                             Product Name: MacBookPro[B]8,1
Linux 3.11[/B]
```
=======================================================   
 glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) Sandybridge Mobile 
    GL_VERSION:    3.0 Mesa 9.2.1
=======================================================
[build] use-vbo=false: FPS: 1327 FrameTime: 0.754 ms
[build] use-vbo=true: FPS: 1393 FrameTime: 0.718 ms
[texture] texture-filter=nearest: FPS: 1280 FrameTime: 0.781 ms
[texture] texture-filter=linear: FPS: 1277 FrameTime: 0.783 ms
[texture] texture-filter=mipmap: FPS: 1299 FrameTime: 0.770 ms
[shading] shading=gouraud: FPS: 1218 FrameTime: 0.821 ms
[shading] shading=blinn-phong-inf: FPS: 1219 FrameTime: 0.820 ms
[shading] shading=phong: FPS: 1153 FrameTime: 0.867 ms
[bump] bump-render=high-poly: FPS: 823 FrameTime: 1.215 ms
[bump] bump-render=normals: FPS: 1372 FrameTime: 0.729 ms
[bump] bump-render=height: FPS: 1297 FrameTime: 0.771 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 738 FrameTime: 1.355 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 384 FrameTime: 2.604 ms
[pulsar] light=false:quads=5:texture=false: FPS: 1255 FrameTime: 0.797 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 405 FrameTime: 2.469 ms
[desktop] effect=shadow:windows=4: FPS: 696 FrameTime: 1.437 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 559 FrameTime: 1.789 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 709 FrameTime: 1.410 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 618 FrameTime: 1.618 ms
[ideas] speed=duration: FPS: 1050 FrameTime: 0.952 ms
[jellyfish] <default>: FPS: 814 FrameTime: 1.229 ms
[terrain] <default>: FPS: 100 FrameTime: 10.000 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 1241 FrameTime: 0.806 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 1236 FrameTime: 0.809 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 1241 FrameTime: 0.806 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 1244 FrameTime: 0.804 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 1240 FrameTime: 0.806 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 1242 FrameTime: 0.805 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 1237 FrameTime: 0.808 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 1179 FrameTime: 0.848 ms
=======================================================
                                  glmark2 Score: 1028 
=======================================================
```


_**Processor Information**_
    Socket Designation: U2E1
    Type: Central Processor
    Manufacturer: Intel(R) Corporation
    ID: A7 06 02 00 FF FB EB BF
    Version: Intel(R) Core(TM)* i5-2415M CPU @ 2.30GHz*
    Voltage: 0.0 V
    Max Speed: 2300 MHz
    Current Speed: 2319 MHz
    Status: Populated, Enabled
    Upgrade: ZIF Socket

_**Memory Device**_
    Size: 4096 MB
    Form Factor: SODIMM
    Locator: DIMM0
    Bank Locator: BANK 0
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1333 MHz


_**Memory Device**_
    Size: 4096 MB
    Form Factor: SODIMM
    Locator: DIMM0
    Bank Locator: BANK 1
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1333 MHz

---

### Post by Daniel_Lopez on 2014-02-28
[U][B]Sony Vaio SVE15122CXW
[/B][/U]i3-3110M 2.4ghz (locked @ 2.4ghz durring test)
8gb pc3-12800
HD 4000
UbuntuStudio 13.10
3.11.0-17-lowlatency (kernel)
Desktop Environment running (Xfce)
**"i915.powesave=0" added to grub parameters** 

```
$ lspci | grep "VGA"00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
```

800x600

```
$ glmark2
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) Ivybridge Mobile 
    GL_VERSION:    3.0 Mesa 9.2.1
=======================================================
[build] use-vbo=false: FPS: 2194 FrameTime: 0.456 ms
[build] use-vbo=true: FPS: 2365 FrameTime: 0.423 ms
[texture] texture-filter=nearest: FPS: 2654 FrameTime: 0.377 ms
[texture] texture-filter=linear: FPS: 2609 FrameTime: 0.383 ms
[texture] texture-filter=mipmap: FPS: 2576 FrameTime: 0.388 ms
[shading] shading=gouraud: FPS: 1711 FrameTime: 0.584 ms
[shading] shading=blinn-phong-inf: FPS: 1721 FrameTime: 0.581 ms
[shading] shading=phong: FPS: 1687 FrameTime: 0.593 ms
[bump] bump-render=high-poly: FPS: 723 FrameTime: 1.383 ms
[bump] bump-render=normals: FPS: 2950 FrameTime: 0.339 ms
[bump] bump-render=height: FPS: 2700 FrameTime: 0.370 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 1340 FrameTime: 0.746 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 644 FrameTime: 1.553 ms
[pulsar] light=false:quads=5:texture=false: FPS: 2237 FrameTime: 0.447 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 616 FrameTime: 1.623 ms
[desktop] effect=shadow:windows=4: FPS: 1136 FrameTime: 0.880 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 541 FrameTime: 1.848 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 613 FrameTime: 1.631 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 607 FrameTime: 1.647 ms
[ideas] speed=duration: FPS: 1401 FrameTime: 0.714 ms
[jellyfish] <default>: FPS: 1056 FrameTime: 0.947 ms
[terrain] <default>: FPS: 123 FrameTime: 8.130 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 2451 FrameTime: 0.408 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 2565 FrameTime: 0.390 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 2453 FrameTime: 0.408 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 2485 FrameTime: 0.402 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 2611 FrameTime: 0.383 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 2472 FrameTime: 0.405 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 2475 FrameTime: 0.404 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 2570 FrameTime: 0.389 ms
=======================================================
                                  glmark2 Score: 1809 
=======================================================
```

1366x768

```
$ glmark2 --fullscreen
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) Ivybridge Mobile 
    GL_VERSION:    3.0 Mesa 9.2.1
=======================================================
[build] use-vbo=false: FPS: 1099 FrameTime: 0.910 ms
[build] use-vbo=true: FPS: 1187 FrameTime: 0.842 ms
[texture] texture-filter=nearest: FPS: 1193 FrameTime: 0.838 ms
[texture] texture-filter=linear: FPS: 1184 FrameTime: 0.845 ms
[texture] texture-filter=mipmap: FPS: 1164 FrameTime: 0.859 ms
[shading] shading=gouraud: FPS: 965 FrameTime: 1.036 ms
[shading] shading=blinn-phong-inf: FPS: 967 FrameTime: 1.034 ms
[shading] shading=phong: FPS: 962 FrameTime: 1.040 ms
[bump] bump-render=high-poly: FPS: 539 FrameTime: 1.855 ms
[bump] bump-render=normals: FPS: 1247 FrameTime: 0.802 ms
[bump] bump-render=height: FPS: 1176 FrameTime: 0.850 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 590 FrameTime: 1.695 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 309 FrameTime: 3.236 ms
[pulsar] light=false:quads=5:texture=false: FPS: 990 FrameTime: 1.010 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 310 FrameTime: 3.226 ms
[desktop] effect=shadow:windows=4: FPS: 525 FrameTime: 1.905 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 471 FrameTime: 2.123 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 532 FrameTime: 1.880 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 527 FrameTime: 1.898 ms
[ideas] speed=duration: FPS: 883 FrameTime: 1.133 ms
[jellyfish] <default>: FPS: 558 FrameTime: 1.792 ms
[terrain] <default>: FPS: 74 FrameTime: 13.514 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 1064 FrameTime: 0.940 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 1111 FrameTime: 0.900 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 1062 FrameTime: 0.942 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 1071 FrameTime: 0.934 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 1096 FrameTime: 0.912 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 1071 FrameTime: 0.934 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 1070 FrameTime: 0.935 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 1112 FrameTime: 0.899 ms
=======================================================
                                  glmark2 Score: 870 
=======================================================
```

Disabling power-save is crucial on mobile systems.
Unfortunately, balancing load and Intel Dynamic Frequency is difficult on this machine, so, the iGPU didn't keep at full speed (1000mhz).

---

### Post by juin-roet on 2014-06-10
Ubuntu 14.04 64 bit
VGA - **Radeon R7 265** [Gallium 0.4 on AMD PITCAIRN]  
RAM - Corsair Vengeance DDR3 2x4 8 GB 
MOBO - ASUS M5 A99FX PRO R2.0 (Factory bios I think, haven't messed with it if that matters)
CPU - AMD FX(tm)-8350 Eight-Core Processor × 8

No overclocking, in desktop environment, also I just used the standard test not full screen: unsure about dimensions. 

X.org Driver
```
   
======================================================= 
     glmark2 2012.08  
 ======================================================= 
     OpenGL Information  
     GL_VENDOR:     X.Org  
     GL_RENDERER:   Gallium 0.4 on AMD PITCAIRN  
     GL_VERSION:    3.0 Mesa 10.1.3  
 ======================================================= 
 [build] use-vbo=false: FPS: 2670 FrameTime: 0.375 ms  
 [build] use-vbo=true: FPS: 3644 FrameTime: 0.274 ms  
 [texture] texture-filter=nearest: FPS: 3596 FrameTime: 0.278 ms  
 [texture] texture-filter=linear: FPS: 3607 FrameTime: 0.277 ms  
 [texture] texture-filter=mipmap: FPS: 3568 FrameTime: 0.280 ms  
 [shading] shading=gouraud: FPS: 3628 FrameTime: 0.276 ms  
 [shading] shading=blinn-phong-inf: FPS: 3685 FrameTime: 0.271 ms  
 [shading] shading=phong: FPS: 3588 FrameTime: 0.279 ms  
 [bump] bump-render=high-poly: FPS: 3007 FrameTime: 0.333 ms  
 [bump] bump-render=normals: FPS: 3588 FrameTime: 0.279 ms  
 [bump] bump-render=height: FPS: 3595 FrameTime: 0.278 ms  
 [effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 3733 FrameTime: 0.268 ms  
 [effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 3140 FrameTime: 0.318 ms  
 [pulsar] light=false:quads=5:texture=false: FPS: 3243 FrameTime: 0.308 ms  
 [desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 1668 FrameTime: 0.600 ms  
 [desktop] effect=shadow:windows=4: FPS: 1659 FrameTime: 0.603 ms  
 [buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 399 FrameTime: 2.506 ms  
 [buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 802 FrameTime: 1.247 ms  
 [buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 459 FrameTime: 2.179 ms  
 [ideas] speed=duration: FPS: 794 FrameTime: 1.259 ms  
 [jellyfish] <default>: FPS: 3228 FrameTime: 0.310 ms  
 [terrain] <default>: FPS: 421 FrameTime: 2.375 ms  
 [conditionals] fragment-steps=0:vertex-steps=0: FPS: 3754 FrameTime: 0.266 ms  
 [conditionals] fragment-steps=5:vertex-steps=0: FPS: 3776 FrameTime: 0.265 ms  
 [conditionals] fragment-steps=0:vertex-steps=5: FPS: 3775 FrameTime: 0.265 ms  
 [function] fragment-complexity=low:fragment-steps=5: FPS: 3843 FrameTime: 0.260 ms  
 [function] fragment-complexity=medium:fragment-steps=5: FPS: 3822 FrameTime: 0.262 ms  
 [loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 3747 FrameTime: 0.267 ms  
 [loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 3742 FrameTime: 0.267 ms  
 [loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 3827 FrameTime: 0.261 ms  
 ======================================================= 
                                   glmark2 Score: 2933  
 ======================================================= 


```

Flgrx Driver: Video Hardware Accelleration Enabled
```
   
======================================================= 
     OpenGL Information 
     GL_VENDOR:     ATI Technologies Inc. 
     GL_RENDERER:   AMD Radeon R7 200 Series          
     GL_VERSION:    4.3.12798 Compatibility Profile Context 13.35.1005 
 ======================================================= 
 [build] use-vbo=false: FPS: 3121 FrameTime: 0.320 ms 
 [build] use-vbo=true: FPS: 6879 FrameTime: 0.145 ms 
 [texture] texture-filter=nearest: FPS: 6772 FrameTime: 0.148 ms 
 [texture] texture-filter=linear: FPS: 6675 FrameTime: 0.150 ms 
 [texture] texture-filter=mipmap: FPS: 6816 FrameTime: 0.147 ms 
 [shading] shading=gouraud: FPS: 6744 FrameTime: 0.148 ms 
 [shading] shading=blinn-phong-inf: FPS: 6807 FrameTime: 0.147 ms 
 [shading] shading=phong: FPS: 6857 FrameTime: 0.146 ms 
 [bump] bump-render=high-poly: FPS: 4259 FrameTime: 0.235 ms 
 [bump] bump-render=normals: FPS: 6733 FrameTime: 0.149 ms 
 [bump] bump-render=height: FPS: 6643 FrameTime: 0.151 ms 
 [effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 4417 FrameTime: 0.226 ms 
 [effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 3869 FrameTime: 0.258 ms 
 [pulsar] light=false:quads=5:texture=false: FPS: 5932 FrameTime: 0.169 ms 
 [desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 1386 FrameTime: 0.722 ms 
 [desktop] effect=shadow:windows=4: FPS: 1454 FrameTime: 0.688 ms 
 [buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 373 FrameTime: 2.681 ms 
 [buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1015 FrameTime: 0.985 ms 
 [buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 431 FrameTime: 2.320 ms 
 [ideas] speed=duration: FPS: 2804 FrameTime: 0.357 ms 
 [jellyfish] <default>: FPS: 5055 FrameTime: 0.198 ms 
 [terrain] <default>: FPS: 603 FrameTime: 1.658 ms 

 [conditionals] fragment-steps=0:vertex-steps=0: FPS: 6720 FrameTime: 0.149 ms 
 [conditionals] fragment-steps=5:vertex-steps=0: FPS: 6804 FrameTime: 0.147 ms 
 [conditionals] fragment-steps=0:vertex-steps=5: FPS: 6700 FrameTime: 0.149 ms 
 [function] fragment-complexity=low:fragment-steps=5: FPS: 6711 FrameTime: 0.149 ms 
 [function] fragment-complexity=medium:fragment-steps=5: FPS: 6834 FrameTime: 0.146 ms 
 [loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 6814 FrameTime: 0.147 ms 
 [loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 6923 FrameTime: 0.144 ms 
 [loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 6659 FrameTime: 0.150 ms 
 ======================================================= 
                                   glmark2 Score: 4993  
 ======================================================= 


```

---

### Post by aramil248 on 2014-06-12
so i installed glmark2 and when i run glmark2 i get this error ```
aramil@aramil-desktop:~$ glmark2Inconsistency detected by ld.so: dl-version.c: 224: _dl_check_map_versions: Assertion `needed != ((void *)0)' failed!



```

---

### Post by dannyboy79 on 2014-06-12
> **aramil248 said:**
> so i installed glmark2 and when i run glmark2 i get this error ```
aramil@aramil-desktop:~$ glmark2Inconsistency detected by ld.so: dl-version.c: 224: _dl_check_map_versions: Assertion `needed != ((void *)0)' failed!



```
i know you've been messing around with drivers, are you sure you completely uninstalled the nvidia website driver? it's possible it didn't uninstall all it's files and left some leaving you in a bad state. i wish i could point you in a direction to investigate but i have no idea where to start. there's a lot of dependencies and libraries for graphics drivers.

---

### Post by martin-wangel on 2014-08-18
> **Ranko Kohime said:**
> 

I noticed you have no gtx750 in your list. This is run on top of the full ubuntu/unity stack with a 1GB EVGA GTX750 SC:

[COLOR=#500050][FONT=arial]=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
[/FONT][/COLOR]
[FONT=arial]    GL_RENDERER:   GeForce GTX 750/PCIe/SSE2[/FONT]
[FONT=arial]    GL_VERSION:    4.4.0 NVIDIA 340.32[/FONT]
[FONT=arial]==============================[/FONT][FONT=arial]=========================[/FONT]
[FONT=arial][build] use-vbo=false: FPS: 6568 FrameTime: 0.152 ms[/FONT]
[FONT=arial][build] use-vbo=true: FPS: 10563 FrameTime: 0.095 ms[/FONT]
[FONT=arial][texture] texture-filter=nearest: FPS: 9635 FrameTime: 0.104 ms[/FONT]
[FONT=arial][texture] texture-filter=linear: FPS: 9630 FrameTime: 0.104 ms[/FONT]
[FONT=arial][texture] texture-filter=mipmap: FPS: 9611 FrameTime: 0.104 ms[/FONT]
[FONT=arial][shading] shading=gouraud: FPS: 9074 FrameTime: 0.110 ms[/FONT]
[FONT=arial][shading] shading=blinn-phong-inf: FPS: 9069 FrameTime: 0.110 ms[/FONT]
[FONT=arial][shading] shading=phong: FPS: 8318 FrameTime: 0.120 ms[/FONT]
[FONT=arial][bump] bump-render=high-poly: FPS: 5942 FrameTime: 0.168 ms[/FONT]
[FONT=arial][bump] bump-render=normals: FPS: 10527 FrameTime: 0.095 ms[/FONT]
[FONT=arial][bump] bump-render=height: FPS: 10327 FrameTime: 0.097 ms[/FONT]
[FONT=arial][effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 6769 FrameTime: 0.148 ms[/FONT]
[FONT=arial][effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,[/FONT][FONT=arial]1,1,1,1;: FPS: 3780 FrameTime: 0.265 ms[/FONT]
[FONT=arial][pulsar] light=false:quads=5:texture=[/FONT][FONT=arial]false: FPS: 9674 FrameTime: 0.103 ms[/FONT]
[FONT=arial][desktop] blur-radius=5:effect=blur:[/FONT][FONT=arial]passes=1:separable=true:[/FONT][FONT=arial]windows=4: FPS: 3131 FrameTime: 0.319 ms[/FONT]
[FONT=arial][desktop] effect=shadow:windows=4: FPS: 5654 FrameTime: 0.177 ms[/FONT]
[FONT=arial][buffer] columns=200:interleave=false:[/FONT][FONT=arial]update-dispersion=0.9:update-[/FONT][FONT=arial]fraction=0.5:update-method=[/FONT][FONT=arial]map: FPS: 1152 FrameTime: 0.868 ms[/FONT]
[FONT=arial][buffer] columns=200:interleave=false:[/FONT][FONT=arial]update-dispersion=0.9:update-[/FONT][FONT=arial]fraction=0.5:update-method=[/FONT][FONT=arial]subdata: FPS: 1366 FrameTime: 0.732 ms[/FONT]
[FONT=arial][buffer] columns=200:interleave=true:[/FONT][FONT=arial]update-dispersion=0.9:update-[/FONT][FONT=arial]fraction=0.5:update-method=[/FONT][FONT=arial]map: FPS: 1211 FrameTime: 0.826 ms[/FONT]
[FONT=arial][ideas] speed=duration: FPS: 8130 FrameTime: 0.123 ms[/FONT]
[FONT=arial][jellyfish] <default>: FPS: 5772 FrameTime: 0.173 ms[/FONT]
[FONT=arial][terrain] <default>: FPS: 623 FrameTime: 1.605 ms[/FONT]
[FONT=arial][conditionals] fragment-steps=0:vertex-steps=[/FONT][FONT=arial]0: FPS: 9242 FrameTime: 0.108 ms[/FONT]
[FONT=arial][conditionals] fragment-steps=5:vertex-steps=[/FONT][FONT=arial]0: FPS: 8496 FrameTime: 0.118 ms[/FONT]
[FONT=arial][conditionals] fragment-steps=0:vertex-steps=[/FONT][FONT=arial]5: FPS: 9202 FrameTime: 0.109 ms[/FONT]
[FONT=arial][function] fragment-complexity=low:[/FONT][FONT=arial]fragment-steps=5: FPS: 9147 FrameTime: 0.109 ms[/FONT]
[FONT=arial][function] fragment-complexity=medium:[/FONT][FONT=arial]fragment-steps=5: FPS: 7936 FrameTime: 0.126 ms[/FONT]
[FONT=arial][loop] fragment-loop=false:fragment-[/FONT][FONT=arial]steps=5:vertex-steps=5: FPS: 9146 FrameTime: 0.109 ms[/FONT]
[FONT=arial][loop] fragment-steps=5:fragment-[/FONT][FONT=arial]uniform=false:vertex-steps=5: FPS: 9126 FrameTime: 0.110 ms[/FONT]
[FONT=arial][loop] fragment-steps=5:fragment-[/FONT][FONT=arial]uniform=true:vertex-steps=5: FPS: 8462 FrameTime: 0.118 ms[/FONT]
[FONT=arial]==============================[/FONT][FONT=arial]=========================[/FONT]
[FONT=arial]                              [/FONT][FONT=arial]    glmark2 Score: 7242 [/FONT]
[FONT=arial]==============================[/FONT][FONT=arial]=========================
[/FONT]

---

### Post by oldrocker99 on 2014-08-18
I have a 650ti, and the 750 is twice as fast and uses half the power. Next on my NewEgg purchases, for sure.

---

### Post by JDorfler on 2014-08-19
```
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   AMD Radeon HD 6900M Series
    GL_VERSION:    4.4.12967 Compatibility Profile Context 13.35.1005
=======================================================
[build] use-vbo=false: FPS: 4114 FrameTime: 0.243 ms
[build] use-vbo=true: FPS: 5510 FrameTime: 0.181 ms
[texture] texture-filter=nearest: FPS: 5400 FrameTime: 0.185 ms
[texture] texture-filter=linear: FPS: 5399 FrameTime: 0.185 ms
[texture] texture-filter=mipmap: FPS: 5429 FrameTime: 0.184 ms
[shading] shading=gouraud: FPS: 4773 FrameTime: 0.210 ms
[shading] shading=blinn-phong-inf: FPS: 4732 FrameTime: 0.211 ms
[shading] shading=phong: FPS: 4324 FrameTime: 0.231 ms
[bump] bump-render=high-poly: FPS: 2782 FrameTime: 0.359 ms
[bump] bump-render=normals: FPS: 5263 FrameTime: 0.190 ms
[bump] bump-render=height: FPS: 4973 FrameTime: 0.201 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 1502 FrameTime: 0.666 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 948 FrameTime: 1.055 ms
[pulsar] light=false:quads=5:texture=false: FPS: 4773 FrameTime: 0.210 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 1022 FrameTime: 0.978 ms
[desktop] effect=shadow:windows=4: FPS: 1058 FrameTime: 0.945 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 749 FrameTime: 1.335 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 979 FrameTime: 1.021 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 861 FrameTime: 1.161 ms
[ideas] speed=duration: FPS: 2844 FrameTime: 0.352 ms
[jellyfish] <default>: FPS: 3001 FrameTime: 0.333 ms
[terrain] <default>: FPS: 210 FrameTime: 4.762 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 5081 FrameTime: 0.197 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 4257 FrameTime: 0.235 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 5063 FrameTime: 0.198 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 4855 FrameTime: 0.206 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 3393 FrameTime: 0.295 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 4797 FrameTime: 0.208 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 4805 FrameTime: 0.208 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 3465 FrameTime: 0.289 ms
=======================================================
                                  glmark2 Score: 3545 
=======================================================

```

That's my laptop at Fullscreen.  I'll post on my desktop when I get home.  Have a 290X overclocked coming.  So I'll post that as well.

---

### Post by dradius on 2014-08-24
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 660 Ti/PCIe/SSE2
    GL_VERSION:    4.4.0 NVIDIA 331.38
=======================================================
[build] use-vbo=false: FPS: 4756 FrameTime: 0.210 ms
[build] use-vbo=true: FPS: 12985 FrameTime: 0.077 ms
[texture] texture-filter=nearest: FPS: 10841 FrameTime: 0.092 ms
[texture] texture-filter=linear: FPS: 10846 FrameTime: 0.092 ms
[texture] texture-filter=mipmap: FPS: 11476 FrameTime: 0.087 ms
[shading] shading=gouraud: FPS: 10943 FrameTime: 0.091 ms
[shading] shading=blinn-phong-inf: FPS: 10394 FrameTime: 0.096 ms
[shading] shading=phong: FPS: 10880 FrameTime: 0.092 ms
[bump] bump-render=high-poly: FPS: 8198 FrameTime: 0.122 ms
[bump] bump-render=normals: FPS: 12701 FrameTime: 0.079 ms
[bump] bump-render=height: FPS: 12505 FrameTime: 0.080 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 9044 FrameTime: 0.111 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 6711 FrameTime: 0.149 ms
[pulsar] light=false:quads=5:texture=false: FPS: 11240 FrameTime: 0.089 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 3713 FrameTime: 0.269 ms
[desktop] effect=shadow:windows=4: FPS: 4988 FrameTime: 0.200 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 602 FrameTime: 1.661 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 683 FrameTime: 1.464 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 738 FrameTime: 1.355 ms
[ideas] speed=duration: FPS: 8465 FrameTime: 0.118 ms
[jellyfish] <default>: FPS: 6130 FrameTime: 0.163 ms
[terrain] <default>: FPS: 721 FrameTime: 1.387 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 10564 FrameTime: 0.095 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 10390 FrameTime: 0.096 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 10532 FrameTime: 0.095 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 10456 FrameTime: 0.096 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 10442 FrameTime: 0.096 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 10497 FrameTime: 0.095 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 10505 FrameTime: 0.095 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 10459 FrameTime: 0.096 ms
=======================================================
                                  glmark2 Score: 8446 
=======================================================

---

### Post by bizhat on 2014-08-25
@martin-wangel Thank you very much for posting GTX 750 Ti result. I will be gettingit shortly (or a GTX 800).

Here is my Radeon HD 5670 512 MB card performance on Ubuntu 14.04 unity.

```

boby@fwhlin:~$ glmark2
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     X.Org
    GL_RENDERER:   Gallium 0.4 on AMD REDWOOD
    GL_VERSION:    3.0 Mesa 10.1.3
=======================================================
[build] use-vbo=false: FPS: 1478 FrameTime: 0.677 ms
[build] use-vbo=true: FPS: 1684 FrameTime: 0.594 ms
[texture] texture-filter=nearest: FPS: 1626 FrameTime: 0.615 ms
[texture] texture-filter=linear: FPS: 1621 FrameTime: 0.617 ms
[texture] texture-filter=mipmap: FPS: 1649 FrameTime: 0.606 ms
[shading] shading=gouraud: FPS: 1589 FrameTime: 0.629 ms
[shading] shading=blinn-phong-inf: FPS: 1588 FrameTime: 0.630 ms
[shading] shading=phong: FPS: 1570 FrameTime: 0.637 ms
[bump] bump-render=high-poly: FPS: 1320 FrameTime: 0.758 ms
[bump] bump-render=normals: FPS: 1699 FrameTime: 0.589 ms
[bump] bump-render=height: FPS: 1685 FrameTime: 0.593 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 1482 FrameTime: 0.675 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 996 FrameTime: 1.004 ms
[pulsar] light=false:quads=5:texture=false: FPS: 1485 FrameTime: 0.673 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 914 FrameTime: 1.094 ms
[desktop] effect=shadow:windows=4: FPS: 1223 FrameTime: 0.818 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 454 FrameTime: 2.203 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 678 FrameTime: 1.475 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 481 FrameTime: 2.079 ms
[ideas] speed=duration: FPS: 890 FrameTime: 1.124 ms
[jellyfish] <default>: FPS: 1316 FrameTime: 0.760 ms
[terrain] <default>: FPS: 231 FrameTime: 4.329 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 1506 FrameTime: 0.664 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 1506 FrameTime: 0.664 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 1506 FrameTime: 0.664 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 1506 FrameTime: 0.664 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 1420 FrameTime: 0.704 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 1505 FrameTime: 0.664 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 1507 FrameTime: 0.664 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 1082 FrameTime: 0.924 ms
=======================================================
                                  glmark2 Score: 1306 
=======================================================
boby@fwhlin:~$ 

```

glmark2 Score: 1306 
Test run on 1920x1080.
GPU: Sapphire HD 5670 512 MB

Can't wait to get GTX 750 Ti, that perform 5 to 6 times faster than my card. I see AMD doing good work on open source driver, so i do consider it too, but R9 285 power usage is almost same as R9 280, i need to save some electricity too.

---

### Post by belarrius on 2014-08-25
Ubuntu 14.04 trusty x86_64 (with Unity)

**Windowed**

=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 470/PCIe/SSE2
    GL_VERSION:    4.4.0 NVIDIA 343.13
=======================================================
=======================================================
                                  glmark2 Score: 5819 
=======================================================

[IMG]http://image.noelshack.com/fichiers/2014/35/1409013260-capture-du-2014-08-26-02-34-05.png[/IMG]

---

### Post by bizhat on 2014-08-26
@belarrius what resolution you tested in ?

---

### Post by belarrius on 2014-08-26
> **bizhat said:**
> @belarrius what resolution you tested in ?

Oops, sorry, it's Windowed. I have edited last post.

I try with Fullscreen now but... I have DualScreen and, this test use my two screens! lol

---

### Post by belarrius on 2014-08-26
Ubuntu 14.04 trusty x86_64 (with Unity)

**FullScreen - 1360x768**

==================================================  =====
    glmark2 2012.08
==================================================  =====
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 470/PCIe/SSE2
    GL_VERSION:    4.4.0 NVIDIA 343.13
==================================================  =====
==================================================  =====
                                  glmark2 Score: 4167
==================================================  =====
[IMG]http://image.noelshack.com/fichiers/2014/35/1409049427-fullscreen.png[/IMG]

---

### Post by belarrius on 2014-08-26
Ubuntu 14.04 trusty x86_64 (with Unity)

**FullScreen on DualScreen - 1360x768** **+ 1280x1024**

==================================================  =====
    glmark2 2012.08
==================================================  =====
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 470/PCIe/SSE2
    GL_VERSION:    4.4.0 NVIDIA 343.13
==================================================  =====
==================================================  =====
                                  glmark2 Score: 3317
==================================================  =====

[IMG]http://image.noelshack.com/fichiers/2014/35/1409049492-fullscreendualscreen.png[/IMG]

---

### Post by Keith_Beef on 2014-08-26
This is my system built in 2007, and with the graphics card updated today.

CPU: Intel Q9650
RAM: Mushkin 8GB DDR2-1066 
Graphics card: PNY nVidia Quadro K2000D

Running windowed (800 × 600)
```
=======================================================
    glmark2 2011.09
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   Quadro K2000D/PCIe/SSE2
    GL_VERSION:    4.4.0 NVIDIA 331.20
=======================================================
[build] use-vbo=false:  FPS: 3219
[build] use-vbo=true:  FPS: 7401
[texture] texture-filter=nearest:  FPS: 6713
[texture] texture-filter=linear:  FPS: 6181
[texture] texture-filter=mipmap:  FPS: 6883
[shading] shading=gouraud:  FPS: 5282
[shading] shading=blinn-phong-inf:  FPS: 5292
[shading] shading=phong:  FPS: 5028
[bump] bump-render=high-poly:  FPS: 3261
[bump] bump-render=normals:  FPS: 6440
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;:  FPS: 4126
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;:  FPS: 2191
[pulsar] light=false:quads=5:texture=false:  FPS: 5395
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4:  FPS: 1861
[conditionals] fragment-steps=0:vertex-steps=0:  FPS: 5664
[conditionals] fragment-steps=5:vertex-steps=0:  FPS: 4936
[conditionals] fragment-steps=0:vertex-steps=5:  FPS: 5664
[function] fragment-complexity=low:fragment-steps=5:  FPS: 5651
[function] fragment-complexity=medium:fragment-steps=5:  FPS: 4880
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5:  FPS: 5655
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5:  FPS: 5652
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5:  FPS: 5053
=======================================================
                                  glmark2 Score: 5110 
=======================================================
```

I didn't see a full-screen option, so ran with the size set to my screen resolution

```
glmark2 --size 1680x1050
=======================================================
    glmark2 2011.09
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   Quadro K2000D/PCIe/SSE2
    GL_VERSION:    4.4.0 NVIDIA 331.20
=======================================================
[build] use-vbo=false:  FPS: 2170
[build] use-vbo=true:  FPS: 3017
[texture] texture-filter=nearest:  FPS: 2882
[texture] texture-filter=linear:  FPS: 2874
[texture] texture-filter=mipmap:  FPS: 2917
[shading] shading=gouraud:  FPS: 2538
[shading] shading=blinn-phong-inf:  FPS: 2539
[shading] shading=phong:  FPS: 2392
[bump] bump-render=high-poly:  FPS: 2074
[bump] bump-render=normals:  FPS: 2761
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;:  FPS: 1529
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;:  FPS: 734
[pulsar] light=false:quads=5:texture=false:  FPS: 2200
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4:  FPS: 685
[conditionals] fragment-steps=0:vertex-steps=0:  FPS: 2374
[conditionals] fragment-steps=5:vertex-steps=0:  FPS: 2024
[conditionals] fragment-steps=0:vertex-steps=5:  FPS: 2376
[function] fragment-complexity=low:fragment-steps=5:  FPS: 2353
[function] fragment-complexity=medium:fragment-steps=5:  FPS: 1997
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5:  FPS: 2354
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5:  FPS: 2354
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5:  FPS: 2080
=======================================================
                                  glmark2 Score: 2237 
=======================================================
```

---

### Post by oldrocker99 on 2014-09-11
Update for me. Just got a nVidia 750ti. This is fullscreen at 1920x1080:
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 750 Ti/PCIe/SSE2
    GL_VERSION:    4.4.0 NVIDIA 343.13
=======================================================
[build] use-vbo=false: FPS: 3529 FrameTime: 0.283 ms
[build] use-vbo=true: FPS: 4738 FrameTime: 0.211 ms
[texture] texture-filter=nearest: FPS: 4739 FrameTime: 0.211 ms                                                                                                                    
[texture] texture-filter=linear: FPS: 4737 FrameTime: 0.211 ms                                                                                                                     
[texture] texture-filter=mipmap: FPS: 4738 FrameTime: 0.211 ms                                                                                                                     
[shading] shading=gouraud: FPS: 4215 FrameTime: 0.237 ms                                                                                                                           
[shading] shading=blinn-phong-inf: FPS: 4281 FrameTime: 0.234 ms                                                                                                                   
[shading] shading=phong: FPS: 3676 FrameTime: 0.272 ms                                                                                                                             
[bump] bump-render=high-poly: FPS: 3474 FrameTime: 0.288 ms                                                                                                                        
[bump] bump-render=normals: FPS: 5356 FrameTime: 0.187 ms
[bump] bump-render=height: FPS: 5163 FrameTime: 0.194 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 3081 FrameTime: 0.325 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 1639 FrameTime: 0.610 ms
[pulsar] light=false:quads=5:texture=false: FPS: 4748 FrameTime: 0.211 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 1541 FrameTime: 0.649 ms
[desktop] effect=shadow:windows=4: FPS: 2331 FrameTime: 0.429 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 644 FrameTime: 1.553 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 776 FrameTime: 1.289 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 834 FrameTime: 1.199 ms
[ideas] speed=duration: FPS: 4182 FrameTime: 0.239 ms
[jellyfish] <default>: FPS: 3125 FrameTime: 0.320 ms
[terrain] <default>: FPS: 389 FrameTime: 2.571 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 4981 FrameTime: 0.201 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 4726 FrameTime: 0.212 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 4934 FrameTime: 0.203 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 4914 FrameTime: 0.204 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 4693 FrameTime: 0.213 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 4919 FrameTime: 0.203 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 4920 FrameTime: 0.203 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 4721 FrameTime: 0.212 ms
=======================================================
                                  glmark2 Score: 3691 
=======================================================

---

### Post by ilpiero on 2014-09-12
```
glmark2 --fullscreen
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   AMD Radeon HD 8570D
    GL_VERSION:    4.2.12337 Compatibility Profile Context 13.101
=======================================================
[build] use-vbo=false: FPS: 59 FrameTime: 16.949 ms
[build] use-vbo=true: FPS: 60 FrameTime: 16.667 ms
[texture] texture-filter=nearest: FPS: 60 FrameTime: 16.667 ms
[texture] texture-filter=linear: FPS: 59 FrameTime: 16.949 ms
[texture] texture-filter=mipmap: FPS: 59 FrameTime: 16.949 ms
[shading] shading=gouraud: FPS: 60 FrameTime: 16.667 ms
[shading] shading=blinn-phong-inf: FPS: 60 FrameTime: 16.667 ms
[shading] shading=phong: FPS: 60 FrameTime: 16.667 ms
[bump] bump-render=high-poly: FPS: 60 FrameTime: 16.667 ms
[bump] bump-render=normals: FPS: 60 FrameTime: 16.667 ms
[bump] bump-render=height: FPS: 60 FrameTime: 16.667 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 60 FrameTime: 16.667 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 60 FrameTime: 16.667 ms
[pulsar] light=false:quads=5:texture=false: FPS: 60 FrameTime: 16.667 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 60 FrameTime: 16.667 ms
[desktop] effect=shadow:windows=4: FPS: 60 FrameTime: 16.667 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 59 FrameTime: 16.949 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 60 FrameTime: 16.667 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 59 FrameTime: 16.949 ms
[ideas] speed=duration: FPS: 60 FrameTime: 16.667 ms
[jellyfish] <default>: FPS: 60 FrameTime: 16.667 ms
[terrain] <default>: FPS: 51 FrameTime: 19.608 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 60 FrameTime: 16.667 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 60 FrameTime: 16.667 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 60 FrameTime: 16.667 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 60 FrameTime: 16.667 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 60 FrameTime: 16.667 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 60 FrameTime: 16.667 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 60 FrameTime: 16.667 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 60 FrameTime: 16.667 ms
=======================================================
                                  glmark2 Score: 59 
=======================================================
```



err...  59 with an AMD A8 6600K APU (AMD Radeon HD 8570D). fullscreen. 
Have i cheked the "lousy performance" flag somewhere?

---

### Post by sffvba[e0rt on 2014-09-12
Ubuntu 14.04.1 running Unity, ran in terminal at a resolution of 1920x1080 on a GTX770: 5493

---

### Post by dannyboy79 on 2014-09-13
> **oldrocker99 said:**
> Update for me. Just got a nVidia 750ti. This is fullscreen at 1920x1080:
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 750 Ti/PCIe/SSE2
    GL_VERSION:    4.4.0 NVIDIA 343.13
=======================================================
[build] use-vbo=false: FPS: 3529 FrameTime: 0.283 ms
[build] use-vbo=true: FPS: 4738 FrameTime: 0.211 ms
[texture] texture-filter=nearest: FPS: 4739 FrameTime: 0.211 ms                                                                                                                    
[texture] texture-filter=linear: FPS: 4737 FrameTime: 0.211 ms                                                                                                                     
[texture] texture-filter=mipmap: FPS: 4738 FrameTime: 0.211 ms                                                                                                                     
[shading] shading=gouraud: FPS: 4215 FrameTime: 0.237 ms                                                                                                                           
[shading] shading=blinn-phong-inf: FPS: 4281 FrameTime: 0.234 ms                                                                                                                   
[shading] shading=phong: FPS: 3676 FrameTime: 0.272 ms                                                                                                                             
[bump] bump-render=high-poly: FPS: 3474 FrameTime: 0.288 ms                                                                                                                        
[bump] bump-render=normals: FPS: 5356 FrameTime: 0.187 ms
[bump] bump-render=height: FPS: 5163 FrameTime: 0.194 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 3081 FrameTime: 0.325 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 1639 FrameTime: 0.610 ms
[pulsar] light=false:quads=5:texture=false: FPS: 4748 FrameTime: 0.211 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 1541 FrameTime: 0.649 ms
[desktop] effect=shadow:windows=4: FPS: 2331 FrameTime: 0.429 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 644 FrameTime: 1.553 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 776 FrameTime: 1.289 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 834 FrameTime: 1.199 ms
[ideas] speed=duration: FPS: 4182 FrameTime: 0.239 ms
[jellyfish] <default>: FPS: 3125 FrameTime: 0.320 ms
[terrain] <default>: FPS: 389 FrameTime: 2.571 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 4981 FrameTime: 0.201 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 4726 FrameTime: 0.212 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 4934 FrameTime: 0.203 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 4914 FrameTime: 0.204 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 4693 FrameTime: 0.213 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 4919 FrameTime: 0.203 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 4920 FrameTime: 0.203 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 4721 FrameTime: 0.212 ms
=======================================================
                                  glmark2 Score: 3691 
=======================================================
something isn't right on my end and I don't know what. I ran it on my GTX 760 which is running Nvidia 340.32 and I'm only getting 1464. What's up with that do you know??
```
glmark2 -s 1920x1080
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 760/PCIe/SSE2
    GL_VERSION:    4.4.0 NVIDIA 340.32
=======================================================
[build] use-vbo=false: FPS: 1874 FrameTime: 0.534 ms
[build] use-vbo=true: FPS: 1885 FrameTime: 0.531 ms
[texture] texture-filter=nearest: FPS: 1592 FrameTime: 0.628 ms
[texture] texture-filter=linear: FPS: 1648 FrameTime: 0.607 ms
[texture] texture-filter=mipmap: FPS: 1655 FrameTime: 0.604 ms
[shading] shading=gouraud: FPS: 2495 FrameTime: 0.401 ms
[shading] shading=blinn-phong-inf: FPS: 2076 FrameTime: 0.482 ms
[shading] shading=phong: FPS: 2336 FrameTime: 0.428 ms
[bump] bump-render=high-poly: FPS: 1997 FrameTime: 0.501 ms
[bump] bump-render=normals: FPS: 1992 FrameTime: 0.502 ms
[bump] bump-render=height: FPS: 1977 FrameTime: 0.506 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 1511 FrameTime: 0.662 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 1187 FrameTime: 0.842 ms
[pulsar] light=false:quads=5:texture=false: FPS: 1644 FrameTime: 0.608 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 961 FrameTime: 1.041 ms
[desktop] effect=shadow:windows=4: FPS: 1152 FrameTime: 0.868 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 890 FrameTime: 1.124 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1116 FrameTime: 0.896 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 943 FrameTime: 1.060 ms
[ideas] speed=duration: FPS: 1767 FrameTime: 0.566 ms
[jellyfish] <default>: FPS: 1254 FrameTime: 0.797 ms
[terrain] <default>: FPS: 353 FrameTime: 2.833 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 1302 FrameTime: 0.768 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 1146 FrameTime: 0.873 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 1305 FrameTime: 0.766 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 1179 FrameTime: 0.848 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 1171 FrameTime: 0.854 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 1185 FrameTime: 0.844 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 1180 FrameTime: 0.847 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 1169 FrameTime: 0.855 ms
=======================================================
                                  glmark2 Score: 1464 
=======================================================

```

---

### Post by bizhat on 2014-09-14
Why don't you try latest NVIDIA driver ? I was looking for a GTX 760 score as i may be getting GTX 750 or a GTX 760 soon. Please post a benchmark  once you got it fixed :)

---

### Post by xc3RnbFO8P on 2014-09-14
Intel Core i3 4010U (1.7GHz)
4GB Memory 500GB HDD 8GB NAND Flash SSHD SSD
Intel HD Graphics 4400
Touchscreen 1366 x 768


```
ringi@ringi-Lenovo-Ideapad-Flex-15:~$ glmark2
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) Haswell Mobile 
    GL_VERSION:    3.0 Mesa 10.2.2
=======================================================
[build] use-vbo=false: FPS: 1382 FrameTime: 0.724 ms
[build] use-vbo=true: FPS: 1537 FrameTime: 0.651 ms
[texture] texture-filter=nearest: FPS: 1336 FrameTime: 0.749 ms
[texture] texture-filter=linear: FPS: 1332 FrameTime: 0.751 ms
[texture] texture-filter=mipmap: FPS: 1384 FrameTime: 0.723 ms
[shading] shading=gouraud: FPS: 1295 FrameTime: 0.772 ms
[shading] shading=blinn-phong-inf: FPS: 1311 FrameTime: 0.763 ms
[shading] shading=phong: FPS: 1304 FrameTime: 0.767 ms
[bump] bump-render=high-poly: FPS: 1042 FrameTime: 0.960 ms
[bump] bump-render=normals: FPS: 1508 FrameTime: 0.663 ms
[bump] bump-render=height: FPS: 1486 FrameTime: 0.673 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 1132 FrameTime: 0.883 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 603 FrameTime: 1.658 ms
[pulsar] light=false:quads=5:texture=false: FPS: 1336 FrameTime: 0.749 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 510 FrameTime: 1.961 ms
[desktop] effect=shadow:windows=4: FPS: 749 FrameTime: 1.335 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 456 FrameTime: 2.193 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 449 FrameTime: 2.227 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 501 FrameTime: 1.996 ms
[ideas] speed=duration: FPS: 1260 FrameTime: 0.794 ms
[jellyfish] <default>: FPS: 955 FrameTime: 1.047 ms
[terrain] <default>: FPS: 119 FrameTime: 8.403 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 1320 FrameTime: 0.758 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 1315 FrameTime: 0.760 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 1314 FrameTime: 0.761 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 1319 FrameTime: 0.758 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 1323 FrameTime: 0.756 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 1319 FrameTime: 0.758 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 1317 FrameTime: 0.759 ms                          
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 1312 FrameTime: 0.762 ms                           
=======================================================                                                               
                                  glmark2 Score: 1117                                                                 
======================================================= 

```


```
ringi@ringi-Lenovo-Ideapad-Flex-15:~$ glmark2 --fullscreen
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) Haswell Mobile 
    GL_VERSION:    3.0 Mesa 10.2.2
=======================================================
[build] use-vbo=false: FPS: 631 FrameTime: 1.585 ms
[build] use-vbo=true: FPS: 674 FrameTime: 1.484 ms
[texture] texture-filter=nearest: FPS: 625 FrameTime: 1.600 ms
[texture] texture-filter=linear: FPS: 621 FrameTime: 1.610 ms
[texture] texture-filter=mipmap: FPS: 630 FrameTime: 1.587 ms
[shading] shading=gouraud: FPS: 595 FrameTime: 1.681 ms
[shading] shading=blinn-phong-inf: FPS: 599 FrameTime: 1.669 ms
[shading] shading=phong: FPS: 596 FrameTime: 1.678 ms
[bump] bump-render=high-poly: FPS: 556 FrameTime: 1.799 ms
[bump] bump-render=normals: FPS: 665 FrameTime: 1.504 ms
[bump] bump-render=height: FPS: 663 FrameTime: 1.508 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 508 FrameTime: 1.969 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 273 FrameTime: 3.663 ms
[pulsar] light=false:quads=5:texture=false: FPS: 590 FrameTime: 1.695 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 258 FrameTime: 3.876 ms
[desktop] effect=shadow:windows=4: FPS: 337 FrameTime: 2.967 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 366 FrameTime: 2.732 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 366 FrameTime: 2.732 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 406 FrameTime: 2.463 ms
[ideas] speed=duration: FPS: 596 FrameTime: 1.678 ms
[jellyfish] <default>: FPS: 459 FrameTime: 2.179 ms
[terrain] <default>: FPS: 68 FrameTime: 14.706 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 561 FrameTime: 1.783 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 561 FrameTime: 1.783 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 562 FrameTime: 1.779 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 561 FrameTime: 1.783 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 561 FrameTime: 1.783 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 559 FrameTime: 1.789 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 561 FrameTime: 1.783 ms                           
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 540 FrameTime: 1.852 ms                            
=======================================================                                                               
                                  glmark2 Score: 518                                                                  
```
=======================================================

---

### Post by maxinstuff2 on 2014-09-15
My 2 week old scratch-build:
AMD r9270x (using v14.6 of the beta drivers)
Kubuntu 14.04.1 (disabled 3d accelleration in KDE before running this)
incidental - 8GB DDR3 ram, i5(K) Haswell refresh CPU

FYI - I was getting 58 - 60 every time until I switched off VSYNC in catalyst control centre.... Anti-tearing was on and "wait for vertical refresh" set to "Always" - limiting me to 60 fps! For those of you getting 55-60 score, you probably have VSYNC turned on.
 
Turning this off I re-ran the bechmark and was pleasantly surprised by the sound of my GPU's turbines audibly spinning up for the first time, and the gentle whistle of capacitors burning in :D

at fullscreen 1920x1080 -
```

max@max-Z87-D3HP:~$ glmark2 --fullscreen
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   AMD Radeon R9 200 Series
    GL_VERSION:    4.3.12798 Compatibility Profile Context 14.20
=======================================================
[build] use-vbo=false: FPS: 5404 FrameTime: 0.185 ms
[build] use-vbo=true: FPS: 11167 FrameTime: 0.090 ms
[texture] texture-filter=nearest: FPS: 9294 FrameTime: 0.108 ms
[texture] texture-filter=linear: FPS: 9289 FrameTime: 0.108 ms
[texture] texture-filter=mipmap: FPS: 9448 FrameTime: 0.106 ms
[shading] shading=gouraud: FPS: 9435 FrameTime: 0.106 ms
[shading] shading=blinn-phong-inf: FPS: 9427 FrameTime: 0.106 ms
[shading] shading=phong: FPS: 9115 FrameTime: 0.110 ms
[bump] bump-render=high-poly: FPS: 6880 FrameTime: 0.145 ms
[bump] bump-render=normals: FPS: 10789 FrameTime: 0.093 ms
[bump] bump-render=height: FPS: 10478 FrameTime: 0.095 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 3342 FrameTime: 0.299 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 2241 FrameTime: 0.446 ms
[pulsar] light=false:quads=5:texture=false: FPS: 6893 FrameTime: 0.145 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 2104 FrameTime: 0.475 ms
[desktop] effect=shadow:windows=4: FPS: 1779 FrameTime: 0.562 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 746 FrameTime: 1.340 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1032 FrameTime: 0.969 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 800 FrameTime: 1.250 ms
[ideas] speed=duration: FPS: 4088 FrameTime: 0.245 ms
[jellyfish] <default>: FPS: 4391 FrameTime: 0.228 ms
[terrain] <default>: FPS: 445 FrameTime: 2.247 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 9302 FrameTime: 0.108 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 8626 FrameTime: 0.116 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 9108 FrameTime: 0.110 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 9275 FrameTime: 0.108 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 8053 FrameTime: 0.124 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 9195 FrameTime: 0.109 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 9185 FrameTime: 0.109 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 9153 FrameTime: 0.109 ms
=======================================================
                                  glmark2 Score: 6682 
=======================================================

```

and not full screen:

```

=======================================================
max@max-Z87-D3HP:~$ glmark2
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   AMD Radeon R9 200 Series
    GL_VERSION:    4.3.12798 Compatibility Profile Context 14.20
=======================================================
[build] use-vbo=false: FPS: 3734 FrameTime: 0.268 ms
[build] use-vbo=true: FPS: 9094 FrameTime: 0.110 ms
[texture] texture-filter=nearest: FPS: 9095 FrameTime: 0.110 ms
[texture] texture-filter=linear: FPS: 9298 FrameTime: 0.108 ms
[texture] texture-filter=mipmap: FPS: 8542 FrameTime: 0.117 ms
[shading] shading=gouraud: FPS: 9109 FrameTime: 0.110 ms
[shading] shading=blinn-phong-inf: FPS: 8375 FrameTime: 0.119 ms
[shading] shading=phong: FPS: 9122 FrameTime: 0.110 ms
[bump] bump-render=high-poly: FPS: 7694 FrameTime: 0.130 ms
[bump] bump-render=normals: FPS: 7924 FrameTime: 0.126 ms
[bump] bump-render=height: FPS: 7956 FrameTime: 0.126 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 8712 FrameTime: 0.115 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 6961 FrameTime: 0.144 ms
[pulsar] light=false:quads=5:texture=false: FPS: 8717 FrameTime: 0.115 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 2054 FrameTime: 0.487 ms
[desktop] effect=shadow:windows=4: FPS: 1761 FrameTime: 0.568 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 715 FrameTime: 1.399 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 978 FrameTime: 1.022 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 898 FrameTime: 1.114 ms
[ideas] speed=duration: FPS: 3521 FrameTime: 0.284 ms
[jellyfish] <default>: FPS: 6345 FrameTime: 0.158 ms
[terrain] <default>: FPS: 726 FrameTime: 1.377 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 8755 FrameTime: 0.114 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 9606 FrameTime: 0.104 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 8765 FrameTime: 0.114 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 9452 FrameTime: 0.106 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 9396 FrameTime: 0.106 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 9453 FrameTime: 0.106 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 9509 FrameTime: 0.105 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 9257 FrameTime: 0.108 ms
=======================================================
                                  glmark2 Score: 6850 
=======================================================


```

---

### Post by maxinstuff2 on 2014-09-15
> **ilpiero said:**
> ```
glmark2 --fullscreen
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   AMD Radeon HD 8570D
    GL_VERSION:    4.2.12337 Compatibility Profile Context 13.101
=======================================================
[build] use-vbo=false: FPS: 59 FrameTime: 16.949 ms
[build] use-vbo=true: FPS: 60 FrameTime: 16.667 ms
[texture] texture-filter=nearest: FPS: 60 FrameTime: 16.667 ms
[texture] texture-filter=linear: FPS: 59 FrameTime: 16.949 ms
[texture] texture-filter=mipmap: FPS: 59 FrameTime: 16.949 ms
[shading] shading=gouraud: FPS: 60 FrameTime: 16.667 ms
[shading] shading=blinn-phong-inf: FPS: 60 FrameTime: 16.667 ms
[shading] shading=phong: FPS: 60 FrameTime: 16.667 ms
[bump] bump-render=high-poly: FPS: 60 FrameTime: 16.667 ms
[bump] bump-render=normals: FPS: 60 FrameTime: 16.667 ms
[bump] bump-render=height: FPS: 60 FrameTime: 16.667 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 60 FrameTime: 16.667 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 60 FrameTime: 16.667 ms
[pulsar] light=false:quads=5:texture=false: FPS: 60 FrameTime: 16.667 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 60 FrameTime: 16.667 ms
[desktop] effect=shadow:windows=4: FPS: 60 FrameTime: 16.667 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 59 FrameTime: 16.949 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 60 FrameTime: 16.667 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 59 FrameTime: 16.949 ms
[ideas] speed=duration: FPS: 60 FrameTime: 16.667 ms
[jellyfish] <default>: FPS: 60 FrameTime: 16.667 ms
[terrain] <default>: FPS: 51 FrameTime: 19.608 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 60 FrameTime: 16.667 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 60 FrameTime: 16.667 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 60 FrameTime: 16.667 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 60 FrameTime: 16.667 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 60 FrameTime: 16.667 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 60 FrameTime: 16.667 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 60 FrameTime: 16.667 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 60 FrameTime: 16.667 ms
=======================================================
                                  glmark2 Score: 59 
=======================================================
```



err...  59 with an AMD A8 6600K APU (AMD Radeon HD 8570D). fullscreen. 
Have i cheked the "lousy performance" flag somewhere?

It's called VSYNC (see my previous post)
Go into catalyst and turn off anti-tearing, and set "wait for vertical refresh" all the way down to "performance". 

I get weird artifacting and tearing on my desktop with these setting so switched it back afterwards.
EDIT: weird artifacting before turning 3d desktop accelleration back on in KDE. After turning it back into 3d mode it's fine.

---

### Post by bizhat on 2014-09-15
@maxinstuff2 Thank you for posting R9 270X glmark. How is Linux gaming on it ? Which games run smoothly ?

---

### Post by maxinstuff2 on 2014-09-15
> **bizhat said:**
> @maxinstuff2 Thank you for posting R9 270X glmark. How is Linux gaming on it ? Which games run smoothly ?

Firstly, it was a pain in the ass to get the drivers installed and working properly. Please keep that in mind before you run out and buy it. Always the case with current gen hardware I suppose.... *sigh* 

I can run the following on max settings smoothly (comments in parenthesis). Everything is in Steam unless noted otherwise:
The Witcher [playonlinux] (in play it is excellent, but there is some wine related graphical glitches)
XCOM (flawless)
Left For Dead 2 (flawless)
Mount and Blade (older game but FLAWLESS)
Path of Exile [playonlinux] (flawless)
Mount and Blade: Warband (flawless)

DOTA2 - seems to be fine, I had it crash once in a few hours play. 
Not sure if this is GPU/driver related but problems have been reported (there is in fact an outstanding bug listed in the driver release notes). It hasn't happened to me again - once in 4 hours aint bad.

Civilisation V (flawless)
Planetary Annihilation (curiosly - only works at high settings)

**And FYI -** 
Gone Home - doesn't work
The Witcher 2 [GOG version] - doesn't work 

Sorry I don't have anything more bleeding edge in this list, I am working through my backlog of titles that didn't work very well on my old dell laptop.
I will be downloading Wasteland 2 this week though so I have my fingers crossed :D

EDIT: soon after posting this I managed to get my screen graphics to... vibrate. I couldn't stop it and even regenerated xorg.conf with no effect. THEN I just unplugged the HDMI cable and plugged it back in and it was fixed :S
These drivers are not without bugs. Hopefully they'll mature soon.

---

### Post by dannyboy79 on 2014-09-15
> **bizhat said:**
> Why don't you try latest NVIDIA driver ? I was looking for a GTX 760 score as i may be getting GTX 750 or a GTX 760 soon. Please post a benchmark  once you got it fixed :)
i am running the latest nvidia drivers, 340.32 is the latest on their website ([http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)). I have no problem achieving almost 60 FPS in Metro Last Light maxed out and I get around 40 to 45 FPS in The Witcher 2 even with it's sad state of using the eON wrapper so I don't think it's anything wrong with my card or driver install. It may be how glmark2 handles dual monitor setups. Also, my numbers are running in a 1920x1080 window, i can't be sure what everyone is running their test with, if it's just the default than no wonder their getting such high numbers

UPDATE: i ended up noticing others were using 334.13 so I gave that a try, much better but still not better than a 750ti????? That just doesn't seem right at all. I'm running a dual monitior setup so not sure if that's impacting anything. Here's some weird results. I did it once with the -s 1920x1080 set and then I ran it again using --fullscreen. You would think the test with the -s setting would be better since it's in a window BUT it's not, it's lower than the --fullscreen test so that leads me to believe something is weird with the glmark2 benchmark.

```
glmark2 -s 1920x1080
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 760/PCIe/SSE2
    GL_VERSION:    4.4.0 NVIDIA 343.13
=======================================================
[build] use-vbo=false: FPS: 2911 FrameTime: 0.344 ms
[build] use-vbo=true: FPS: 4274 FrameTime: 0.234 ms
[texture] texture-filter=nearest: FPS: 4262 FrameTime: 0.235 ms
[texture] texture-filter=linear: FPS: 3598 FrameTime: 0.278 ms
[texture] texture-filter=mipmap: FPS: 3874 FrameTime: 0.258 ms
[shading] shading=gouraud: FPS: 4437 FrameTime: 0.225 ms
[shading] shading=blinn-phong-inf: FPS: 4474 FrameTime: 0.224 ms
[shading] shading=phong: FPS: 4493 FrameTime: 0.223 ms
[bump] bump-render=high-poly: FPS: 4397 FrameTime: 0.227 ms
[bump] bump-render=normals: FPS: 4490 FrameTime: 0.223 ms
[bump] bump-render=height: FPS: 4492 FrameTime: 0.223 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 3062 FrameTime: 0.327 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 2050 FrameTime: 0.488 ms
[pulsar] light=false:quads=5:texture=false: FPS: 4026 FrameTime: 0.248 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 1669 FrameTime: 0.599 ms
[desktop] effect=shadow:windows=4: FPS: 2262 FrameTime: 0.442 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 973 FrameTime: 1.028 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1204 FrameTime: 0.831 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1121 FrameTime: 0.892 ms
[ideas] speed=duration: FPS: 3326 FrameTime: 0.301 ms
[jellyfish] <default>: FPS: 2570 FrameTime: 0.389 ms
[terrain] <default>: FPS: 466 FrameTime: 2.146 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 4504 FrameTime: 0.222 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 4439 FrameTime: 0.225 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 4523 FrameTime: 0.221 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 4519 FrameTime: 0.221 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 4113 FrameTime: 0.243 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 4506 FrameTime: 0.222 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 4508 FrameTime: 0.222 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 4485 FrameTime: 0.223 ms
=======================================================
                                  glmark2 Score: 3467 
=======================================================


```
glmark2 --fullscreen
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 760/PCIe/SSE2
    GL_VERSION:    4.4.0 NVIDIA 343.13
=======================================================
[build] use-vbo=false: FPS: 3545 FrameTime: 0.282 ms
[build] use-vbo=true: FPS: 4450 FrameTime: 0.225 ms
[texture] texture-filter=nearest: FPS: 4481 FrameTime: 0.223 ms
[texture] texture-filter=linear: FPS: 4487 FrameTime: 0.223 ms
[texture] texture-filter=mipmap: FPS: 4444 FrameTime: 0.225 ms
[shading] shading=gouraud: FPS: 4515 FrameTime: 0.221 ms
[shading] shading=blinn-phong-inf: FPS: 4511 FrameTime: 0.222 ms
[shading] shading=phong: FPS: 4452 FrameTime: 0.225 ms
[bump] bump-render=high-poly: FPS: 4499 FrameTime: 0.222 ms
[bump] bump-render=normals: FPS: 4394 FrameTime: 0.228 ms
[bump] bump-render=height: FPS: 4466 FrameTime: 0.224 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 3075 FrameTime: 0.325 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 2025 FrameTime: 0.494 ms
[pulsar] light=false:quads=5:texture=false: FPS: 4284 FrameTime: 0.233 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 1445 FrameTime: 0.692 ms
[desktop] effect=shadow:windows=4: FPS: 1963 FrameTime: 0.509 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 989 FrameTime: 1.011 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1253 FrameTime: 0.798 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1125 FrameTime: 0.889 ms
[ideas] speed=duration: FPS: 3328 FrameTime: 0.300 ms
[jellyfish] <default>: FPS: 2880 FrameTime: 0.347 ms
[terrain] <default>: FPS: 336 FrameTime: 2.976 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 4287 FrameTime: 0.233 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 4438 FrameTime: 0.225 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 4481 FrameTime: 0.223 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 4470 FrameTime: 0.224 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 4512 FrameTime: 0.222 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 4432 FrameTime: 0.226 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 4503 FrameTime: 0.222 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 4514 FrameTime: 0.222 ms
=======================================================
                                  glmark2 Score: 3552 
=======================================================[/code]

---

### Post by maxinstuff2 on 2014-09-15
> **dannyboy79 said:**
> UPDATE: i ended up noticing others were using 334.13 so I gave that a try, much better but still not better than a 750ti????? That just doesn't seem right at all. I'm running a dual monitior setup so not sure if that's impacting anything. Here's some weird results. I did it once with the -s 1920x1080 set and then I ran it again using --fullscreen. You would think the test with the -s setting would be better since it's in a window BUT it's not, it's lower than the --fullscreen test so that leads me to believe something is weird with the glmark2 benchmark.


Have you tried disconnecting the second monitor?
The test seems to me to be based on pure fps so it doesn't tell the whole story. There are many variables. If you want to see the highest score possible:
> turn of desktop accelleration
> turn off vsync, and put all graphics card settings to "Performance" instead of "Quality". 
You will likely get a much higher score, but I am sure you can see why that might not be ideal, or even desired....

---

### Post by dannyboy79 on 2014-09-15
> **maxinstuff2 said:**
> Have you tried disconnecting the second monitor?
The test seems to me to be based on pure fps so it doesn't tell the whole story. There are many variables. If you want to see the highest score possible:
> turn of desktop accelleration
> turn off vsync, and put all graphics card settings to "Performance" instead of "Quality". 
You will likely get a much higher score, but I am sure you can see why that might not be ideal, or even desired....

still doesn't seem correct even after turning off COMPTON which is a compositor for getting rid of screen tearing but again i think it's because of my dual monitor and I'm not that interested to unplug my second monitor or disable it momentarily so here's my final numbers which is barely better than a 750ti so maybe it is accurate?
```
glmark2 -s 1920x1080
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 760/PCIe/SSE2
    GL_VERSION:    4.4.0 NVIDIA 343.13
=======================================================
[build] use-vbo=false: FPS: 4425 FrameTime: 0.226 ms
[build] use-vbo=true: FPS: 4652 FrameTime: 0.215 ms
[texture] texture-filter=nearest: FPS: 4637 FrameTime: 0.216 ms
[texture] texture-filter=linear: FPS: 4638 FrameTime: 0.216 ms
[texture] texture-filter=mipmap: FPS: 4640 FrameTime: 0.216 ms
[shading] shading=gouraud: FPS: 4648 FrameTime: 0.215 ms
[shading] shading=blinn-phong-inf: FPS: 4647 FrameTime: 0.215 ms
[shading] shading=phong: FPS: 4648 FrameTime: 0.215 ms
[bump] bump-render=high-poly: FPS: 4649 FrameTime: 0.215 ms
[bump] bump-render=normals: FPS: 4650 FrameTime: 0.215 ms
[bump] bump-render=height: FPS: 4645 FrameTime: 0.215 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 3690 FrameTime: 0.271 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 2114 FrameTime: 0.473 ms
[pulsar] light=false:quads=5:texture=false: FPS: 4298 FrameTime: 0.233 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 1753 FrameTime: 0.570 ms
[desktop] effect=shadow:windows=4: FPS: 2590 FrameTime: 0.386 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1122 FrameTime: 0.891 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1377 FrameTime: 0.726 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1256 FrameTime: 0.796 ms
[ideas] speed=duration: FPS: 3925 FrameTime: 0.255 ms
[jellyfish] <default>: FPS: 2860 FrameTime: 0.350 ms
[terrain] <default>: FPS: 482 FrameTime: 2.075 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 4658 FrameTime: 0.215 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 4658 FrameTime: 0.215 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 4660 FrameTime: 0.215 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 4661 FrameTime: 0.215 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 4658 FrameTime: 0.215 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 4662 FrameTime: 0.215 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 4660 FrameTime: 0.215 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 4663 FrameTime: 0.214 ms
=======================================================
                                  glmark2 Score: 3787 
=======================================================

```

---

### Post by maxinstuff2 on 2014-09-16
> **dannyboy79 said:**
> still doesn't seem correct even after turning off COMPTON which is a compositor for getting rid of screen tearing but again i think it's because of my dual monitor and I'm not that interested to unplug my second monitor or disable it momentarily so here's my final numbers which is barely better than a 750ti so maybe it is accurate?


Interesting, it looks like these items:
```
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1122 FrameTime: 0.891 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1377 FrameTime: 0.726 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1256 FrameTime: 0.796 ms
```
and especially this one:
```
[terrain] <default>: FPS: 482 FrameTime: 2.075 ms
```
are the only things that trashed your score....

The rest is all up over 4000.

---

### Post by polochamps on 2014-09-18
Ubuntu 14.04 x64 with Unity
Nvidia 331.38
1920x1080
3.13.0-35


```
 $ glmark2 -s 1920x1080
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 660 Ti/PCIe/SSE2
    GL_VERSION:    4.4.0 NVIDIA 331.38
=======================================================
[build] use-vbo=false: FPS: 6374 FrameTime: 0.157 ms
[build] use-vbo=true: FPS: 7648 FrameTime: 0.131 ms
[texture] texture-filter=nearest: FPS: 6432 FrameTime: 0.155 ms
[texture] texture-filter=linear: FPS: 6486 FrameTime: 0.154 ms
[texture] texture-filter=mipmap: FPS: 6628 FrameTime: 0.151 ms
[shading] shading=gouraud: FPS: 6139 FrameTime: 0.163 ms
[shading] shading=blinn-phong-inf: FPS: 6142 FrameTime: 0.163 ms
[shading] shading=phong: FPS: 6054 FrameTime: 0.165 ms
[bump] bump-render=high-poly: FPS: 5947 FrameTime: 0.168 ms
[bump] bump-render=normals: FPS: 7451 FrameTime: 0.134 ms
[bump] bump-render=height: FPS: 7365 FrameTime: 0.136 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 3966 FrameTime: 0.252 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 2506 FrameTime: 0.399 ms
[pulsar] light=false:quads=5:texture=false: FPS: 5679 FrameTime: 0.176 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 1836 FrameTime: 0.545 ms
[desktop] effect=shadow:windows=4: FPS: 2677 FrameTime: 0.374 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1498 FrameTime: 0.668 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1675 FrameTime: 0.597 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1617 FrameTime: 0.618 ms
[ideas] speed=duration: FPS: 4660 FrameTime: 0.215 ms
[jellyfish] <default>: FPS: 2798 FrameTime: 0.357 ms
[terrain] <default>: FPS: 376 FrameTime: 2.660 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 5303 FrameTime: 0.189 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 5402 FrameTime: 0.185 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 5552 FrameTime: 0.180 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 5419 FrameTime: 0.185 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 5356 FrameTime: 0.187 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 5450 FrameTime: 0.183 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 5450 FrameTime: 0.183 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 5430 FrameTime: 0.184 ms
=======================================================
                                  glmark2 Score: 4843 




```

```
 $ glmark2 --fullscreen
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 660 Ti/PCIe/SSE2
    GL_VERSION:    4.4.0 NVIDIA 331.38
=======================================================
[build] use-vbo=false: FPS: 5283 FrameTime: 0.189 ms
[build] use-vbo=true: FPS: 5410 FrameTime: 0.185 ms
[texture] texture-filter=nearest: FPS: 4887 FrameTime: 0.205 ms
[texture] texture-filter=linear: FPS: 4886 FrameTime: 0.205 ms
[texture] texture-filter=mipmap: FPS: 4911 FrameTime: 0.204 ms
[shading] shading=gouraud: FPS: 4803 FrameTime: 0.208 ms
[shading] shading=blinn-phong-inf: FPS: 4795 FrameTime: 0.209 ms
[shading] shading=phong: FPS: 4813 FrameTime: 0.208 ms
[bump] bump-render=high-poly: FPS: 4387 FrameTime: 0.228 ms
[bump] bump-render=normals: FPS: 5391 FrameTime: 0.185 ms
[bump] bump-render=height: FPS: 5296 FrameTime: 0.189 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 3571 FrameTime: 0.280 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 2424 FrameTime: 0.413 ms
[pulsar] light=false:quads=5:texture=false: FPS: 3844 FrameTime: 0.260 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 1724 FrameTime: 0.580 ms
[desktop] effect=shadow:windows=4: FPS: 2429 FrameTime: 0.412 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1417 FrameTime: 0.706 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1664 FrameTime: 0.601 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1534 FrameTime: 0.652 ms
[ideas] speed=duration: FPS: 4166 FrameTime: 0.240 ms
[jellyfish] <default>: FPS: 2662 FrameTime: 0.376 ms
[terrain] <default>: FPS: 377 FrameTime: 2.653 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 4923 FrameTime: 0.203 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 4896 FrameTime: 0.204 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 4924 FrameTime: 0.203 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 4924 FrameTime: 0.203 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 4892 FrameTime: 0.204 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 4926 FrameTime: 0.203 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 4924 FrameTime: 0.203 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 4903 FrameTime: 0.204 ms
=======================================================
                                  glmark2 Score: 3999 


```

**Default**

```
 glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 660 Ti/PCIe/SSE2
    GL_VERSION:    4.4.0 NVIDIA 331.38
=======================================================
[build] use-vbo=false: FPS: 8972 FrameTime: 0.111 ms
[build] use-vbo=true: FPS: 15629 FrameTime: 0.064 ms
[texture] texture-filter=nearest: FPS: 13651 FrameTime: 0.073 ms
[texture] texture-filter=linear: FPS: 13116 FrameTime: 0.076 ms
[texture] texture-filter=mipmap: FPS: 14669 FrameTime: 0.068 ms
[shading] shading=gouraud: FPS: 13792 FrameTime: 0.073 ms
[shading] shading=blinn-phong-inf: FPS: 13717 FrameTime: 0.073 ms
[shading] shading=phong: FPS: 13692 FrameTime: 0.073 ms
[bump] bump-render=high-poly: FPS: 9710 FrameTime: 0.103 ms
[bump] bump-render=normals: FPS: 16822 FrameTime: 0.059 ms
[bump] bump-render=height: FPS: 16555 FrameTime: 0.060 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 11035 FrameTime: 0.091 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 8372 FrameTime: 0.119 ms
[pulsar] light=false:quads=5:texture=false: FPS: 14535 FrameTime: 0.069 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 4641 FrameTime: 0.215 ms
[desktop] effect=shadow:windows=4: FPS: 7521 FrameTime: 0.133 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1301 FrameTime: 0.769 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1686 FrameTime: 0.593 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1623 FrameTime: 0.616 ms
[ideas] speed=duration: FPS: 12606 FrameTime: 0.079 ms
[jellyfish] <default>: FPS: 7379 FrameTime: 0.136 ms
[terrain] <default>: FPS: 795 FrameTime: 1.258 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 12366 FrameTime: 0.081 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 13209 FrameTime: 0.076 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 13446 FrameTime: 0.074 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 13147 FrameTime: 0.076 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 13219 FrameTime: 0.076 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 13180 FrameTime: 0.076 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 12483 FrameTime: 0.080 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 13090 FrameTime: 0.076 ms
=======================================================
                                  glmark2 Score: 10865 


```

---

### Post by olliemonster on 2014-09-20
Ubuntu 14.10 dev X64 amd a10 5700 with an intergrated graphics card 
With mesa it scored 367
It was in windowed mode with unity running
I haven't tried using amds drivers

---

### Post by dannyboy79 on 2014-09-21
> **olliemonster said:**
> Ubuntu 14.10 dev X64 amd a10 5700 with an intergrated graphics card 
With mesa it scored 367
It was in windowed mode with unity running
I haven't tried using amds drivers
if you aren't going to run the proprietary catalyst driver from AMD than I would at least suggest using the latest open source AMD driver over the default one ubuntu packages, you can easily get it by using Oibaf's PPA, it will give you an updated radeon driver as well as a more recent mesa build, you'll see a huge improvement but it still isn't as good as the proprietary AMD catalyst driver though I don't think. Good luck

---

### Post by MrMichaelHill on 2014-09-23
> **ManamiVixen said:**
> Everybody, when you do the test, make sure there are no other programs that require 3D acceleration with the GPU running. Like say Compiz and Unity. If they are running, it wil skew the results. Be sure to use a non-composited desktop like LXDE or Gnome-Sesion-Fallback with no effects to get an accurate reading.

Kind of don't agree with this sorry?

I think that as long as you put in that you are running Ubuntu 14.04 in your results its a good indicator as to how different DE's are running on different hardware?

---

### Post by JDorfler on 2014-09-30
Okay, as promised all fullscreen 1920*1080;

Main PC:
AMD FX-8350 OCed to 4.4GHz, AMD Radeon HD-7970 GHz Edition
```
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   AMD Radeon HD 7900 Series 
    GL_VERSION:    4.4.12967 Compatibility Profile Context 14.20
=======================================================
[build] use-vbo=false: FPS: 3156 FrameTime: 0.317 ms
[build] use-vbo=true: FPS: 6603 FrameTime: 0.151 ms
[texture] texture-filter=nearest: FPS: 6488 FrameTime: 0.154 ms
[texture] texture-filter=linear: FPS: 6339 FrameTime: 0.158 ms
[texture] texture-filter=mipmap: FPS: 6419 FrameTime: 0.156 ms
[shading] shading=gouraud: FPS: 6098 FrameTime: 0.164 ms
[shading] shading=blinn-phong-inf: FPS: 6069 FrameTime: 0.165 ms
[shading] shading=phong: FPS: 6064 FrameTime: 0.165 ms
[bump] bump-render=high-poly: FPS: 5548 FrameTime: 0.180 ms
[bump] bump-render=normals: FPS: 6617 FrameTime: 0.151 ms
[bump] bump-render=height: FPS: 6190 FrameTime: 0.162 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 4720 FrameTime: 0.212 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 3376 FrameTime: 0.296 ms
[pulsar] light=false:quads=5:texture=false: FPS: 5631 FrameTime: 0.178 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 1736 FrameTime: 0.576 ms
[desktop] effect=shadow:windows=4: FPS: 1822 FrameTime: 0.549 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 931 FrameTime: 1.074 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1473 FrameTime: 0.679 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1176 FrameTime: 0.850 ms
[ideas] speed=duration: FPS: 3847 FrameTime: 0.260 ms
[jellyfish] <default>: FPS: 4398 FrameTime: 0.227 ms
[terrain] <default>: FPS: 525 FrameTime: 1.905 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 6426 FrameTime: 0.156 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 6226 FrameTime: 0.161 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 6248 FrameTime: 0.160 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 6393 FrameTime: 0.156 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 6316 FrameTime: 0.158 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 6246 FrameTime: 0.160 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 6287 FrameTime: 0.159 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 6318 FrameTime: 0.158 ms
=======================================================
                                  glmark2 Score: 4856 
=======================================================

```

AMD FX-8350 OCed to 4.4GHz, AMD Radeon R9 290X GHz Edition
```
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   AMD Radeon R9 200 Series
    GL_VERSION:    4.4.12967 Compatibility Profile Context 14.20
=======================================================
[build] use-vbo=false: FPS: 5196 FrameTime: 0.192 ms
[build] use-vbo=true: FPS: 9360 FrameTime: 0.107 ms
[texture] texture-filter=nearest: FPS: 9140 FrameTime: 0.109 ms
[texture] texture-filter=linear: FPS: 9146 FrameTime: 0.109 ms
[texture] texture-filter=mipmap: FPS: 9219 FrameTime: 0.108 ms
[shading] shading=gouraud: FPS: 8844 FrameTime: 0.113 ms
[shading] shading=blinn-phong-inf: FPS: 8785 FrameTime: 0.114 ms
[shading] shading=phong: FPS: 8744 FrameTime: 0.114 ms
[bump] bump-render=high-poly: FPS: 7208 FrameTime: 0.139 ms
[bump] bump-render=normals: FPS: 9324 FrameTime: 0.107 ms
[bump] bump-render=height: FPS: 9292 FrameTime: 0.108 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 6717 FrameTime: 0.149 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 4695 FrameTime: 0.213 ms
[pulsar] light=false:quads=5:texture=false: FPS: 8388 FrameTime: 0.119 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 3015 FrameTime: 0.332 ms
[desktop] effect=shadow:windows=4: FPS: 2121 FrameTime: 0.471 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 941 FrameTime: 1.063 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1452 FrameTime: 0.689 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1191 FrameTime: 0.840 ms
[ideas] speed=duration: FPS: 3943 FrameTime: 0.254 ms
[jellyfish] <default>: FPS: 6885 FrameTime: 0.145 ms
[terrain] <default>: FPS: 659 FrameTime: 1.517 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 8884 FrameTime: 0.113 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 9066 FrameTime: 0.110 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 8952 FrameTime: 0.112 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 9006 FrameTime: 0.111 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 9010 FrameTime: 0.111 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 8968 FrameTime: 0.112 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 9085 FrameTime: 0.110 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 8867 FrameTime: 0.113 ms
=======================================================
                                  glmark2 Score: 6870 
=======================================================

```
AMD FX-9590 OCed to 5.0GHz, AMD Radeon R9 290X GHz Edition
```
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   AMD Radeon R9 200 Series
    GL_VERSION:    4.4.13084 Compatibility Profile Context 14.20
=======================================================
[build] use-vbo=false: FPS: 6234 FrameTime: 0.160 ms
[build] use-vbo=true: FPS: 11282 FrameTime: 0.089 ms
[texture] texture-filter=nearest: FPS: 11278 FrameTime: 0.089 ms
[texture] texture-filter=linear: FPS: 11280 FrameTime: 0.089 ms
[texture] texture-filter=mipmap: FPS: 11300 FrameTime: 0.088 ms
[shading] shading=gouraud: FPS: 10847 FrameTime: 0.092 ms
[shading] shading=blinn-phong-inf: FPS: 10772 FrameTime: 0.093 ms
[shading] shading=phong: FPS: 10344 FrameTime: 0.097 ms
[bump] bump-render=high-poly: FPS: 8517 FrameTime: 0.117 ms
[bump] bump-render=normals: FPS: 11308 FrameTime: 0.088 ms
[bump] bump-render=height: FPS: 11280 FrameTime: 0.089 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 6751 FrameTime: 0.148 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 4788 FrameTime: 0.209 ms
[pulsar] light=false:quads=5:texture=false: FPS: 10553 FrameTime: 0.095 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 3052 FrameTime: 0.328 ms
[desktop] effect=shadow:windows=4: FPS: 2470 FrameTime: 0.405 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1016 FrameTime: 0.984 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1712 FrameTime: 0.584 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1287 FrameTime: 0.777 ms
[ideas] speed=duration: FPS: 4637 FrameTime: 0.216 ms
[jellyfish] <default>: FPS: 8260 FrameTime: 0.121 ms
[terrain] <default>: FPS: 728 FrameTime: 1.374 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 11279 FrameTime: 0.089 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 11257 FrameTime: 0.089 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 11258 FrameTime: 0.089 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 11274 FrameTime: 0.089 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 11256 FrameTime: 0.089 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 11230 FrameTime: 0.089 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 11236 FrameTime: 0.089 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 11206 FrameTime: 0.089 ms
=======================================================
                                  glmark2 Score: 8323 
=======================================================

```
Sager Notebook 2011 Edition
Core I7 Mobile Extreme Edition, AMD Mobile Radeon HD 6970
```
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   AMD Radeon HD 6900M Series
    GL_VERSION:    4.4.12967 Compatibility Profile Context 13.35.1005
=======================================================
[build] use-vbo=false: FPS: 4114 FrameTime: 0.243 ms
[build] use-vbo=true: FPS: 5510 FrameTime: 0.181 ms
[texture] texture-filter=nearest: FPS: 5400 FrameTime: 0.185 ms
[texture] texture-filter=linear: FPS: 5399 FrameTime: 0.185 ms
[texture] texture-filter=mipmap: FPS: 5429 FrameTime: 0.184 ms
[shading] shading=gouraud: FPS: 4773 FrameTime: 0.210 ms
[shading] shading=blinn-phong-inf: FPS: 4732 FrameTime: 0.211 ms
[shading] shading=phong: FPS: 4324 FrameTime: 0.231 ms
[bump] bump-render=high-poly: FPS: 2782 FrameTime: 0.359 ms
[bump] bump-render=normals: FPS: 5263 FrameTime: 0.190 ms
[bump] bump-render=height: FPS: 4973 FrameTime: 0.201 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 1502 FrameTime: 0.666 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 948 FrameTime: 1.055 ms
[pulsar] light=false:quads=5:texture=false: FPS: 4773 FrameTime: 0.210 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 1022 FrameTime: 0.978 ms
[desktop] effect=shadow:windows=4: FPS: 1058 FrameTime: 0.945 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 749 FrameTime: 1.335 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 979 FrameTime: 1.021 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 861 FrameTime: 1.161 ms
[ideas] speed=duration: FPS: 2844 FrameTime: 0.352 ms
[jellyfish] <default>: FPS: 3001 FrameTime: 0.333 ms
[terrain] <default>: FPS: 210 FrameTime: 4.762 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 5081 FrameTime: 0.197 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 4257 FrameTime: 0.235 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 5063 FrameTime: 0.198 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 4855 FrameTime: 0.206 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 3393 FrameTime: 0.295 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 4797 FrameTime: 0.208 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 4805 FrameTime: 0.208 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 3465 FrameTime: 0.289 ms
=======================================================
                                  glmark2 Score: 3545 
=======================================================

```

All tests done with Compiz Cube and many effects still in place while office applications still running.
Enjoy.

---

### Post by Christopherius on 2014-10-01
NVIDIA GTX 650 Ti glmark2 score: 3666

---

### Post by peter185 on 2015-03-29
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 460/PCIe/SSE2
    GL_VERSION:    4.4.0 NVIDIA 331.113
=======================================================


=======================================================
                                  glmark2 Score: **6065** 
=======================================================

---

### Post by Drazhok on 2015-04-09
I don't even want to try lol, my video card is a sculpted turd with a fan.

---

### Post by binary-soul on 2015-05-28
Its a ZOTAC GTX 970 AMP! Extreme Core

> 
======================================================= 

   glmark2 2012.08

=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 970/PCIe/SSE2
    GL_VERSION:    4.5.0 NVIDIA 346.72
=======================================================
=======================================================
                                  glmark2 Score: 9470 
=======================================================


---

### Post by efflandt on 2015-05-29
I am just curious how martin-wangle got 7242 at default 800x600 with GTX 750 and oldrocker99 got 3691 --fullscreen @ 1080p with glmark2 2012.08 or if PCIe 3.0 vs. 2.0 makes a difference for these cards. I have a 5 year old PC w/BIOS (in my sig), not UEFI, and the best I have been able to do so far with MSI Twin Frozr GTX 750 Ti OC with gpmark2 2012.08 (regular default Unity desktop) with nvidia-352 (352.09 from xorg-edgers, just slightly faster than nvidia-349) at default 800x600 has been 4792 at its stock overclock and 5264 w/gpu bumped up another 220 Hz. And the best I did --fullscreen @ 1080p was 2457 (2494 overclocked).

Although, I did manage to do 7251 @ default 800x600 in 12.04 with the older glmark2 2011.09 that I still have on an SSD and 2904 @ -s 1920x1080 (that version has no --fullscreen) using nvidia-331-updates. The GTX 750 Ti is faster for most things than my old GTX 550 Ti while using almost half the power (60w vs. 116w) and it works fine for Steam games (triple digits most of the time in Team Fortress 2).

So I am just curious if just PCIe 3.0 makes them 50% faster than PCIe 2.0 for this relatively low powered card or some other factor?

PS: Nvidia prime in 14.04 works much better on my laptop than bumblebee (optirun) did in 13.10 (both 64-bit). With 319.60 driver in 13.10 default (800x600)/fullscreen (1080p) scores were 173/88 for Intel and 235/95 with optirun.

For nvidia-331-updates (331.113) in 14.04 default/1080p scores are 1441/361 Intel and 4380/2074 Nvidia.

---

### Post by atmega8513 on 2015-09-03
(I hope this isn't too far out of date.)
my Intel i3-4010U Integrated quad core electron juggler (gigabyte BRIX projector) gave a 1600 at 1360x768 with lxde up.
just for kicks, my amd radeon hd 4200 laptop gave a 226 at 1366x768 also with lxde running. hope this helps.

---

### Post by alexandr14 on 2016-01-19
Hi there! Here is score of my office computer, only for fun or history...:)
 
Advanced Micro Devices, Inc. [AMD/ATI] RV730 XT [Radeon HD 4670] [1002:9490]

```
glmark2 --size 1920x1080
=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     X.Org
    GL_RENDERER:   Gallium 0.4 on AMD RV730 (DRM 2.43.0, LLVM 3.6.2)
    GL_VERSION:    3.0 Mesa 11.0.2
=======================================================
[build] use-vbo=false: FPS: 418 FrameTime: 2.392 ms
[build] use-vbo=true: FPS: 417 FrameTime: 2.398 ms
[texture] texture-filter=nearest: FPS: 391 FrameTime: 2.558 ms
[texture] texture-filter=linear: FPS: 391 FrameTime: 2.558 ms
[texture] texture-filter=mipmap: FPS: 393 FrameTime: 2.545 ms
[shading] shading=gouraud: FPS: 390 FrameTime: 2.564 ms
[shading] shading=blinn-phong-inf: FPS: 390 FrameTime: 2.564 ms
[shading] shading=phong: FPS: 390 FrameTime: 2.564 ms
[shading] shading=cel: FPS: 398 FrameTime: 2.513 ms
[bump] bump-render=high-poly: FPS: 375 FrameTime: 2.667 ms
[bump] bump-render=normals: FPS: 407 FrameTime: 2.457 ms
[bump] bump-render=height: FPS: 404 FrameTime: 2.475 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 319 FrameTime: 3.135 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 228 FrameTime: 4.386 ms
[pulsar] light=false:quads=5:texture=false: FPS: 330 FrameTime: 3.030 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 150 FrameTime: 6.667 ms
[desktop] effect=shadow:windows=4: FPS: 183 FrameTime: 5.464 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 298 FrameTime: 3.356 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 311 FrameTime: 3.215 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 300 FrameTime: 3.333 ms
[ideas] speed=duration: FPS: 344 FrameTime: 2.907 ms
[jellyfish] <default>: FPS: 229 FrameTime: 4.367 ms
[terrain] <default>: FPS: 58 FrameTime: 17.241 ms
[shadow] <default>: FPS: 155 FrameTime: 6.452 ms
[refract] <default>: FPS: 60 FrameTime: 16.667 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 364 FrameTime: 2.747 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 364 FrameTime: 2.747 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 364 FrameTime: 2.747 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 365 FrameTime: 2.740 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 352 FrameTime: 2.841 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 365 FrameTime: 2.740 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 365 FrameTime: 2.740 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 281 FrameTime: 3.559 ms
=======================================================
                                  glmark2 Score: 319 
=======================================================
```
```
glmark2 --size 800x600
=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     X.Org
    GL_RENDERER:   Gallium 0.4 on AMD RV730 (DRM 2.43.0, LLVM 3.6.2)
    GL_VERSION:    3.0 Mesa 11.0.2
=======================================================
[build] use-vbo=false: FPS: 1695 FrameTime: 0.590 ms
[build] use-vbo=true: FPS: 1790 FrameTime: 0.559 ms
[texture] texture-filter=nearest: FPS: 1573 FrameTime: 0.636 ms
[texture] texture-filter=linear: FPS: 1560 FrameTime: 0.641 ms
[texture] texture-filter=mipmap: FPS: 1606 FrameTime: 0.623 ms
[shading] shading=gouraud: FPS: 1581 FrameTime: 0.633 ms
[shading] shading=blinn-phong-inf: FPS: 1582 FrameTime: 0.632 ms
[shading] shading=phong: FPS: 1575 FrameTime: 0.635 ms
[shading] shading=cel: FPS: 1572 FrameTime: 0.636 ms
[bump] bump-render=high-poly: FPS: 1243 FrameTime: 0.805 ms
[bump] bump-render=normals: FPS: 1768 FrameTime: 0.566 ms
[bump] bump-render=height: FPS: 1733 FrameTime: 0.577 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 1358 FrameTime: 0.736 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 1006 FrameTime: 0.994 ms
[pulsar] light=false:quads=5:texture=false: FPS: 1405 FrameTime: 0.712 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 589 FrameTime: 1.698 ms
[desktop] effect=shadow:windows=4: FPS: 766 FrameTime: 1.305 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 595 FrameTime: 1.681 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 643 FrameTime: 1.555 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 639 FrameTime: 1.565 ms
[ideas] speed=duration: FPS: 1355 FrameTime: 0.738 ms
[jellyfish] <default>: FPS: 888 FrameTime: 1.126 ms
[terrain] <default>: FPS: 150 FrameTime: 6.667 ms
[shadow] <default>: FPS: 658 FrameTime: 1.520 ms
[refract] <default>: FPS: 195 FrameTime: 5.128 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 1505 FrameTime: 0.664 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 1505 FrameTime: 0.664 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 1504 FrameTime: 0.665 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 1499 FrameTime: 0.667 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 1462 FrameTime: 0.684 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 1501 FrameTime: 0.666 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 1504 FrameTime: 0.665 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 1115 FrameTime: 0.897 ms
=======================================================
                                  glmark2 Score: 1246 
=======================================================
```

---

### Post by ronneburger on 2016-01-25
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 750/PCIe/SSE2
    GL_VERSION:    4.4.0 NVIDIA 340.96
=======================================================
[build] use-vbo=false: FPS: 4504 FrameTime: 0.222 ms
[build] use-vbo=true: FPS: 6684 FrameTime: 0.150 ms
[texture] texture-filter=nearest: FPS: 6417 FrameTime: 0.156 ms
[texture] texture-filter=linear: FPS: 6720 FrameTime: 0.149 ms
[texture] texture-filter=mipmap: FPS: 6780 FrameTime: 0.147 ms
[shading] shading=gouraud: FPS: 6132 FrameTime: 0.163 ms
[shading] shading=blinn-phong-inf: FPS: 6054 FrameTime: 0.165 ms
[shading] shading=phong: FPS: 5565 FrameTime: 0.180 ms
[bump] bump-render=high-poly: FPS: 4158 FrameTime: 0.241 ms
[bump] bump-render=normals: FPS: 6755 FrameTime: 0.148 ms
[bump] bump-render=height: FPS: 6534 FrameTime: 0.153 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 4511 FrameTime: 0.222 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 2723 FrameTime: 0.367 ms
[pulsar] light=false:quads=5:texture=false: FPS: 6230 FrameTime: 0.161 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 2290 FrameTime: 0.437 ms
[desktop] effect=shadow:windows=4: FPS: 3807 FrameTime: 0.263 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1072 FrameTime: 0.933 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1204 FrameTime: 0.831 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1140 FrameTime: 0.877 ms
[ideas] speed=duration: FPS: 5333 FrameTime: 0.188 ms
[jellyfish] <default>: FPS: 3910 FrameTime: 0.256 ms
[terrain] <default>: FPS: 503 FrameTime: 1.988 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 6000 FrameTime: 0.167 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 5505 FrameTime: 0.182 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 5894 FrameTime: 0.170 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 5844 FrameTime: 0.171 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 5193 FrameTime: 0.193 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 5823 FrameTime: 0.172 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 5881 FrameTime: 0.170 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 5488 FrameTime: 0.182 ms
=======================================================
                                  glmark2 Score: 4821 
=======================================================

---

### Post by dosm-mail on 2016-02-07
I know this thread is quite old, but I just tested on my devices. First, my laptop with Intel i3-3120m without a graphics card:

```

[FONT=monospace][COLOR=#000000]=======================================================[/COLOR]
    glmark2 2014.03
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center 
    GL_RENDERER:   Mesa DRI Intel(R) Ivybridge Mobile 
    GL_VERSION:    3.0 Mesa 11.1.1
=======================================================
with default window settings:
=======================================================
                                  glmark2 Score: 1495 
=======================================================
and in fullscreen (1600x900):
[/FONT][FONT=monospace]======================================================= [/FONT]
[FONT=monospace]                                 glmark2 Score: 389 [/FONT]
[FONT=monospace]=======================================================
[/FONT]
```

Second, my self build desktop with i7-4790k and nvidia gt 730 ddr3 2gb:

```

[FONT=monospace][COLOR=#000000]=======================================================[/COLOR]
    glmark2 2014.03
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GT 730/PCIe/SSE2
    GL_VERSION:    4.5.0 NVIDIA 361.18
=======================================================
with default window settings:
=======================================================
                                  glmark2 Score: 2144
=======================================================
and in fullscreen (1920x1080):
[/FONT][FONT=monospace][COLOR=#000000]=======================================================[/COLOR]
                                  glmark2 Score: 723
=======================================================
[/FONT]
```

---

### Post by carmelo123412 on 2016-02-09
Yeah, old thread, I tested my device after the new nvidia update...
GTX 970 Asus Strix

=======================================================
    glmark2 2014.03
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 970/PCIe/SSE2
    GL_VERSION:    4.5.0 NVIDIA 361.28
=======================================================
[build] use-vbo=false: FPS: 9906 FrameTime: 0.101 ms
[build] use-vbo=true: FPS: 16981 FrameTime: 0.059 ms
[texture] texture-filter=nearest: FPS: 15418 FrameTime: 0.065 ms
[texture] texture-filter=linear: FPS: 15376 FrameTime: 0.065 ms
[texture] texture-filter=mipmap: FPS: 15605 FrameTime: 0.064 ms
[shading] shading=gouraud: FPS: 15619 FrameTime: 0.064 ms
[shading] shading=blinn-phong-inf: FPS: 13949 FrameTime: 0.072 ms
[shading] shading=phong: FPS: 14381 FrameTime: 0.070 ms
[shading] shading=cel: FPS: 14438 FrameTime: 0.069 ms
[bump] bump-render=high-poly: FPS: 11863 FrameTime: 0.084 ms
[bump] bump-render=normals: FPS: 16360 FrameTime: 0.061 ms
[bump] bump-render=height: FPS: 15865 FrameTime: 0.063 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 11650 FrameTime: 0.086 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 7664 FrameTime: 0.130 ms
[pulsar] light=false:quads=5:texture=false: FPS: 15176 FrameTime: 0.066 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 5565 FrameTime: 0.180 ms
[desktop] effect=shadow:windows=4: FPS: 9850 FrameTime: 0.102 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1605 FrameTime: 0.623 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1800 FrameTime: 0.556 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1750 FrameTime: 0.571 ms
[ideas] speed=duration: FPS: 13652 FrameTime: 0.073 ms
[jellyfish] <default>: FPS: 11006 FrameTime: 0.091 ms
[terrain] <default>: FPS: 1108 FrameTime: 0.903 ms
[shadow] <default>: FPS: 11973 FrameTime: 0.084 ms
[refract] <default>: FPS: 3850 FrameTime: 0.260 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 16019 FrameTime: 0.062 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 15149 FrameTime: 0.066 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 15871 FrameTime: 0.063 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 15809 FrameTime: 0.063 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 14756 FrameTime: 0.068 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 13753 FrameTime: 0.073 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 14570 FrameTime: 0.069 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 13620 FrameTime: 0.073 ms
=======================================================
                                  glmark2 Score: 11877 
=======================================================

---

### Post by Ploddit on 2016-03-18
Was trying to confirm my old GPU wasn't malfunctioning - seems par for the course.

=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce 9300 GE/PCIe/SSE2
    GL_VERSION:    3.3.0 NVIDIA 340.96
=======================================================
[build] use-vbo=false: FPS: 480 FrameTime: 2.083 ms
[build] use-vbo=true: FPS: 489 FrameTime: 2.045 ms
[texture] texture-filter=nearest: FPS: 409 FrameTime: 2.445 ms
[texture] texture-filter=linear: FPS: 407 FrameTime: 2.457 ms
[texture] texture-filter=mipmap: FPS: 422 FrameTime: 2.370 ms
[shading] shading=gouraud: FPS: 406 FrameTime: 2.463 ms
[shading] shading=blinn-phong-inf: FPS: 381 FrameTime: 2.625 ms
[shading] shading=phong: FPS: 305 FrameTime: 3.279 ms
[bump] bump-render=high-poly: FPS: 265 FrameTime: 3.774 ms
[bump] bump-render=normals: FPS: 474 FrameTime: 2.110 ms
[bump] bump-render=height: FPS: 456 FrameTime: 2.193 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 283 FrameTime: 3.534 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 151 FrameTime: 6.623 ms
[pulsar] light=false:quads=5:texture=false: FPS: 344 FrameTime: 2.907 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 145 FrameTime: 6.897 ms
[desktop] effect=shadow:windows=4: FPS: 235 FrameTime: 4.255 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 179 FrameTime: 5.587 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 239 FrameTime: 4.184 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 209 FrameTime: 4.785 ms
[ideas] speed=duration: FPS: 334 FrameTime: 2.994 ms
[jellyfish] <default>: FPS: 235 FrameTime: 4.255 ms
[terrain] <default>: FPS: 22 FrameTime: 45.455 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 429 FrameTime: 2.331 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 306 FrameTime: 3.268 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 429 FrameTime: 2.331 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 404 FrameTime: 2.475 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 302 FrameTime: 3.311 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 398 FrameTime: 2.513 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 382 FrameTime: 2.618 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 321 FrameTime: 3.115 ms
=======================================================
                                  glmark2 Score: 328 


Linux Mint 17.3 cinnamon(2.8.6) 64bit in office desktop enviroment
Kernel 3.19.0-32
Intel E2180 Dual core @ 2.0
 4GB RAM
 Nvidia G98  9300GE 256VRAM
Screen res was 1920X1080 but glmark2 runs in a liitle window


Thanks seems it's as bad as normal it was having issues with supertuxcart on HD - I thought it'd of managed that.

I removed the GPU to compare with the inbuilt X4500 on the G41 mobo

  glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) G41 
    GL_VERSION:    2.1 Mesa 10.5.9
=======================================================
[build] use-vbo=false: FPS: 272 FrameTime: 3.676 ms
[build] use-vbo=true: FPS: 276 FrameTime: 3.623 ms
[texture] texture-filter=nearest: FPS: 275 FrameTime: 3.636 ms
[texture] texture-filter=linear: FPS: 272 FrameTime: 3.676 ms
[texture] texture-filter=mipmap: FPS: 271 FrameTime: 3.690 ms
[shading] shading=gouraud: FPS: 212 FrameTime: 4.717 ms
[shading] shading=blinn-phong-inf: FPS: 208 FrameTime: 4.808 ms
[shading] shading=phong: FPS: 171 FrameTime: 5.848 ms
[bump] bump-render=high-poly: FPS: 130 FrameTime: 7.692 ms
[bump] bump-render=normals: FPS: 284 FrameTime: 3.521 ms
[bump] bump-render=height: FPS: 258 FrameTime: 3.876 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 157 FrameTime: 6.369 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 100 FrameTime: 10.000 ms
[pulsar] light=false:quads=5:texture=false: FPS: 246 FrameTime: 4.065 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 89 FrameTime: 11.236 ms
[desktop] effect=shadow:windows=4: FPS: 120 FrameTime: 8.333 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 122 FrameTime: 8.197 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 120 FrameTime: 8.333 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 144 FrameTime: 6.944 ms
[ideas] speed=duration: FPS: 200 FrameTime: 5.000 ms
[jellyfish] <default>: FPS: 132 FrameTime: 7.576 ms
[terrain] <default>: FPS: 17 FrameTime: 58.824 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 278 FrameTime: 3.597 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 218 FrameTime: 4.587 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 278 FrameTime: 3.597 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 270 FrameTime: 3.704 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 197 FrameTime: 5.076 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 261 FrameTime: 3.831 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 261 FrameTime: 3.831 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 208 FrameTime: 4.808 ms
=======================================================
                                  glmark2 Score: 201 
=======================================================

Linux Mint 17.3 cinnamon(2.8.6) 64bit in office desktop enviroment
Kernel 3.19.0-32
Intel E2180 Dual core @ 2.0
 4GB RAM
 Intel GMA X4500 
Screen res was 1920X1080 but glmark2 runs in a liitle window

---

### Post by Retlol on 2016-03-29
```
glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     X.Org
    GL_RENDERER:   Gallium 0.4 on AMD BONAIRE (DRM 2.43.0, LLVM 3.6.2)
    GL_VERSION:    3.0 Mesa 11.0.2
=======================================================
[build] use-vbo=false: FPS: 3775 FrameTime: 0.265 ms
[build] use-vbo=true: FPS: 15708 FrameTime: 0.064 ms
[texture] texture-filter=nearest: FPS: 13262 FrameTime: 0.075 ms
[texture] texture-filter=linear: FPS: 13304 FrameTime: 0.075 ms
[texture] texture-filter=mipmap: FPS: 14577 FrameTime: 0.069 ms
[shading] shading=gouraud: FPS: 13385 FrameTime: 0.075 ms
[shading] shading=blinn-phong-inf: FPS: 13537 FrameTime: 0.074 ms
[shading] shading=phong: FPS: 12623 FrameTime: 0.079 ms
[shading] shading=cel: FPS: 12461 FrameTime: 0.080 ms
[bump] bump-render=high-poly: FPS: 8216 FrameTime: 0.122 ms
[bump] bump-render=normals: FPS: 14409 FrameTime: 0.069 ms
[bump] bump-render=height: FPS: 15495 FrameTime: 0.065 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 11551 FrameTime: 0.087 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 4901 FrameTime: 0.204 ms
[pulsar] light=false:quads=5:texture=false: FPS: 14305 FrameTime: 0.070 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 3242 FrameTime: 0.308 ms
[desktop] effect=shadow:windows=4: FPS: 6831 FrameTime: 0.146 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 955 FrameTime: 1.047 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1197 FrameTime: 0.835 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1039 FrameTime: 0.962 ms
[ideas] speed=duration: FPS: 3401 FrameTime: 0.294 ms
[jellyfish] <default>: FPS: 6918 FrameTime: 0.145 ms
[terrain] <default>: FPS: 632 FrameTime: 1.582 ms
[shadow] <default>: FPS: 3129 FrameTime: 0.320 ms
[refract] <default>: FPS: 826 FrameTime: 1.211 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 4350 FrameTime: 0.230 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 4477 FrameTime: 0.223 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 4508 FrameTime: 0.222 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 4557 FrameTime: 0.219 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 4593 FrameTime: 0.218 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 4467 FrameTime: 0.224 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 4244 FrameTime: 0.236 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 4467 FrameTime: 0.224 ms
=======================================================
                                  glmark2 Score: 7434 
=======================================================
```

i3 4160 - MSI R7 360 2GB OC
Open source drivers

---

### Post by Retlol on 2016-03-30
Switched to closed source drivers:

```
glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   AMD Radeon (TM) R7 360 Series 
    GL_VERSION:    4.5.13399 Compatibility Profile Context 15.201.1151
=======================================================
[build] use-vbo=false: FPS: 4218 FrameTime: 0.237 ms
[build] use-vbo=true: FPS: 13512 FrameTime: 0.074 ms
[texture] texture-filter=nearest: FPS: 11323 FrameTime: 0.088 ms
[texture] texture-filter=linear: FPS: 11402 FrameTime: 0.088 ms
[texture] texture-filter=mipmap: FPS: 11979 FrameTime: 0.083 ms
[shading] shading=gouraud: FPS: 11398 FrameTime: 0.088 ms
[shading] shading=blinn-phong-inf: FPS: 11458 FrameTime: 0.087 ms
[shading] shading=phong: FPS: 11120 FrameTime: 0.090 ms
[shading] shading=cel: FPS: 11334 FrameTime: 0.088 ms
[bump] bump-render=high-poly: FPS: 7842 FrameTime: 0.128 ms
[bump] bump-render=normals: FPS: 13014 FrameTime: 0.077 ms
[bump] bump-render=height: FPS: 11785 FrameTime: 0.085 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 4907 FrameTime: 0.204 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 3624 FrameTime: 0.276 ms
[pulsar] light=false:quads=5:texture=false: FPS: 9977 FrameTime: 0.100 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 3079 FrameTime: 0.325 ms
[desktop] effect=shadow:windows=4: FPS: 2234 FrameTime: 0.448 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 730 FrameTime: 1.370 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1262 FrameTime: 0.792 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 940 FrameTime: 1.064 ms
[ideas] speed=duration: FPS: 4540 FrameTime: 0.220 ms
[jellyfish] <default>: FPS: 7189 FrameTime: 0.139 ms
[terrain] <default>: FPS: 645 FrameTime: 1.550 ms
[shadow] <default>: FPS: 3960 FrameTime: 0.253 ms
[refract] <default>: FPS: 916 FrameTime: 1.092 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 12532 FrameTime: 0.080 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 12459 FrameTime: 0.080 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 12092 FrameTime: 0.083 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 12055 FrameTime: 0.083 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 12348 FrameTime: 0.081 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 11876 FrameTime: 0.084 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 11224 FrameTime: 0.089 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 12389 FrameTime: 0.081 ms
=======================================================
                                  glmark2 Score: 8223 
=======================================================

```

Quite a bit better than the open source drivers.

---

### Post by brianewalsh2 on 2016-04-03
Ive never tried running a gfx benchmark under linux. guess my system is showing its age a little.
i5 3570k

=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 660 Ti/PCIe/SSE2
    GL_VERSION:    4.5.0 NVIDIA 352.63
=======================================================
[build] use-vbo=false: FPS: 9597 FrameTime: 0.104 ms
[build] use-vbo=true: FPS: 12074 FrameTime: 0.083 ms
[texture] texture-filter=nearest: FPS: 8070 FrameTime: 0.124 ms
[texture] texture-filter=linear: FPS: 12929 FrameTime: 0.077 ms
[texture] texture-filter=mipmap: FPS: 13790 FrameTime: 0.073 ms
[shading] shading=gouraud: FPS: 12959 FrameTime: 0.077 ms
[shading] shading=blinn-phong-inf: FPS: 12954 FrameTime: 0.077 ms
[shading] shading=phong: FPS: 12824 FrameTime: 0.078 ms
[bump] bump-render=high-poly: FPS: 9522 FrameTime: 0.105 ms
[bump] bump-render=normals: FPS: 15497 FrameTime: 0.065 ms
[bump] bump-render=height: FPS: 15143 FrameTime: 0.066 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 10478 FrameTime: 0.095 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 7574 FrameTime: 0.132 ms
[pulsar] light=false:quads=5:texture=false: FPS: 13455 FrameTime: 0.074 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 4360 FrameTime: 0.229 ms
[desktop] effect=shadow:windows=4: FPS: 6112 FrameTime: 0.164 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1139 FrameTime: 0.878 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1387 FrameTime: 0.721 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1019 FrameTime: 0.981 ms
[ideas] speed=duration: FPS: 9840 FrameTime: 0.102 ms
[jellyfish] <default>: FPS: 6960 FrameTime: 0.144 ms
[terrain] <default>: FPS: 794 FrameTime: 1.259 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 12423 FrameTime: 0.080 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 12386 FrameTime: 0.081 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 12545 FrameTime: 0.080 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 12423 FrameTime: 0.080 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 12328 FrameTime: 0.081 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 12434 FrameTime: 0.080 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 12452 FrameTime: 0.080 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 12382 FrameTime: 0.081 ms
=======================================================
                                  glmark2 Score: 9928 
=======================================================

---

### Post by rainmaker522 on 2016-04-10
Xwayland on HP Elitebook notebook. I believe this is a i965 chip.

In standard window size, 1366x768 resolution.

=======================================================
    glmark2 2014.03
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) Ivybridge Mobile 
    GL_VERSION:    3.0 Mesa 11.2.0
=======================================================
[build] use-vbo=false: FPS: 1972 FrameTime: 0.507 ms
[build] use-vbo=true: FPS: 2219 FrameTime: 0.451 ms
[texture] texture-filter=nearest: FPS: 2527 FrameTime: 0.396 ms
[texture] texture-filter=linear: FPS: 2521 FrameTime: 0.397 ms
[texture] texture-filter=mipmap: FPS: 2544 FrameTime: 0.393 ms
[shading] shading=gouraud: FPS: 1540 FrameTime: 0.649 ms
[shading] shading=blinn-phong-inf: FPS: 1530 FrameTime: 0.654 ms
[shading] shading=phong: FPS: 1482 FrameTime: 0.675 ms
[shading] shading=cel: FPS: 1473 FrameTime: 0.679 ms
[bump] bump-render=high-poly: FPS: 728 FrameTime: 1.374 ms
[bump] bump-render=normals: FPS: 2560 FrameTime: 0.391 ms
[bump] bump-render=height: FPS: 2230 FrameTime: 0.448 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 1373 FrameTime: 0.728 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 726 FrameTime: 1.377 ms
[pulsar] light=false:quads=5:texture=false: FPS: 1800 FrameTime: 0.556 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 572 FrameTime: 1.748 ms
[desktop] effect=shadow:windows=4: FPS: 1028 FrameTime: 0.973 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 312 FrameTime: 3.205 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 724 FrameTime: 1.381 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 355 FrameTime: 2.817 ms
[ideas] speed=duration: FPS: 1467 FrameTime: 0.682 ms
[jellyfish] <default>: FPS: 1115 FrameTime: 0.897 ms
[terrain] <default>: FPS: 133 FrameTime: 7.519 ms
[shadow] <default>: FPS: 714 FrameTime: 1.401 ms
[refract] <default>: FPS: 203 FrameTime: 4.926 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 2171 FrameTime: 0.461 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 2205 FrameTime: 0.454 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 2174 FrameTime: 0.460 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 2187 FrameTime: 0.457 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 2245 FrameTime: 0.445 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 2192 FrameTime: 0.456 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 2187 FrameTime: 0.457 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 2114 FrameTime: 0.473 ms
=======================================================
                                  glmark2 Score: 1555 
=======================================================

---

### Post by The_Woodpecker on 2016-04-11
Here is my results (windowed mode)

Running on Ubuntu 12.04 on my HP notebook:
** Failed to set swap interval. Results may be bounded above by refresh rate.
=======================================================
    glmark2 2011.09
=======================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   AMD Radeon HD 8210
    GL_VERSION:    4.3.12798 Compatibility Profile Context 13.35.1005
=======================================================
[build] use-vbo=false:  FPS: 241
[build] use-vbo=true:  FPS: 587
[texture] texture-filter=nearest:  FPS: 540
[texture] texture-filter=linear:  FPS: 546
[texture] texture-filter=mipmap:  FPS: 563
[shading] shading=gouraud:  FPS: 515
[shading] shading=blinn-phong-inf:  FPS: 515
[shading] shading=phong:  FPS: 475
[bump] bump-render=high-poly:  FPS: 438
[bump] bump-render=normals:  FPS: 516
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;:  FPS: 275
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;:  FPS: 194
[pulsar] light=false:quads=5:texture=false:  FPS: 442
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4:  FPS: 164
[conditionals] fragment-steps=0:vertex-steps=0:  FPS: 516
[conditionals] fragment-steps=5:vertex-steps=0:  FPS: 520
[conditionals] fragment-steps=0:vertex-steps=5:  FPS: 538
[function] fragment-complexity=low:fragment-steps=5:  FPS: 539
[function] fragment-complexity=medium:fragment-steps=5:  FPS: 527
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5:  FPS: 505
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5:  FPS: 469
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5:  FPS: 468
=======================================================
                                  glmark2 Score: 458 
=======================================================

---

### Post by oldrocker99 on 2016-04-13
On my nVidia 960 desktop, glmark2 returns a segmentation fault:(, a bug I've reported. On my newly-acquired AMD-E300 Toshiba C-855D-S5104, I got this:
```
oldrocker99@oldrocker99-Satellite-C855D:~$ glmark2 --fullscreen
=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     X.Org
    GL_RENDERER:   Gallium 0.4 on AMD PALM (DRM 2.43.0, LLVM 3.8.0)
    GL_VERSION:    3.0 Mesa 11.2.0
=======================================================
[build] use-vbo=false: FPS: 59 FrameTime: 16.949 ms
[build] use-vbo=true: FPS: 60 FrameTime: 16.667 ms
[texture] texture-filter=nearest: FPS: 60 FrameTime: 16.667 ms
[texture] texture-filter=linear: FPS: 60 FrameTime: 16.667 ms
[texture] texture-filter=mipmap: FPS: 60 FrameTime: 16.667 ms
[shading] shading=gouraud: FPS: 60 FrameTime: 16.667 ms
[shading] shading=blinn-phong-inf: FPS: 60 FrameTime: 16.667 ms
[shading] shading=phong: FPS: 60 FrameTime: 16.667 ms
[shading] shading=cel: FPS: 60 FrameTime: 16.667 ms
[bump] bump-render=high-poly: FPS: 60 FrameTime: 16.667 ms
[bump] bump-render=normals: FPS: 60 FrameTime: 16.667 ms
[bump] bump-render=height: FPS: 60 FrameTime: 16.667 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 60 FrameTime: 16.667 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 60 FrameTime: 16.667 ms
[pulsar] light=false:quads=5:texture=false: FPS: 60 FrameTime: 16.667 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 60 FrameTime: 16.667 ms
[desktop] effect=shadow:windows=4: FPS: 60 FrameTime: 16.667 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 60 FrameTime: 16.667 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 60 FrameTime: 16.667 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 60 FrameTime: 16.667 ms
[ideas] speed=duration: FPS: 60 FrameTime: 16.667 ms
[jellyfish] <default>: FPS: 60 FrameTime: 16.667 ms
[terrain] <default>: FPS: 28 FrameTime: 35.714 ms
[shadow] <default>: FPS: 60 FrameTime: 16.667 ms
[refract] <default>: FPS: 30 FrameTime: 33.333 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 60 FrameTime: 16.667 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 60 FrameTime: 16.667 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 60 FrameTime: 16.667 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 60 FrameTime: 16.667 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 60 FrameTime: 16.667 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 60 FrameTime: 16.667 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 60 FrameTime: 16.667 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 60 FrameTime: 16.667 ms
=======================================================
                                  glmark2 Score: 58 
=======================================================
oldrocker99@oldrocker99-Satellite-C855D:~$ glmark2
=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     X.Org
    GL_RENDERER:   Gallium 0.4 on AMD PALM (DRM 2.43.0, LLVM 3.8.0)
    GL_VERSION:    3.0 Mesa 11.2.0
=======================================================
[build] use-vbo=false: FPS: 306 FrameTime: 3.268 ms
[build] use-vbo=true: FPS: 410 FrameTime: 2.439 ms
[texture] texture-filter=nearest: FPS: 386 FrameTime: 2.591 ms
[texture] texture-filter=linear: FPS: 385 FrameTime: 2.597 ms
[texture] texture-filter=mipmap: FPS: 393 FrameTime: 2.545 ms
[shading] shading=gouraud: FPS: 366 FrameTime: 2.732 ms
[shading] shading=blinn-phong-inf: FPS: 364 FrameTime: 2.747 ms
[shading] shading=phong: FPS: 359 FrameTime: 2.786 ms
[shading] shading=cel: FPS: 350 FrameTime: 2.857 ms
[bump] bump-render=high-poly: FPS: 294 FrameTime: 3.401 ms
[bump] bump-render=normals: FPS: 408 FrameTime: 2.451 ms
[bump] bump-render=height: FPS: 357 FrameTime: 2.801 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 350 FrameTime: 2.857 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 261 FrameTime: 3.831 ms
[pulsar] light=false:quads=5:texture=false: FPS: 360 FrameTime: 2.778 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 179 FrameTime: 5.587 ms
[desktop] effect=shadow:windows=4: FPS: 230 FrameTime: 4.348 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 76 FrameTime: 13.158 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 84 FrameTime: 11.905 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 95 FrameTime: 10.526 ms
[ideas] speed=duration: FPS: 187 FrameTime: 5.348 ms
[jellyfish] <default>: FPS: 232 FrameTime: 4.310 ms
[terrain] <default>: FPS: 42 FrameTime: 23.810 ms
[shadow] <default>: FPS: 185 FrameTime: 5.405 ms
[refract] <default>: FPS: 52 FrameTime: 19.231 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 409 FrameTime: 2.445 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 387 FrameTime: 2.584 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 412 FrameTime: 2.427 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 406 FrameTime: 2.463 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 339 FrameTime: 2.950 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 406 FrameTime: 2.463 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 408 FrameTime: 2.451 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 272 FrameTime: 3.676 ms
=======================================================
                                  glmark2 Score: 295 
=======================================================

```

---

### Post by Retlol on 2016-05-26
MSI R7 360 OC.

The latest drivers have actually even made my score worse. The Radeon driver isn't very good. On Ubuntu 15.10 with  Mesa 11.0.2 I had a score of 7434, with fglrx I had a score of 8223. On Ubuntu 16.04 with Mesa 11.2.0 I have a score of 6334. Basically a 20% performance decrease. 

I want to cry. To put this into perspective I own Tomb Raider (2013) on Steam. On Windows I can play this game with ultra/high settings with 60fps with a lot of eyecandy enabled (not all!). On Ubuntu I can't even use high quality presets and have to play on medium settings with everything turned off to get similar (slighlty higher) fps. I'm not sure if the framedrops on Linux are with the port or the driver, in any case, there's a lot of drops (to 1-10 fps for a few seconds) while the game runs flawlessly on Windows.

rw@Ubuntu:~$ glmark2
=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     X.Org
    GL_RENDERER:   Gallium 0.4 on AMD BONAIRE (DRM 2.43.0, LLVM 3.8.0)
    GL_VERSION:    3.0 Mesa 11.2.0
=======================================================
[build] use-vbo=false: FPS: 5347 FrameTime: 0.187 ms
[build] use-vbo=true: FPS: 9002 FrameTime: 0.111 ms
[texture] texture-filter=nearest: FPS: 7807 FrameTime: 0.128 ms
[texture] texture-filter=linear: FPS: 7732 FrameTime: 0.129 ms
[texture] texture-filter=mipmap: FPS: 8113 FrameTime: 0.123 ms
[shading] shading=gouraud: FPS: 7954 FrameTime: 0.126 ms
[shading] shading=blinn-phong-inf: FPS: 7906 FrameTime: 0.126 ms
[shading] shading=phong: FPS: 7815 FrameTime: 0.128 ms
[shading] shading=cel: FPS: 7815 FrameTime: 0.128 ms
[bump] bump-render=high-poly: FPS: 5979 FrameTime: 0.167 ms
[bump] bump-render=normals: FPS: 8688 FrameTime: 0.115 ms
[bump] bump-render=height: FPS: 8464 FrameTime: 0.118 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 7671 FrameTime: 0.130 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 4588 FrameTime: 0.218 ms
[pulsar] light=false:quads=5:texture=false: FPS: 8024 FrameTime: 0.125 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 3068 FrameTime: 0.326 ms
[desktop] effect=shadow:windows=4: FPS: 5028 FrameTime: 0.199 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 976 FrameTime: 1.025 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1183 FrameTime: 0.845 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1059 FrameTime: 0.944 ms
[ideas] speed=duration: FPS: 3645 FrameTime: 0.274 ms
[jellyfish] <default>: FPS: 5631 FrameTime: 0.178 ms
[terrain] <default>: FPS: 698 FrameTime: 1.433 ms
[shadow] <default>: FPS: 4721 FrameTime: 0.212 ms
[refract] <default>: FPS: 944 FrameTime: 1.059 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 8667 FrameTime: 0.115 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 8622 FrameTime: 0.116 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 8767 FrameTime: 0.114 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 8651 FrameTime: 0.116 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 8759 FrameTime: 0.114 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 8699 FrameTime: 0.115 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 8724 FrameTime: 0.115 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 8610 FrameTime: 0.116 ms
=======================================================
                                  glmark2 Score: 6344 
=======================================================

---

### Post by heiko_s on 2016-08-04
heiko@woody ~ $ glmark2
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   Quadro 2000/PCIe/SSE2
    GL_VERSION:    4.5.0 NVIDIA 352.63
=======================================================
[build] use-vbo=false: FPS: 3239 FrameTime: 0.309 ms
[build] use-vbo=true: FPS: 4307 FrameTime: 0.232 ms
[texture] texture-filter=nearest: FPS: 4030 FrameTime: 0.248 ms
[texture] texture-filter=linear: FPS: 3970 FrameTime: 0.252 ms
[texture] texture-filter=mipmap: FPS: 4190 FrameTime: 0.239 ms
[shading] shading=gouraud: FPS: 3867 FrameTime: 0.259 ms
[shading] shading=blinn-phong-inf: FPS: 3907 FrameTime: 0.256 ms
[shading] shading=phong: FPS: 3661 FrameTime: 0.273 ms
[bump] bump-render=high-poly: FPS: 2278 FrameTime: 0.439 ms
[bump] bump-render=normals: FPS: 4740 FrameTime: 0.211 ms
[bump] bump-render=height: FPS: 4653 FrameTime: 0.215 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 2258 FrameTime: 0.443 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 1008 FrameTime: 0.992 ms
[pulsar] light=false:quads=5:texture=false: FPS: 3765 FrameTime: 0.266 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 989 FrameTime: 1.011 ms
[desktop] effect=shadow:windows=4: FPS: 2032 FrameTime: 0.492 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 969 FrameTime: 1.032 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1233 FrameTime: 0.811 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1060 FrameTime: 0.943 ms
[ideas] speed=duration: FPS: 2824 FrameTime: 0.354 ms
[jellyfish] <default>: FPS: 2168 FrameTime: 0.461 ms
[terrain] <default>: FPS: 218 FrameTime: 4.587 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 4070 FrameTime: 0.246 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 3020 FrameTime: 0.331 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 4100 FrameTime: 0.244 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 4072 FrameTime: 0.246 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 3064 FrameTime: 0.326 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 4055 FrameTime: 0.247 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 4051 FrameTime: 0.247 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 3678 FrameTime: 0.272 ms
=======================================================
                                  glmark2 Score: 3049 
=======================================================

---

### Post by jackccrawford on 2016-08-08
Just tested with the new NVIDIA Titan X (Pascal) released last week.
Are you sitting down?

=======================================================
                                  glmark2 Score: 17737 
=======================================================

Link for the card:  [http://www.geforce.com/hardware/10series/titan-x-pascal](http://www.geforce.com/hardware/10series/titan-x-pascal)

Machine details:
LGA 2011 Intel Six Core 3.4GHZ CPU
128GB of RAM
Titan X 12GB

---

### Post by cayan on 2016-08-19
GLMark built from source with flavor x11-gl. 

My system:
Resolution: 1920x1080
Desktop

CPU: i7 9700k

I ran with the integrated graphics and the score was like ~350.

=======================================================
    glmark2 2014.03
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 950/PCIe/SSE2
    GL_VERSION:    4.5.0 NVIDIA 370.23
=======================================================
=======================================================
                                  glmark2 Score: 9853 
=======================================================

---

### Post by mhjessen2 on 2016-09-17
Wow! Some of these numbers are just amazing! As for my workhorse Toshiba Satellite C55-C5241;

Operating System: Ubuntu 16.04.1 LTS
Kernel: Linux 4.4.0-36-generic
Architecture: x86-64
Model name: Intel(R) Core(TM) i5-5200U CPU @ 2.20GHz

$ glmark2
=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) HD Graphics 5500 (Broadwell GT2) 
    GL_VERSION:    3.0 Mesa 12.1.0-devel
=======================================================
glmark2 Score: 1438

$ glmark2 --fullscreen
glmark2 Score: 875

---

### Post by pqwoerituytrueiwoq on 2016-09-17
```
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 650 Ti BOOST/PCIe/SSE2
    GL_VERSION:    4.5.0 NVIDIA 367.44
=======================================================
=======================================================
                                  glmark2 Score: 10240 
=======================================================

```* GPU is overclocked

---

### Post by Scott Deagan on 2016-09-28
On an nVidia GTX 1070, running proprietary driver 370.28:

**glmark2**
Score: 17045

**glmark2 --s 1920x1080**
Score: 9026

and on a 2560x1440 monitor:

**glmark2 --fullscreen**
Score: 4286

---

### Post by adam-tuba on 2016-12-16
AMD Radeon HD 7770 + AMD FX 6300 Black
=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     X.Org
    GL_RENDERER:   Gallium 0.4 on AMD CAPE VERDE (DRM 2.43.0, LLVM 3.8.0)
    GL_VERSION:    3.0 Mesa 11.2.0
=======================================================
...
=======================================================
                                  glmark2 Score: 2208 
=======================================================

---

### Post by misanthropos on 2017-03-20
Since I play Enemy Territory I noticed not getting the same FPS as I used to with the nvidia-blob but I cant use older nvidia drivers with current kernels. 
However with nouveau it runs quite fast. 

=======================================================
    glmark2 2014.03
=======================================================
    OpenGL Information
    GL_VENDOR:     nouveau
    GL_RENDERER:   Gallium 0.4 on NVE6
    GL_VERSION:    3.0 Mesa 17.1.0-devel (git-5b5ffb7)
=======================================================
=======================================================
                                  glmark2 Score: 4570
=======================================================

with nvidia-blob glmark2 Score: 2967 which is about the result of 2 others with the same graphics card... wtf?

Resolution 800x600
Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
NVIDIA Corporation GK106 [GeForce GTX 650 Ti] (rev a1)

---

### Post by uNoubu8a on 2017-03-20
AMD HD 6850 1920x1080 Gnome 3.18 --fullscreen

glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     X.Org
    GL_RENDERER:   Gallium 0.4 on AMD BARTS (DRM 2.46.0 / 4.8.0-41-generic, LLVM 3.8.0)
    GL_VERSION:    3.0 Mesa 12.0.6

=======================================================
                                  glmark2 Score: 120 
=======================================================

:'(

---

### Post by hjerezano on 2017-05-07
"uname -a"
Ubuntu 17.04 Latitude-E7450 4.11.0-041100-generic #201705041534 SMP Thu May 4 19:36:05U UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


FROM TTY1
"startx /usr/bin/glmark2 >> GL_BenchMark"


pkexec version 0.105
=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) HD Graphics 5500 (Broadwell GT2) 
    GL_VERSION:    3.0 Mesa 17.2.0-devel - padoka PPA
=======================================================
=======================================================
                                  glmark2 Score: 1865 
=======================================================




FROM TTY1
"startx /usr/bin/glmark2 -s 1920x1080 >> GL_BenchMark"


pkexec version 0.105
=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) HD Graphics 5500 (Broadwell GT2) 
    GL_VERSION:    3.0 Mesa 17.2.0-devel - padoka PPA
=======================================================
=======================================================
                                  glmark2 Score: 493 
=======================================================

---

### Post by kaspergyselinck on 2018-05-02
-------------------------:~$ glmark2 --fullscreen
=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 1060 6GB/PCIe/SSE2
    GL_VERSION:    4.6.0 NVIDIA 396.18
=======================================================
[build] use-vbo=false: FPS: 6595 FrameTime: 0.152 ms
[build] use-vbo=true: FPS: 9811 FrameTime: 0.102 ms
[texture] texture-filter=nearest: FPS: 8995 FrameTime: 0.111 ms
[texture] texture-filter=linear: FPS: 8936 FrameTime: 0.112 ms
[texture] texture-filter=mipmap: FPS: 8962 FrameTime: 0.112 ms
[shading] shading=gouraud: FPS: 9476 FrameTime: 0.106 ms
[shading] shading=blinn-phong-inf: FPS: 9670 FrameTime: 0.103 ms
[shading] shading=phong: FPS: 9203 FrameTime: 0.109 ms
[shading] shading=cel: FPS: 8880 FrameTime: 0.113 ms
[bump] bump-render=high-poly: FPS: 7643 FrameTime: 0.131 ms
[bump] bump-render=normals: FPS: 9299 FrameTime: 0.108 ms
[bump] bump-render=height: FPS: 9129 FrameTime: 0.110 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 5095 FrameTime: 0.196 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 2884 FrameTime: 0.347 ms
[pulsar] light=false:quads=5:texture=false: FPS: 8228 FrameTime: 0.122 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 2451 FrameTime: 0.408 ms
[desktop] effect=shadow:windows=4: FPS: 3568 FrameTime: 0.280 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1140 FrameTime: 0.877 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1217 FrameTime: 0.822 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1249 FrameTime: 0.801 ms
[ideas] speed=duration: FPS: 6812 FrameTime: 0.147 ms
[jellyfish] <default>: FPS: 5431 FrameTime: 0.184 ms
[terrain] <default>: FPS: 433 FrameTime: 2.309 ms
[shadow] <default>: FPS: 5843 FrameTime: 0.171 ms
[refract] <default>: FPS: 2303 FrameTime: 0.434 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 8554 FrameTime: 0.117 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 8407 FrameTime: 0.119 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 8526 FrameTime: 0.117 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 8463 FrameTime: 0.118 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 8212 FrameTime: 0.122 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 8391 FrameTime: 0.119 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 8498 FrameTime: 0.118 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 8272 FrameTime: 0.121 ms
=======================================================
                                  glmark2 Score: 6684 
=======================================================

---

### Post by pqwoerituytrueiwoq on 2018-05-02
*GPU is overclocked as high as possible without a hardware mod (Sustained boost clock of 1.2Ghz +/-4Hz)
```
chad@Z97Killer:~$ screenfetch 
                          ./+o+-       chad@Z97Killer
                  yyyyy- -yyyyyy+      OS: Ubuntu 18.04 bionic
               ://+//////-yyyyyyo      Kernel: x86_64 Linux 4.15.0-20-generic
           .++ .:/++++++/-.+sss/`      Uptime: 5h 47m
         .:++o:  /++++++++/:--:/-      Packages: 2165
        o:+o+:++.`..```.-/oo+++++/     Shell: bash 4.4.19
       .:+o:+o/.          `+sssoo+/    Resolution: 1920x1080
  .++/+:+oo+o:`             /sssooo.   WM: Xfwm4
 /+++//+:`oo+o               /::--:.   WM Theme: Numix-Dark-Blue
 \+/+o+++`o++o               ++////.   GTK3 Theme: Greybird
  .++.o+++oo+:`             /dddhhh.   Disk: 808G / 1.5T (57%)
       .+.o+oo:.          `oddhhhh+    CPU: Intel Core i5-4690K CPU @ 3.9GHz
        \+.++o+o``-````.:ohdhhhhh+     GPU: NVidia GeForce GTX 650 Ti Boost
         `:o+++ `ohhhhhhhhyo++os:      RAM: 2912MB / 15992MB
           .o:`.syhhhhhhh/.oo++o`     
               /osyyyyyyo++ooo+++/    
                   ````` +oo+++o\:    
                          `oo++.  

chad@Z97Killer:~$ glmark2 --fullscreen
=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 650 Ti BOOST/PCIe/SSE2
    GL_VERSION:    4.6.0 NVIDIA 390.48
=======================================================
[build] use-vbo=false: FPS: 4737 FrameTime: 0.211 ms
[build] use-vbo=true: FPS: 5135 FrameTime: 0.195 ms
[texture] texture-filter=nearest: FPS: 4278 FrameTime: 0.234 ms
[texture] texture-filter=linear: FPS: 3996 FrameTime: 0.250 ms
[texture] texture-filter=mipmap: FPS: 4515 FrameTime: 0.221 ms
[shading] shading=gouraud: FPS: 4304 FrameTime: 0.232 ms
[shading] shading=blinn-phong-inf: FPS: 4421 FrameTime: 0.226 ms
[shading] shading=phong: FPS: 4420 FrameTime: 0.226 ms
[shading] shading=cel: FPS: 4156 FrameTime: 0.241 ms
[bump] bump-render=high-poly: FPS: 3771 FrameTime: 0.265 ms
[bump] bump-render=normals: FPS: 4733 FrameTime: 0.211 ms
[bump] bump-render=height: FPS: 4600 FrameTime: 0.217 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 2584 FrameTime: 0.387 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 1469 FrameTime: 0.681 ms
[pulsar] light=false:quads=5:texture=false: FPS: 3785 FrameTime: 0.264 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 1138 FrameTime: 0.879 ms
[desktop] effect=shadow:windows=4: FPS: 1781 FrameTime: 0.561 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1262 FrameTime: 0.792 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1411 FrameTime: 0.709 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1344 FrameTime: 0.744 ms
[ideas] speed=duration: FPS: 3156 FrameTime: 0.317 ms
[jellyfish] <default>: FPS: 2006 FrameTime: 0.499 ms
[terrain] <default>: FPS: 337 FrameTime: 2.967 ms
[shadow] <default>: FPS: 3173 FrameTime: 0.315 ms
[refract] <default>: FPS: 933 FrameTime: 1.072 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 4354 FrameTime: 0.230 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 3652 FrameTime: 0.274 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 4377 FrameTime: 0.228 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 3973 FrameTime: 0.252 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 3389 FrameTime: 0.295 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 3808 FrameTime: 0.263 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 4219 FrameTime: 0.237 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 3668 FrameTime: 0.273 ms
=======================================================
                                  glmark2 Score: 3299 
=======================================================

```

---

### Post by devin11 on 2018-05-09
OS: Ubuntu 18.04 bionic
Kernel: x86_64 Linux 4.15.0-20-generic
Uptime: 11m
Packages: 1729
Shell: bash 4.4.19
Resolution: 5760x1080
DE: GNOME 
WM: GNOME Shell
WM Theme: Adwaita
GTK Theme: Ambiance [GTK2/3]
Icon Theme: ubuntu-mono-dark
Font: Ubuntu 11
CPU: Intel Core i7-8700K @ 12x 4.7GHz [27.8°C]
GPU: GeForce GTX 1080
RAM: 3123MiB / 32092MiB


devin@devin-liquidbeast:~$ glmark2 
=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 1080/PCIe/SSE2
    GL_VERSION:    4.6.0 NVIDIA 390.48
=======================================================
[build] use-vbo=false: FPS: 12404 FrameTime: 0.081 ms
[build] use-vbo=true: FPS: 24898 FrameTime: 0.040 ms
[texture] texture-filter=nearest: FPS: 24099 FrameTime: 0.041 ms
[texture] texture-filter=linear: FPS: 24050 FrameTime: 0.042 ms
[texture] texture-filter=mipmap: FPS: 24162 FrameTime: 0.041 ms
[shading] shading=gouraud: FPS: 20512 FrameTime: 0.049 ms
[shading] shading=blinn-phong-inf: FPS: 21096 FrameTime: 0.047 ms
[shading] shading=phong: FPS: 21962 FrameTime: 0.046 ms
[shading] shading=cel: FPS: 22130 FrameTime: 0.045 ms
[bump] bump-render=high-poly: FPS: 17599 FrameTime: 0.057 ms
[bump] bump-render=normals: FPS: 25045 FrameTime: 0.040 ms
[bump] bump-render=height: FPS: 24753 FrameTime: 0.040 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 20596 FrameTime: 0.049 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 15620 FrameTime: 0.064 ms
[pulsar] light=false:quads=5:texture=false: FPS: 24339 FrameTime: 0.041 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 8745 FrameTime: 0.114 ms
[desktop] effect=shadow:windows=4: FPS: 12213 FrameTime: 0.082 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1788 FrameTime: 0.559 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 2086 FrameTime: 0.479 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1903 FrameTime: 0.525 ms
[ideas] speed=duration: FPS: 15841 FrameTime: 0.063 ms
[jellyfish] <default>: FPS: 18401 FrameTime: 0.054 ms
[terrain] <default>: FPS: 1702 FrameTime: 0.588 ms
[shadow] <default>: FPS: 17716 FrameTime: 0.056 ms
[refract] <default>: FPS: 6290 FrameTime: 0.159 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 22612 FrameTime: 0.044 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 22691 FrameTime: 0.044 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 23208 FrameTime: 0.043 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 23268 FrameTime: 0.043 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 22998 FrameTime: 0.043 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 23098 FrameTime: 0.043 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 23203 FrameTime: 0.043 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 23101 FrameTime: 0.043 ms
=======================================================
                                  glmark2 Score: 18003 
=======================================================

---

### Post by conormcgregor on 2018-07-24
I just tested an old HD 5870, with fx 6300 and standard driver, 5771, not bad for being 9 years old.

```
=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     X.Org
    GL_RENDERER:   AMD CYPRESS (DRM 2.50.0 / 4.15.0-29-generic, LLVM 5.0.0)
    GL_VERSION:    3.0 Mesa 17.2.8
=======================================================
[build] use-vbo=false: FPS: 3919 FrameTime: 0.255 ms
[build] use-vbo=true: FPS: 8234 FrameTime: 0.121 ms
[texture] texture-filter=nearest: FPS: 7814 FrameTime: 0.128 ms
[texture] texture-filter=linear: FPS: 7587 FrameTime: 0.132 ms
[texture] texture-filter=mipmap: FPS: 7011 FrameTime: 0.143 ms
[shading] shading=gouraud: FPS: 7378 FrameTime: 0.136 ms
[shading] shading=blinn-phong-inf: FPS: 7741 FrameTime: 0.129 ms
[shading] shading=phong: FPS: 7800 FrameTime: 0.128 ms
[shading] shading=cel: FPS: 7806 FrameTime: 0.128 ms
[bump] bump-render=high-poly: FPS: 4060 FrameTime: 0.246 ms
[bump] bump-render=normals: FPS: 8160 FrameTime: 0.123 ms
[bump] bump-render=height: FPS: 7522 FrameTime: 0.133 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 8240 FrameTime: 0.121 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 5797 FrameTime: 0.173 ms
[pulsar] light=false:quads=5:texture=false: FPS: 6597 FrameTime: 0.152 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 2977 FrameTime: 0.336 ms
[desktop] effect=shadow:windows=4: FPS: 3424 FrameTime: 0.292 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 840 FrameTime: 1.190 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 986 FrameTime: 1.014 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 908 FrameTime: 1.101 ms
[ideas] speed=duration: FPS: 1255 FrameTime: 0.797 ms
[jellyfish] <default>: FPS: 5717 FrameTime: 0.175 ms
[terrain] <default>: FPS: 694 FrameTime: 1.441 ms
[shadow] <default>: FPS: 3484 FrameTime: 0.287 ms
[refract] <default>: FPS: 1139 FrameTime: 0.878 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 8122 FrameTime: 0.123 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 7913 FrameTime: 0.126 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 7698 FrameTime: 0.130 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 8314 FrameTime: 0.120 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 8474 FrameTime: 0.118 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 8317 FrameTime: 0.120 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 8310 FrameTime: 0.120 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 6212 FrameTime: 0.161 ms
=======================================================
                                  glmark2 Score: 5771 
=======================================================
```

Just performed same test with HD 7770, 1GB DDR5, 4946 points, better than expected compared with the HD 5870.

```
=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     X.Org
    GL_RENDERER:   AMD CAPE VERDE (DRM 2.50.0 / 4.15.0-29-generic, LLVM 5.0.0)
    GL_VERSION:    3.0 Mesa 17.2.8
=======================================================
[build] use-vbo=false: FPS: 3723 FrameTime: 0.269 ms
[build] use-vbo=true: FPS: 6886 FrameTime: 0.145 ms
[texture] texture-filter=nearest: FPS: 6307 FrameTime: 0.159 ms
[texture] texture-filter=linear: FPS: 6343 FrameTime: 0.158 ms
[texture] texture-filter=mipmap: FPS: 6606 FrameTime: 0.151 ms
[shading] shading=gouraud: FPS: 5779 FrameTime: 0.173 ms
[shading] shading=blinn-phong-inf: FPS: 5790 FrameTime: 0.173 ms
[shading] shading=phong: FPS: 5724 FrameTime: 0.175 ms
[shading] shading=cel: FPS: 5734 FrameTime: 0.174 ms
[bump] bump-render=high-poly: FPS: 3742 FrameTime: 0.267 ms
[bump] bump-render=normals: FPS: 7039 FrameTime: 0.142 ms
[bump] bump-render=height: FPS: 6863 FrameTime: 0.146 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 5885 FrameTime: 0.170 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 3650 FrameTime: 0.274 ms
[pulsar] light=false:quads=5:texture=false: FPS: 6151 FrameTime: 0.163 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 2504 FrameTime: 0.399 ms
[desktop] effect=shadow:windows=4: FPS: 3720 FrameTime: 0.269 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 794 FrameTime: 1.259 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 930 FrameTime: 1.075 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 942 FrameTime: 1.062 ms
[ideas] speed=duration: FPS: 2348 FrameTime: 0.426 ms
[jellyfish] <default>: FPS: 4613 FrameTime: 0.217 ms
[terrain] <default>: FPS: 552 FrameTime: 1.812 ms
[shadow] <default>: FPS: 3745 FrameTime: 0.267 ms
[refract] <default>: FPS: 743 FrameTime: 1.346 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 6978 FrameTime: 0.143 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 6906 FrameTime: 0.145 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 6977 FrameTime: 0.143 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 6997 FrameTime: 0.143 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 6959 FrameTime: 0.144 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 7056 FrameTime: 0.142 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 7140 FrameTime: 0.140 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 7105 FrameTime: 0.141 ms
=======================================================
                                  glmark2 Score: 4946 
=======================================================
```

---

### Post by #&amp;thj^% on 2018-07-26
This install is on a SanDisk 64 gig USB 3.0 ThumbDrive

```
OS: Ubuntu 18.04.1 LTS x86_64 
Host: 750-417c 1.01 
Kernel: 4.17.8-041708-lowlatency 
Uptime: 47 mins 
Packages: 2031 
Shell: bash 4.4.19 
Resolution: 1920x1080 
DE: Xfce 
WM: Compiz 
WM Theme: Adwaita 
Theme: Arc-Dark [GTK2] 
Icons: Humanity-Dark [GTK2] 
Terminal: xfce4-terminal 
Terminal Font: DejaVu Sans Mono 11 
CPU: Intel i5-6400 (4) @ 3.300GHz 
GPU: NVIDIA GeForce GTX 560 Ti 
GPU: Intel Integrated Graphics 
Memory: 1540MiB / 11918MiB 
=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 560 Ti/PCIe/SSE2
    GL_VERSION:    4.6.0 NVIDIA 390.77
=======================================================
[build] use-vbo=false: FPS: 5450 FrameTime: 0.183 ms
[build] use-vbo=true: FPS: 9991 FrameTime: 0.100 ms
[texture] texture-filter=nearest: FPS: 9718 FrameTime: 0.103 ms
[texture] texture-filter=linear: FPS: 9663 FrameTime: 0.103 ms
[texture] texture-filter=mipmap: FPS: 10019 FrameTime: 0.100 ms
[shading] shading=gouraud: FPS: 9075 FrameTime: 0.110 ms
[shading] shading=blinn-phong-inf: FPS: 9239 FrameTime: 0.108 ms
[shading] shading=phong: FPS: 8311 FrameTime: 0.120 ms
[shading] shading=cel: FPS: 8356 FrameTime: 0.120 ms
[bump] bump-render=high-poly: FPS: 5499 FrameTime: 0.182 ms
[bump] bump-render=normals: FPS: 10734 FrameTime: 0.093 ms
[bump] bump-render=height: FPS: 10464 FrameTime: 0.096 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 7213 FrameTime: 0.139 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 4141 FrameTime: 0.241 ms
[pulsar] light=false:quads=5:texture=false: FPS: 8194 FrameTime: 0.122 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 2866 FrameTime: 0.349 ms
[desktop] effect=shadow:windows=4: FPS: 5218 FrameTime: 0.192 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1130 FrameTime: 0.885 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1397 FrameTime: 0.716 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1213 FrameTime: 0.824 ms
[ideas] speed=duration: FPS: 7508 FrameTime: 0.133 ms
[jellyfish] <default>: FPS: 5560 FrameTime: 0.180 ms
[terrain] <default>: FPS: 608 FrameTime: 1.645 ms
[shadow] <default>: FPS: 6949 FrameTime: 0.144 ms
[refract] <default>: FPS: 1758 FrameTime: 0.569 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 9438 FrameTime: 0.106 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 7197 FrameTime: 0.139 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 9389 FrameTime: 0.107 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 8715 FrameTime: 0.115 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 8154 FrameTime: 0.123 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 9393 FrameTime: 0.106 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 7941 FrameTime: 0.126 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 7757 FrameTime: 0.129 ms
=======================================================
                                  glmark2 Score: 6916 
=======================================================
```
And same machine with Arch installed:
```
=======================================================
    glmark2 2017.07
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 560 Ti/PCIe/SSE2
    GL_VERSION:    4.6.0 NVIDIA 390.67
=======================================================
[build] use-vbo=false: FPS: 5434 FrameTime: 0.184 ms
[build] use-vbo=true: FPS: 10750 FrameTime: 0.093 ms
[texture] texture-filter=nearest: FPS: 9661 FrameTime: 0.104 ms
[texture] texture-filter=linear: FPS: 9665 FrameTime: 0.103 ms
[texture] texture-filter=mipmap: FPS: 10172 FrameTime: 0.098 ms
[shading] shading=gouraud: FPS: 9396 FrameTime: 0.106 ms
[shading] shading=blinn-phong-inf: FPS: 9520 FrameTime: 0.105 ms
[shading] shading=phong: FPS: 8704 FrameTime: 0.115 ms
[shading] shading=cel: FPS: 8754 FrameTime: 0.114 ms
[bump] bump-render=high-poly: FPS: 5256 FrameTime: 0.190 ms
[bump] bump-render=normals: FPS: 10194 FrameTime: 0.098 ms
[bump] bump-render=height: FPS: 10663 FrameTime: 0.094 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 7354 FrameTime: 0.136 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 4109 FrameTime: 0.243 ms
[pulsar] light=false:quads=5:texture=false: FPS: 9009 FrameTime: 0.111 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 2870 FrameTime: 0.348 ms
[desktop] effect=shadow:windows=4: FPS: 5117 FrameTime: 0.195 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1169 FrameTime: 0.855 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1435 FrameTime: 0.697 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1306 FrameTime: 0.766 ms
[ideas] speed=duration: FPS: 7522 FrameTime: 0.133 ms
[jellyfish] <default>: FPS: 5386 FrameTime: 0.186 ms
[terrain] <default>: FPS: 607 FrameTime: 1.647 ms
[shadow] <default>: FPS: 6879 FrameTime: 0.145 ms
[refract] <default>: FPS: 1754 FrameTime: 0.570 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 9663 FrameTime: 0.103 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 7365 FrameTime: 0.136 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 9676 FrameTime: 0.103 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 9613 FrameTime: 0.104 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 8397 FrameTime: 0.119 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 9656 FrameTime: 0.104 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 9640 FrameTime: 0.104 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 8364 FrameTime: 0.120 ms
=======================================================
                                  glmark2 Score: 7123 
=======================================================

```

---

### Post by monopoli-1977 on 2018-09-12
```
$ glmark2
=======================================================
    glmark2 2017.07
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) HD Graphics 520 (Skylake GT2) 
    GL_VERSION:    3.0 Mesa 18.0.5
=======================================================


=======================================================
                                  glmark2 Score: 941 
=======================================================
```

---

### Post by friedchips2 on 2018-09-27
GTX 1050 bottlenecked by 6G of ECC DDR2 ram and a Core2Duo E6850 @ 3Ghz

```
=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 1050/PCIe/SSE2
    GL_VERSION:    4.6.0 NVIDIA 390.87
=======================================================
[build] use-vbo=false: FPS: 3217 FrameTime: 0.311 ms
[build] use-vbo=true: FPS: 5129 FrameTime: 0.195 ms
[texture] texture-filter=nearest: FPS: 4879 FrameTime: 0.205 ms
[texture] texture-filter=linear: FPS: 4750 FrameTime: 0.211 ms
[texture] texture-filter=mipmap: FPS: 5084 FrameTime: 0.197 ms
[shading] shading=gouraud: FPS: 4601 FrameTime: 0.217 ms
[shading] shading=blinn-phong-inf: FPS: 4605 FrameTime: 0.217 ms
[shading] shading=phong: FPS: 4706 FrameTime: 0.212 ms
[shading] shading=cel: FPS: 4421 FrameTime: 0.226 ms
[bump] bump-render=high-poly: FPS: 3622 FrameTime: 0.276 ms
[bump] bump-render=normals: FPS: 5226 FrameTime: 0.191 ms
[bump] bump-render=height: FPS: 5187 FrameTime: 0.193 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 4345 FrameTime: 0.230 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 3001 FrameTime: 0.333 ms
[pulsar] light=false:quads=5:texture=false: FPS: 4983 FrameTime: 0.201 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 2466 FrameTime: 0.406 ms
[desktop] effect=shadow:windows=4: FPS: 2844 FrameTime: 0.352 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 727 FrameTime: 1.376 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 811 FrameTime: 1.233 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 803 FrameTime: 1.245 ms
[ideas] speed=duration: FPS: 4277 FrameTime: 0.234 ms
[jellyfish] <default>: FPS: 3691 FrameTime: 0.271 ms
[terrain] <default>: FPS: 731 FrameTime: 1.368 ms
[shadow] <default>: FPS: 4202 FrameTime: 0.238 ms
[refract] <default>: FPS: 1708 FrameTime: 0.585 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 5131 FrameTime: 0.195 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 5471 FrameTime: 0.183 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 4808 FrameTime: 0.208 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 5876 FrameTime: 0.170 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 4676 FrameTime: 0.214 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 4684 FrameTime: 0.213 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 4918 FrameTime: 0.203 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 4574 FrameTime: 0.219 ms
=======================================================
                                  glmark2 Score: 3944 
=======================================================
```

Planning a cheap upgrade to get on a modern platform. Just slapped a $100 card into an otherwise antiquated system.



-------UPDATE!!!!!!
Killing compton made way more difference than I would have thought. In Unigine heaven my score is only maybe 50 points different. Like 1950 vs 1900. In glmark2 my score is nearly tripled.
```
=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 1050/PCIe/SSE2
    GL_VERSION:    4.6.0 NVIDIA 390.87
=======================================================
[build] use-vbo=false: FPS: 6731 FrameTime: 0.149 ms
[build] use-vbo=true: FPS: 18592 FrameTime: 0.054 ms
[texture] texture-filter=nearest: FPS: 16314 FrameTime: 0.061 ms
[texture] texture-filter=linear: FPS: 16357 FrameTime: 0.061 ms
[texture] texture-filter=mipmap: FPS: 16605 FrameTime: 0.060 ms
[shading] shading=gouraud: FPS: 15432 FrameTime: 0.065 ms
[shading] shading=blinn-phong-inf: FPS: 15369 FrameTime: 0.065 ms
[shading] shading=phong: FPS: 13458 FrameTime: 0.074 ms
[shading] shading=cel: FPS: 13446 FrameTime: 0.074 ms
[bump] bump-render=high-poly: FPS: 9089 FrameTime: 0.110 ms
[bump] bump-render=normals: FPS: 19040 FrameTime: 0.053 ms
[bump] bump-render=height: FPS: 18822 FrameTime: 0.053 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 11216 FrameTime: 0.089 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 6227 FrameTime: 0.161 ms
[pulsar] light=false:quads=5:texture=false: FPS: 17349 FrameTime: 0.058 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 3076 FrameTime: 0.325 ms
[desktop] effect=shadow:windows=4: FPS: 3698 FrameTime: 0.270 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 753 FrameTime: 1.328 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 824 FrameTime: 1.214 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 836 FrameTime: 1.196 ms
[ideas] speed=duration: FPS: 5820 FrameTime: 0.172 ms
[jellyfish] <default>: FPS: 9898 FrameTime: 0.101 ms
[terrain] <default>: FPS: 845 FrameTime: 1.183 ms
[shadow] <default>: FPS: 9546 FrameTime: 0.105 ms
[refract] <default>: FPS: 2555 FrameTime: 0.391 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 17445 FrameTime: 0.057 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 15574 FrameTime: 0.064 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 17333 FrameTime: 0.058 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 16604 FrameTime: 0.060 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 14739 FrameTime: 0.068 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 16500 FrameTime: 0.061 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 16450 FrameTime: 0.061 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 15043 FrameTime: 0.066 ms
=======================================================
                                  glmark2 Score: 11563 
=======================================================
```

---

### Post by alphacrasher on 2018-10-09
Nvidia Quadro P2000
Dell Precision  7530 laptop with 4K display.

```

$ glmark2 --fullscreen
=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   Quadro P2000/PCIe/SSE2
    GL_VERSION:    4.6.0 NVIDIA 390.77
=======================================================
[build] use-vbo=false: FPS: 1406 FrameTime: 0.711 ms                                                                                                                                              
[build] use-vbo=true: FPS: 1422 FrameTime: 0.703 ms                                                                                                                                               
[texture] texture-filter=nearest: FPS: 1200 FrameTime: 0.833 ms                                                                                                                                   
[texture] texture-filter=linear: FPS: 1205 FrameTime: 0.830 ms                                                                                                                                    
[texture] texture-filter=mipmap: FPS: 1198 FrameTime: 0.835 ms                                                                                                                                    
[shading] shading=gouraud: FPS: 1253 FrameTime: 0.798 ms                                                                                                                                          
[shading] shading=blinn-phong-inf: FPS: 1243 FrameTime: 0.805 ms                                                                                                                                  
[shading] shading=phong: FPS: 1222 FrameTime: 0.818 ms                                                                                                                                            
[shading] shading=cel: FPS: 1233 FrameTime: 0.811 ms                                                                                                                                              
[bump] bump-render=high-poly: FPS: 1313 FrameTime: 0.762 ms                                                                                                                                       
[bump] bump-render=normals: FPS: 1388 FrameTime: 0.720 ms                                                                                                                                         
[bump] bump-render=height: FPS: 1323 FrameTime: 0.756 ms                                                                                                                                          
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 688 FrameTime: 1.453 ms                                                                                                                               
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 363 FrameTime: 2.755 ms                                                                                                                    
[pulsar] light=false:quads=5:texture=false: FPS: 1130 FrameTime: 0.885 ms                                                                                                                         
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 393 FrameTime: 2.545 ms                                                                                               
[desktop] effect=shadow:windows=4: FPS: 596 FrameTime: 1.678 ms                                                                                                                                   
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1042 FrameTime: 0.960 ms                                                                  
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1026 FrameTime: 0.975 ms                                                              
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1062 FrameTime: 0.942 ms                                                                   
[ideas] speed=duration: FPS: 1099 FrameTime: 0.910 ms                                                                                                                                             
[jellyfish] <default>: FPS: 699 FrameTime: 1.431 ms                                                                                                                                               
[terrain] <default>: FPS: 107 FrameTime: 9.346 ms                                                                                                                                                 
[shadow] <default>: FPS: 983 FrameTime: 1.017 ms                                                                                                                                                  
[refract] <default>: FPS: 256 FrameTime: 3.906 ms                                                                                                                                                 
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 1205 FrameTime: 0.830 ms                                                                                                                     
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 1080 FrameTime: 0.926 ms                                                                                                                     
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 1126 FrameTime: 0.888 ms                                                                                                                     
[function] fragment-complexity=low:fragment-steps=5: FPS: 1120 FrameTime: 0.893 ms                                                                                                                
[function] fragment-complexity=medium:fragment-steps=5: FPS: 1036 FrameTime: 0.965 ms                                                                                                             
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 1119 FrameTime: 0.894 ms                                                                                                         
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 1118 FrameTime: 0.894 ms                                                                                                      
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 1054 FrameTime: 0.949 ms                                                                                                       
=======================================================                                                                                                                                           
                                  glmark2 Score: 1021                                                                                                                                             
=======================================================  

```

---

### Post by sirtomato on 2018-10-11
with a DE, my GTX 1050 gets 8157 at 600x800

---

### Post by genkaplevis on 2018-10-30
Comparing it with the score of other machines should give a rough comparison of the ... with a different GPU configuration to understand what the glmark output indicated. ... At the end of thetests, glmark would show a score.

---

### Post by James_Creasy on 2018-11-08
Surface Laptop, Ubuntu 18.04


```
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) Iris Plus Graphics 640 (Kaby Lake GT3e) 
    GL_VERSION:    3.0 Mesa 18.0.5


    glmark2 Score: 2419 
```

---

### Post by JoeMac42 on 2018-12-09
Home built AMD Ryzen 5 2600 mini-ITX
EVGA GTX 1050Ti

```

=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 1050 Ti/PCIe/SSE2
    GL_VERSION:    4.6.0 NVIDIA 390.77
=======================================================
[build] use-vbo=false: FPS: 3328 FrameTime: 0.300 ms
[build] use-vbo=true: FPS: 10285 FrameTime: 0.097 ms
[texture] texture-filter=nearest: FPS: 10437 FrameTime: 0.096 ms
[texture] texture-filter=linear: FPS: 10373 FrameTime: 0.096 ms
[texture] texture-filter=mipmap: FPS: 10521 FrameTime: 0.095 ms
[shading] shading=gouraud: FPS: 10100 FrameTime: 0.099 ms
[shading] shading=blinn-phong-inf: FPS: 9853 FrameTime: 0.101 ms
[shading] shading=phong: FPS: 9471 FrameTime: 0.106 ms
[shading] shading=cel: FPS: 9468 FrameTime: 0.106 ms
[bump] bump-render=high-poly: FPS: 7213 FrameTime: 0.139 ms
[bump] bump-render=normals: FPS: 10583 FrameTime: 0.094 ms
[bump] bump-render=height: FPS: 11184 FrameTime: 0.089 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 7872 FrameTime: 0.127 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 5225 FrameTime: 0.191 ms
[pulsar] light=false:quads=5:texture=false: FPS: 10211 FrameTime: 0.098 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 3414 FrameTime: 0.293 ms
[desktop] effect=shadow:windows=4: FPS: 4305 FrameTime: 0.232 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 833 FrameTime: 1.200 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 859 FrameTime: 1.164 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 895 FrameTime: 1.117 ms
[ideas] speed=duration: FPS: 5653 FrameTime: 0.177 ms
[jellyfish] <default>: FPS: 7434 FrameTime: 0.135 ms
[terrain] <default>: FPS: 797 FrameTime: 1.255 ms
[shadow] <default>: FPS: 7356 FrameTime: 0.136 ms
[refract] <default>: FPS: 2227 FrameTime: 0.449 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 9929 FrameTime: 0.101 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 10220 FrameTime: 0.098 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 9846 FrameTime: 0.102 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 9582 FrameTime: 0.104 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 9788 FrameTime: 0.102 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 9506 FrameTime: 0.105 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 10235 FrameTime: 0.098 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 9799 FrameTime: 0.102 ms
[build] use-vbo=false: FPS: 3274 FrameTime: 0.305 ms
[build] use-vbo=true: FPS: 10321 FrameTime: 0.097 ms
[texture] texture-filter=nearest: FPS: 10373 FrameTime: 0.096 ms
[texture] texture-filter=linear: FPS: 10247 FrameTime: 0.098 ms
[texture] texture-filter=mipmap: FPS: 9699 FrameTime: 0.103 ms
[shading] shading=gouraud: FPS: 9943 FrameTime: 0.101 ms
[shading] shading=blinn-phong-inf: FPS: 9160 FrameTime: 0.109 ms
[shading] shading=phong: FPS: 9461 FrameTime: 0.106 ms
[shading] shading=cel: FPS: 9487 FrameTime: 0.105 ms
[bump] bump-render=high-poly: FPS: 6646 FrameTime: 0.150 ms
[bump] bump-render=normals: FPS: 11506 FrameTime: 0.087 ms
[bump] bump-render=height: FPS: 11437 FrameTime: 0.087 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 7785 FrameTime: 0.128 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 4962 FrameTime: 0.202 ms
[pulsar] light=false:quads=5:texture=false: FPS: 11024 FrameTime: 0.091 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 3463 FrameTime: 0.289 ms
[desktop] effect=shadow:windows=4: FPS: 4162 FrameTime: 0.240 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 773 FrameTime: 1.294 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 820 FrameTime: 1.220 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 970 FrameTime: 1.031 ms
[ideas] speed=duration: FPS: 5529 FrameTime: 0.181 ms
[jellyfish] <default>: FPS: 6989 FrameTime: 0.143 ms
[terrain] <default>: FPS: 792 FrameTime: 1.263 ms
[shadow] <default>: FPS: 7160 FrameTime: 0.140 ms
[refract] <default>: FPS: 2228 FrameTime: 0.449 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 10068 FrameTime: 0.099 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 10169 FrameTime: 0.098 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 10701 FrameTime: 0.093 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 10131 FrameTime: 0.099 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 9072 FrameTime: 0.110 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 10246 FrameTime: 0.098 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 9474 FrameTime: 0.106 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 9113 FrameTime: 0.110 ms
[build] use-vbo=false: FPS: 3285 FrameTime: 0.304 ms
[build] use-vbo=true: FPS: 10278 FrameTime: 0.097 ms
[texture] texture-filter=nearest: FPS: 9558 FrameTime: 0.105 ms
[texture] texture-filter=linear: FPS: 10320 FrameTime: 0.097 ms
[texture] texture-filter=mipmap: FPS: 9971 FrameTime: 0.100 ms
[shading] shading=gouraud: FPS: 9936 FrameTime: 0.101 ms
[shading] shading=blinn-phong-inf: FPS: 9996 FrameTime: 0.100 ms
[shading] shading=phong: FPS: 8732 FrameTime: 0.115 ms
[shading] shading=cel: FPS: 9407 FrameTime: 0.106 ms
[bump] bump-render=high-poly: FPS: 6771 FrameTime: 0.148 ms
[bump] bump-render=normals: FPS: 11475 FrameTime: 0.087 ms
[bump] bump-render=height: FPS: 10496 FrameTime: 0.095 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 8289 FrameTime: 0.121 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 4891 FrameTime: 0.204 ms
[pulsar] light=false:quads=5:texture=false: FPS: 11006 FrameTime: 0.091 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 3386 FrameTime: 0.295 ms
[desktop] effect=shadow:windows=4: FPS: 4229 FrameTime: 0.236 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 813 FrameTime: 1.230 ms
=======================================================
                                  glmark2 Score: 7605 
=======================================================

```

I ran glmark2 to stress the GPU while simultaneously running mprime to stress the CPU.  My goal was to test the cooling system while under stress.

Here's a repeat without mprime running:

```

=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 1050 Ti/PCIe/SSE2
    GL_VERSION:    4.6.0 NVIDIA 390.77
=======================================================
[build] use-vbo=false: FPS: 11240 FrameTime: 0.089 ms
[build] use-vbo=true: FPS: 20958 FrameTime: 0.048 ms
[texture] texture-filter=nearest: FPS: 19475 FrameTime: 0.051 ms
[texture] texture-filter=linear: FPS: 19479 FrameTime: 0.051 ms
[texture] texture-filter=mipmap: FPS: 19440 FrameTime: 0.051 ms
[shading] shading=gouraud: FPS: 17764 FrameTime: 0.056 ms
[shading] shading=blinn-phong-inf: FPS: 17518 FrameTime: 0.057 ms
[shading] shading=phong: FPS: 15794 FrameTime: 0.063 ms
[shading] shading=cel: FPS: 15754 FrameTime: 0.063 ms
[bump] bump-render=high-poly: FPS: 10932 FrameTime: 0.091 ms
[bump] bump-render=normals: FPS: 22526 FrameTime: 0.044 ms
[bump] bump-render=height: FPS: 22070 FrameTime: 0.045 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 13711 FrameTime: 0.073 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 7805 FrameTime: 0.128 ms
[pulsar] light=false:quads=5:texture=false: FPS: 20519 FrameTime: 0.049 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 5784 FrameTime: 0.173 ms
[desktop] effect=shadow:windows=4: FPS: 9402 FrameTime: 0.106 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 2185 FrameTime: 0.458 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 2526 FrameTime: 0.396 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 2321 FrameTime: 0.431 ms
[ideas] speed=duration: FPS: 13141 FrameTime: 0.076 ms
[jellyfish] <default>: FPS: 12433 FrameTime: 0.080 ms
[terrain] <default>: FPS: 962 FrameTime: 1.040 ms
[shadow] <default>: FPS: 11170 FrameTime: 0.090 ms
[refract] <default>: FPS: 3020 FrameTime: 0.331 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 19852 FrameTime: 0.050 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 19055 FrameTime: 0.052 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 19658 FrameTime: 0.051 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 19754 FrameTime: 0.051 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 18122 FrameTime: 0.055 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 19615 FrameTime: 0.051 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 19491 FrameTime: 0.051 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 18417 FrameTime: 0.054 ms
=======================================================
                                  glmark2 Score: 14299 
=======================================================
```

---

### Post by CatKiller on 2018-12-09
Oh, I remember seeing this thread back in the day!

Erm.... 33989...

```

=======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce RTX 2080 Ti/PCIe/SSE2
    GL_VERSION:    4.6.0 NVIDIA 415.18
=======================================================
[build] use-vbo=false: FPS: 15264 FrameTime: 0.066 ms
[build] use-vbo=true: FPS: 48551 FrameTime: 0.021 ms
[texture] texture-filter=nearest: FPS: 50831 FrameTime: 0.020 ms
[texture] texture-filter=linear: FPS: 50321 FrameTime: 0.020 ms
[texture] texture-filter=mipmap: FPS: 50522 FrameTime: 0.020 ms
[shading] shading=gouraud: FPS: 44348 FrameTime: 0.023 ms
[shading] shading=blinn-phong-inf: FPS: 44242 FrameTime: 0.023 ms
[shading] shading=phong: FPS: 43254 FrameTime: 0.023 ms
[shading] shading=cel: FPS: 42935 FrameTime: 0.023 ms
[bump] bump-render=high-poly: FPS: 36165 FrameTime: 0.028 ms
[bump] bump-render=normals: FPS: 51698 FrameTime: 0.019 ms
[bump] bump-render=height: FPS: 50700 FrameTime: 0.020 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 42346 FrameTime: 0.024 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 30327 FrameTime: 0.033 ms
[pulsar] light=false:quads=5:texture=false: FPS: 47347 FrameTime: 0.021 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 7541 FrameTime: 0.133 ms
[desktop] effect=shadow:windows=4: FPS: 9539 FrameTime: 0.105 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 2245 FrameTime: 0.445 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 2798 FrameTime: 0.357 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 2307 FrameTime: 0.433 ms
[ideas] speed=duration: FPS: 14419 FrameTime: 0.069 ms
[jellyfish] <default>: FPS: 33601 FrameTime: 0.030 ms
[terrain] <default>: FPS: 2035 FrameTime: 0.491 ms
[shadow] <default>: FPS: 22564 FrameTime: 0.044 ms
[refract] <default>: FPS: 10274 FrameTime: 0.097 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 46073 FrameTime: 0.022 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 45776 FrameTime: 0.022 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 45816 FrameTime: 0.022 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 45847 FrameTime: 0.022 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 45520 FrameTime: 0.022 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 45636 FrameTime: 0.022 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 45624 FrameTime: 0.022 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 45191 FrameTime: 0.022 ms
=======================================================
                                  glmark2 Score: 33989 
=======================================================

```

---

### Post by rawashbourne on 2019-07-07
1050 mobile / 7700hq

using nvidia-xrun, I get 9014

```

=======================================================
    glmark2 2017.07
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 1050/PCIe/SSE2
    GL_VERSION:    4.6.0 NVIDIA 430.26
=======================================================
[build] use-vbo=false: FPS: 8032 FrameTime: 0.125 ms
[build] use-vbo=true: FPS: 13183 FrameTime: 0.076 ms
[texture] texture-filter=nearest: FPS: 12444 FrameTime: 0.080 ms
[texture] texture-filter=linear: FPS: 12372 FrameTime: 0.081 ms
[texture] texture-filter=mipmap: FPS: 12676 FrameTime: 0.079 ms
[shading] shading=gouraud: FPS: 11011 FrameTime: 0.091 ms
[shading] shading=blinn-phong-inf: FPS: 11008 FrameTime: 0.091 ms
[shading] shading=phong: FPS: 10132 FrameTime: 0.099 ms
[shading] shading=cel: FPS: 10377 FrameTime: 0.096 ms
[bump] bump-render=high-poly: FPS: 7351 FrameTime: 0.136 ms
[bump] bump-render=normals: FPS: 14048 FrameTime: 0.071 ms
[bump] bump-render=height: FPS: 13837 FrameTime: 0.072 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 9266 FrameTime: 0.108 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 5257 FrameTime: 0.190 ms
[pulsar] light=false:quads=5:texture=false: FPS: 12189 FrameTime: 0.082 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 3785 FrameTime: 0.264 ms
[desktop] effect=shadow:windows=4: FPS: 7187 FrameTime: 0.139 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1420 FrameTime: 0.704 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1563 FrameTime: 0.640 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1655 FrameTime: 0.604 ms
[ideas] speed=duration: FPS: 10371 FrameTime: 0.096 ms
[jellyfish] <default>: FPS: 7190 FrameTime: 0.139 ms
[terrain] <default>: FPS: 781 FrameTime: 1.280 ms
[shadow] <default>: FPS: 7579 FrameTime: 0.132 ms
[refract] <default>: FPS: 1728 FrameTime: 0.579 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 11699 FrameTime: 0.085 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 11318 FrameTime: 0.088 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 11631 FrameTime: 0.086 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 11331 FrameTime: 0.088 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 11244 FrameTime: 0.089 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 11263 FrameTime: 0.089 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 11305 FrameTime: 0.088 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 11259 FrameTime: 0.089 ms
=======================================================
                                  glmark2 Score: 9014 
=======================================================

```

---

### Post by TheFu on 2019-07-07
I use virtual machines.
Over remote X11 through an ssh -tunnel: glmark2 Score: 23
It didn't look bad, but there are lots of issues like:
```
** GLX does not support GLX_EXT_swap_control or GLX_MESA_swap_control!
** Failed to set swap interval. Results may be bounded above by refresh rate.
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 26 FrameTime: 38.462 ms

``` with every test.

Attempts to run it on hardware failed. It core dump on a 16.04 Ryzen 2600 CPU w/ an nVidia 1030 GT GPU.

---

### Post by eirikr1848 on 2020-01-03
I've got an old Dell E1505 I've resurrected with Lubuntu 16.04 LTS. It has a Core Duo T2300 CPU, 2GB DDR2, and an ATI Radeon X1300 GPU (ATI RV515) [I should also add... it has a whopping 8GB SSD)

Windowed Mode (800x600) Score = 82
Fullscreen Mode (1280x800) Score = 51

One of the tests (Scene Terrain) fails due to missing vertex shaders. 

Anyway; after running these benchmarks I found a place to post them; so came here!

---

