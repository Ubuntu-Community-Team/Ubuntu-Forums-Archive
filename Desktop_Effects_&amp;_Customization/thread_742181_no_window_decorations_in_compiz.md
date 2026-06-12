---
title: "no window decorations in compiz"
date: 2008-04-01
forum: Desktop Effects &amp; Customization
---

### Post by tschuliaen on 2008-04-01
Hello
I've now been looking for a solution for my problem for hours and I could not find a solution, therefore I'm opening a new thread although there are very similar ones but not quite the same ones.

I am using the opensource radeonhd drivers and not the ATI fglrx ones.
I have upgraded my Ubuntu Gutsy to Heron. Before compiz fusion worked great, as it does now, however the window decorations have gone.

In the meantime I have purged and reinstalled all the compiz packages, however no success.

so It goes:

```
$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4e44 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 

```

but the window decorations do not appear.

```
metacity --replace
```

brings back the window decorations but also stops compiz and the effects:(

I have also tried using emerald, but had no succes...
Well I hopefully there is another way to solve this strange problem...
thanks!

---

### Post by Shaoline on 2008-04-01
> ```
Checking for nVidia: not present. 
```

I am in no way a Linux guru, but have you checked your graphics driver?

---

### Post by mattchew on 2008-04-01
Oddly, I get the same thing in twinview with nvidia, that compiz runs but windows effects don't.

Maybe I'll have to look info emerald as well?

---

### Post by sdennie on 2008-04-02
Are you sure that you have the decorations plugin enabled?  I believe that if you install the package "compizconfig-settings-manager" and then go to System->Preferences->Advanced Desktop Effects Settings and then enable the Window Decorations plugin, it might fix your problem.

---

### Post by tschuliaen on 2008-04-02
ok now I realized that it only works when I start compiz in console. Under System->Preferences->Appearance it tells me "Desktop effects could not be enabled" so also the AWN Dock appears at the bottom, the actual desktop effects are not working although the plugins would be enabled.
So maybe there is really something wrong with my graphics driver...

```
$ glxinfo | grep string
server glx vendor string: SGI
server glx version string: 1.2
client glx vendor string: SGI
client glx version string: 1.4
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.3-rc2

```

---

### Post by mattk132 on 2008-04-02
go to synaptic and make sure the package xserver-xgl is installed.  If it isn't install it.  This is an opengl utility for X.  AFter this is installed you'll have to restart X and you should be a happy camper.:)

---

### Post by tschuliaen on 2008-04-02
> **mattk132 said:**
> go to synaptic and make sure the package xserver-xgl is installed.  If it isn't install it.  This is an opengl utility for X.  AFter this is installed you'll have to restart X and you should be a happy camper.:)

I tried it and what happened is that I got several daemons that could not start successfully and a really slow performance when for example moving windows (without compiz) and compiz turned out exactly the same (without effects and decorations) but slowed down everything a lot.

I thought the graphics processor should be used with AIGLX instead of the CPU with XGL or am I wrong?

---

### Post by tschuliaen on 2008-04-02
The strange thing is that when I'm starting the Gutsy (not hardy) Live CD the effects work immediately which means that the radeon drivers should support my graphics card and compiz...

---

### Post by tschuliaen on 2008-04-02
Well I now installed the fglrx drivers with envy-ng and strangely I'm getting the exact same errors: no window decorations and no real effects, just the AWN dock at the bottom!

```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 PRO
OpenGL version string: 2.1.7412 Release

```

Please help, I really don't know what else to try:(

---

