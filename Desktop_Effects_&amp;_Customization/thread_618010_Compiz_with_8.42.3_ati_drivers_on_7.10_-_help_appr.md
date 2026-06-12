---
title: "Compiz with 8.42.3 ati drivers on 7.10 - help appreciated!"
date: 2007-11-19
forum: Desktop Effects &amp; Customization
---

### Post by therealknewman on 2007-11-19
I finally got the 8.42.3 driver to work on my system. Performance is great, no more scrolling lag like I had back in the XGL days. The problem is compiz doesn't work anymore! I have aiglx and composite enabled in my xorg.conf file. I've whitelisted the fglrx driver in compiz. When I run compiz my screen gets all fuzzy. I've included a screenshot so you can see what I mean. Has anyone else had the same problem as me? Solutions anyone? I'm running an ati x1600pro (agp) with 1gb ram and amd athlon 3800. My gutsy gibbon is 64 bit. I'll post any more info that could be helpful. I'm not a total linux noob but I'm still learning so bear with me if I seem a little simple.
[IMG]http://pepperscafe.net/jimfiles/Screenshot.png[/IMG]

---

### Post by angryfirelord on 2007-11-20
Turn off effects and run:
```
fglrxinfo
```
in a terminal.

---

### Post by therealknewman on 2007-11-20
```
jim@jim-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6958 Release

```

---

### Post by therealknewman on 2007-11-21
*Bump* Any ideas? Anyone?? Heres another pretty screenshot...
[IMG]http://pepperscafe.net/jimfiles/badcompizre.png[/IMG]

---

### Post by jimerickso on 2007-11-21
at the risk of sounding stupid i am going to ask anyway. did you remove xgl?

sudo apt-get remove xserver-xgl

---

### Post by tiachopvutru on 2007-11-21
I don't think you need Composite enable to add # on each line of "Extension" Section and see what it'd be like. I didn't enable mine, and although Compiz lags, at least it works. :roll:

*Still waiting for an ATI Driver to work entirely well (i.e. Compiz runs fast, and can enable Compiz while processing video)*

That aside, if you didn't already know, there was a new driver out today...

---

### Post by patryk77 on 2007-11-21
@tiachopvutru: i have no problems with compiz and video since i changed the gstreamer output. In a terminal, type:

```
gstreamer-properties
```

in the video tab, set default output plugin to "x window system (no xv)" and click test

if you see the test bars without flickering, you should be good to go

@thereal: i agree, make sure xgl is off, and that your 3d rendering works. In the terminal:

```
$ LIBGL_DEBUG=verbose glxinfo | grep rend
```

---

### Post by therealknewman on 2007-11-22
Just put in the new driver, still same results with compiz. My fps on glxgears went up by 100 though. 
Xgl isn't installed, and i commented out the composite section.. no luck. The LIBGL_DEBUG command gave me this: 
```
jim@jim-desktop:~$ LIBGL_DEBUG=verbose glxinfo | grep rend
libGL: XF86DRIGetClientDriverName: 8.43.2 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/fglrx_dri.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 5, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 5, (OK)
drmOpenByBusid: drmOpenMinor returns 5
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
direct rendering: Yes
OpenGL renderer string: Radeon X1600 Series

```
Oh and Happy Thanksgiving everyone!

---

