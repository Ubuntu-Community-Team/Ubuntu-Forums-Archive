---
title: "Guild Wars not working"
date: 2005-12-16
forum: Gaming &amp; Leisure
---

### Post by badtyprr on 2005-12-16
I'm using Cedega 5.0.3 and have not gotten Guild Wars to work. 

I use the following settings:
```

**General**
Winver: winxp
Cedega Version: 5.0.3
Use XVid Mode: no
Use XRandR: yes
DXGrab: yes
Managed: yes
Mozilla Control: yes
Scheduler: Default
Decrease WineServer Priority: no
Accelerated Interprocess Communication: yes
Use Pthreads: yes
Desktop: no
FreeType and XRender: yes

**Audio**
ALSA
Full Duplex: no
Use MMap: yes

**Video**
Video Ram (MB): Default
AGP Vertex Data (MB): Default
Pixel Shaders: yes, 1.3
Vertex Shaders: yes
NV_VAR Extension: yes
ARB_VBO Extension: yes
Dynamic VBO: no
Index VBO: no
Fixed GL Extension Buffer: yes
Manual GL Extensions: -GL_ARB_vertex_buffer_object
Fixed Program: no
Fragment Offset: auto
Non Power of Two Textures: auto
Clip Space Fix: yes
Anisotropic Filtering: no
Frame Buffer Objects: yes

```
Guild Wars will load, but it renders it in such a mess. (See screenshot)

Any ideas? Because I've tried enabling/disabling every option I can think of in every combination.

Here's more output from fglrxinfo. For specs, see my signature.
```

$fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: FireMV 2400 PCI DDR Generic
OpenGL version string: 1.3.1030 (X4.3.0-8.20.8)

```
If there's anymore information you think you might need to help me (other than a credit card =p), please ask. I'd be happy to provide you with it.

---

### Post by Nego on 2005-12-16
Cedega has VERY POOR ATI support, and ATI has very poor linux support. I'm having this same problem with many games

---

### Post by arpunk on 2005-12-16
Thats exactly what i get when i try to play WoW with wine, my ATI drivers are installed and they work, i get 3D accel. and wine is running also great but i get the same thing you get (screenshot). I guess my xmas gift will be nvidia :(

---

### Post by Elcoco on 2005-12-17
i had problems with cedega 5.0 over using my swap and the game jsut crashed randomly, going back to version 4.4.3 quickly fixed the problem
*note you may have to install a fix that is in the transgaming forums [http://transgaming.org/forum/search.php](http://transgaming.org/forum/search.php)

---

### Post by Snipersnest on 2005-12-17
[QUOTE=Elcoco]i had problems with cedega 5.0 over using my swap and the game jsut crashed randomly, going back to version 4.4.3 quickly fixed the problem
*note you may have to install a fix that is in the transgaming forums [http://transgaming.org/forum/search.php](http://transgaming.org/forum/search.php)[/QUOTE]

lol it still doesn't change the fact that he'll lag really bad  with the ATI card over an nvidia card... I only get about 30-70fps with a 6800 GT on high quality...

---

### Post by sataniceaden saklura on 2005-12-17
i cant get guild wars to install on linux it frezes at the directory selector (sorry i am a noob at linux) i am using wine to try and install of the cd

---

### Post by badtyprr on 2005-12-17
[QUOTE=Snipersnest]lol it still doesn't change the fact that he'll lag really bad  with the ATI card over an nvidia card... I only get about 30-70fps with a 6800 GT on high quality...[/QUOTE]

I was pretty used to playing GW with 20 fps on Windows. So, I think I can handle it. :) If I turn on the FPS counter, I think it's 15fps in Cedega. So, what's 5 more frames, hmm? ;) . And obviously, that screenshot shows GW is not playable.

---

### Post by badtyprr on 2005-12-17
[QUOTE=arpunk]Thats exactly what i get when i try to play WoW with wine, my ATI drivers are installed and they work, i get 3D accel. and wine is running also great but i get the same thing you get (screenshot). I guess my xmas gift will be nvidia :([/QUOTE]

Well, I can't take the ATI video out, so I guess I'm stuck. :p Maybe when laptops come standard with modular video cards, that'll change.

---

### Post by badtyprr on 2005-12-17
[QUOTE=sataniceaden saklura]i cant get guild wars to install on linux it frezes at the directory selector (sorry i am a noob at linux) i am using wine to try and install of the cd[/QUOTE]

Just download the client. Most people have had better luck with the smaller installer from the guildwars.com site instead of installing off of the CD.

---

### Post by gRiMgRaVy014 on 2005-12-18
are you saying that on the official guild wars website you can download a linux installer?

---

### Post by badtyprr on 2005-12-18
[QUOTE=gRiMgRaVy014]are you saying that on the official guild wars website you can download a linux installer?[/QUOTE]

Guild Wars doesn't support linux, but you can use wine or cedega to emulate a windows environment and install it to a virtual drive setup by wine or cedega. Getting the 3d component to work is up to you after that. Apparently ATI has little to no support in linux.. I'm still looking for a solution.

---

### Post by Brynster on 2005-12-19
Load version 4.4.3 from the load previous version options in the toolbar. I had similar issues using ATI card once i had the older cedega engine installed it was much improved. But when "zoning" the cursor can take a minute or so to reappear.

---

### Post by badtyprr on 2005-12-19
[QUOTE=Brynster]Load version 4.4.3 from the load previous version options in the toolbar. I had similar issues using ATI card once i had the older cedega engine installed it was much improved. But when "zoning" the cursor can take a minute or so to reappear.[/QUOTE]

Thanks for the tips. I tried loading 4.4.3, but it still complains about not having the right hardware and just loads into a black screen. Could you possibly share your configuration setup with me from Cedega? Maybe I don't have the right options..

---

### Post by Brynster on 2005-12-20
the ATI 9000?

Hmm whats the tech specs on that card, I am being to think it may be a little underpowered as a laptop card to run Guildwars.

Sometimes the laptop equivalant of a video card has reduced feature set inorder to keep heat down maybe that is the issue.

---

### Post by badtyprr on 2005-12-20
[QUOTE=Brynster]the ATI 9000?

Hmm whats the tech specs on that card, I am being to think it may be a little underpowered as a laptop card to run Guildwars.

Sometimes the laptop equivalant of a video card has reduced feature set inorder to keep heat down maybe that is the issue.[/QUOTE]

The fps readout when in the title screen is 17fps.. about what I'm used to in windows. But I don't have a windows partition anymore. Here's what I could find on the ATI site about the Mobility Radeon 9000:
> 
 Features

3D Performance and Quality

SmartShader™

        * Provides comprehensive hardware-accelerated support for DirectX® 8.1 programmable shader model, enabling more complex and realistic texture and lighting effects than ever before
        * Full supported by OpenGL® using custom extensions
        * Up to 6 textures per single rendering pass
        * Enables advanced per-pixel effects such as reflective bump mapping, anisotropic lighting and Phong shading


SmoothVision™

        * ATI’s most flexible and efficient anti-aliasing implementation available to date
        * Eliminates “jaggies” on the edges of objects, shimmering pixels on distant surfaces, and other visual artifacts for smoother-looking images
        * Superior visual quality without compromising performance
        * 16 programmable sample modes, selectable on a per pixel basis
        * Up to 8 samples per pixel
        * Fully compatible with DirectX® 8.1 multisample buffers


Industry leading power management

PowerPlay™

        * ATI's third-generation PowerPlay™ power management technology provides users with the optimal balance between performance and power consumption
              o Multiple power-saving settings offer increased control and flexibility
              o POWER-ON-DEMAND - constantly monitors system activity, dynamically adjusting clocks and voltage based on user scenario
              o LOW POWER LCD - LCD enables lower refresh rate for longer battery life


Visual quality & productivity

        * Leading-edge technology with integrated support for multiple combinations of displays; includes Hydravision™ software which provides the most flexible and easy-to-use interface for multiple display settings
        * Integrated dual-channel LVDS, with support for QXGA resolutions (2048x1536)
        * 165 MHz integrated TMDS transmitter (Digital Flat Panels)
        * Integrated TV-Out Encoder
        * Improved RAMDAC speed of 400MHz
        * Integrated Spread Spectrum
        * Integrated 12-bit DDR and 24-bit SDR Digital Port
        * Improved ratiometric expansion with ATI ZOOM technology; enabling users to change display resolutions with a single keystroke


Portable entertainment on a notebook

        * Integrated MPEG-2 decode including iDCT, motion compensation, and hardware sub-picture decoder
        * Back-end scaler delivers top quality, industry-leading DVD playback with lowest CPU usage
        * Front-end scaler enables playback on two separate displays
        * 8-bit alpha blending and video keying for effective overlay of video and graphics


Three Pin-Compatible Variants for Ultimate Design Flexibility

        * Mobility™ Radeon™ 9000 represents ATI’s sixth generation of mobile graphics to integrated memory on the chip. With three variants, Mobility™ Radeon™ 9000 offers true flexibility for numerous mobile form factors, from full size to “thin-and-light”. Mobility™ Radeon™ 9000 has three variants:
              o Discrete
              o On-chip 32MB DDR (64-bit)
              o On-chip 64MB DDR (128-bit)
              o On-chip 128MB DDR (128-bit)



---

### Post by badtyprr on 2005-12-24
*bump* Has anyone gotten (or not gotten) an ATI Mobility Radeon 9XXX to work with Guild Wars?

---

