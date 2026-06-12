---
title: "Sli on, steam games black. Help me.... I'm learning."
date: 2019-06-25
forum: Gaming &amp; Leisure
---

### Post by shadowstorm56 on 2019-06-25
I really like ubuntu but the learning of certain things is slow. What I want seems simple enough, my 3 screens enabled and using both my graphics cards. Not looking to span games across all 3 or anything like that... well not yet. If I enable sli I get one screen working and it's flickery, steam games open a black screen and it sits there. If I go in after enabling sli and enable the.... other one besides xinerama then it enables all 3 screens, sli marker is gone but both graphics cards are used. Only game I can run sofar in that mode is runescape and it shows graphics use on both cards. Once again if I load up a steam game in this mode it just pops up a black screen whare the game would load and just sits there. If I enable xinerama at all it kills all graphics on the PC until I disable it. So what do I do? Thanks!

---

### Post by mastablasta on 2019-06-26
what is the GPU ? is the SLI function supported by Linux driver?

---

### Post by shadowstorm56 on 2019-06-26
They are 1080s

---

### Post by Mr. Swiveller on 2019-06-27
Does this also happen in native Linux games that have SLI support? 

Most games on Steam are made for Windows; Proton uses the Wine compatibility layer to run them. Although this generally works well, Wine cannot fully replicate a Windows environment. You may have run into one of the instances where a feature present in the Windows version of an application does not (or not yet) work on Linux.

---

### Post by shadowstorm56 on 2019-06-27
Happens in native ones as well. All the games I tried work fine in non sli mode. Only game that works in sli is runescape

---

### Post by shadowstorm56 on 2019-07-01
I tried different things but there really seems to be no change, no trouble getting one card to work or sli to run just the desktop and runescape. But all games just.... go black.

---

### Post by CatKiller on 2019-07-02
> TwinView is also not supported with SLI or Multi-GPU. Only one display can be used when SLI or Multi-GPU is enabled, with the exception of Mosaic.

If X is configured to use multiple screens and screen 0 has SLI or Multi-GPU enabled, the other screens configured to use the nvidia driver will be disabled. Note that if SLI or Multi-GPU is enabled, the GPUs used by that configuration will be unavailable for single GPU rendering.
[http://us.download.nvidia.com/XFree86/Linux-x86_64/430.09/README/sli.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/430.09/README/sli.html)

As far as I can tell, SLI Mosaic Mode is the only supported way to have SLI and multiple monitors at the same time with the Nvidia driver. Instructions for that are in the readme.

---

### Post by shadowstorm56 on 2019-07-02
Yea and I enabled that, all screens work and use both GPU. But all steam games are just a black screen. If I enable sli and just use one screen and not the mosaic feature it's all flickery and crap and still is just black screen in steam games. Single GPU all the games work but not at the fps I want.

I will double check that readme incase I missed somthing important

---

### Post by CatKiller on 2019-07-03
> **shadowstorm56 said:**
> I will double check that readme incase I missed somthing important
It's very detailed and useful, but it takes a while to absorb it. There are all kinds of weird quirks and limitations. Some come from X11 being from 1987 with 32 years of "organic growth," some come from Nvidia wanting to keep their Linux driver as close to their Windows driver as they can, and some seem to just be arbitrary.

---

### Post by rakivilsov on 2019-08-21
> **shadowstorm56 said:**
> I really like ubuntu but the learning of certain things is slow. What I want seems simple enough, my 3 screens enabled and using both my graphics cards. Not looking to span games across all 3 or anything like that... well not yet. If I enable sli I get one screen working and it's flickery, steam games open a black screen and it sits there. If I go in after enabling sli and enable the.... other one besides xinerama then it enables all 3 screens, sli marker is gone but both graphics cards are used. Only game I can run sofar in that mode is runescape and it shows graphics use on both cards. Once again if I load up a steam game in this mode it just pops up a black screen whare the game would load and just sits there. If I enable xinerama at all it kills all graphics on the PC until I disable it. So what do I do? Thanks! [COLOR=#000000][FONT=Arial]**[[color=#000000]audacity[/color]](https://audacity.onl/) [[color=#000000]temp mail[/color]](https://mails.tips/temp-mail/) [[color=#000000]origin[/color]](https://origin.onl/)**[/FONT][/COLOR]
[COLOR=#000000]Wine cannot fully replicate a Windows environment. You may have run into one of the instances where a feature present in the Windows version of an application does not (or not yet) work on Linux.[/COLOR]

---

