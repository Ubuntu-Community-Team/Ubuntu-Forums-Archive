---
title: "HL2, Steam and Wine"
date: 2007-01-31
forum: Gaming &amp; Leisure
---

### Post by nisbus on 2007-01-31
Hi,

I've finally managed to get the ATI drivers to work with my radeon mobility X700 card. (thanks to this [_guide_]("http://doc.gwos.org/index.php/ATI_AMD_fglrx_Edgy"))

```
glxinfo | grep direct
```

now returns 

```
direct rendering: yes
```

so I would think everything should be working correctly.

Steam runs fine and the installation of HL2DM went just as smooth as the installation on WindowsXP.

I even get HL2DM running under Wine but on the opening video I see a lot of purple specs and it looks like it's rendering the picture in slow motion (it's all pixelated)

I'm running the game with -dxlevel 70 -height 480 -width 640 and the screen obviously changes resolution when I start the game.

The problem comes when I connect to a server. The graphics plain suck. It looks like it's running in a much higher resolution than the one I specified even though in the settings panel of the game it says it's running 640x480. 

Has anyone else seen this?

How can I fix it?

I'm so close but still sooo far away :(

---

