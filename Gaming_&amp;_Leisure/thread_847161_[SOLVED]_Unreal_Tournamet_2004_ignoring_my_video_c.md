---
title: "[SOLVED] Unreal Tournamet 2004 ignoring my video card?"
date: 2008-07-02
forum: Gaming &amp; Leisure
---

### Post by Zeotronic on 2008-07-02
On my father's computer I have a TNT2 NVidia card installed (with the driver and everything), the screensavers seem to recognize that its their (for they run at a normal speed), but Unreal Tournament 2004 doesn't seem to recognize it, because it runs at a speed comparable to if I didn't have the card installed at all. Now on *my* computer, I have newer NVidia card installed (the exact model number escapes me at the moment), and it runs fine, so I'm hoping that I can merely change some configuration somewhere. **How can I get Unreal Tournament 2004 to utilize my TNT2 card?** The game has that NVidia logo on startup, so I must admit I was rather suprised that it wasn't working.

---

### Post by adam_kimber on 2008-07-02
Lol to your footer btw. 

I must admit whilst I have much experience with nvidia graphics cards I do not have any of the TNT range. They are fairly old and I believe you need to use the legacy nvidia driver to get 3D acceleration to work. I think your computer with the TNT ubuntu installation is not using 3D acceleration and hence the game is not working.

Try doing the following, this will test if you are 3D accelerated. 

1) Run the following in a terminal. This will point out which driver you are using to start X with. 

```
less /etc/X11/xorg.conf | grep nv
```

You will either get a line with nvidia (the 3D accelerated proprietary driver from nvidia) or nv the opensource 2D driver. 

2) Run the following command in a terminal

```
less /etc/X11/xorg.conf | grep glx
```

All that does is display the xorg.conf file and then find a particular line (grep is useful for that sort of thing). You should get a line like the following

```
Load           "glx"
```

If not I will tell you how to put it in.

3) Further tests :D . Just open a termainl and type

```
glxinfo | grep direct
```

```
glxinfo | grep NVIDIA
```

Then paste the output, the first should be yes and the second should say server glx vendor string: NVIDIA Corporation

All of that proves the Nvidia driver is installed. :P It will also highlight which version.

---

### Post by Zeotronic on 2008-07-20
Yes to the first one and:
> server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation
OpenGL version string: 1.5.3 NVIDIA 71.86.04

To the second...
Sorry it took me so long to respond.

---

### Post by eragon100 on 2008-07-20
I can tell why is it slow -- because that card is just too old. You will need AT LEAST a geforce 2, rather a 3 or 4, for reasonable performance in ut2k4 :(

---

### Post by Frem on 2008-07-21
This man speaks the truth. The TNT2 is pre-GeForce era. Now, you *might* be able to run the game at low res with all the settings turned down if you change from OpenGL to Software rendering, but you'll need quite a decent processor and it won't be nearly as playable.

Have you considered picking up the original UT? That would probably run quite fine, and it's cheap; I saw a bundle with U1, U2, UT, and UT2k4 at GameStop for $10 two days ago. I almost bought it just for UT2k4. ;-)

---

### Post by eragon100 on 2008-07-21
Isn't it extremely difficult to get the original UT running on a modern distro, as with almost all the old loki games?

---

