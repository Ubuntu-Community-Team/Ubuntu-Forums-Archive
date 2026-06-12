---
title: "Installing Rain-Slick Precipice on EEE PC 1000 HE running UNR 9.04"
date: 2009-05-20
forum: Gaming &amp; Leisure
---

### Post by minderbinder on 2009-05-20
I'm trying to install On the Rain-Slick Precipice of Darkness Part 2 on my EEE PC 1000HE running UNR 9.04 and I seem to be having problems with the graphics driver and opengl. When I click on the RainSlickEp2 file I get an error message that says it could not find a compatible device.

This is the console.log file I get:

exec: Invalid script file ./prefs.cs
Language English [parpg/data/language/english.lso] activated.
Language English [parpg/data/language/english.lso] activated.
exec: Invalid script file common/server/missionLoad.cs
Video Init:
Activating the OpenGL display device...
Setting screen mode: window 800x480x32
  > Setting actual display mode: window 800x600x32
  > Trying 4x multisample video mode.
  ! Failed. SDL error: Couldn't find matching GLX visual
  > Trying 2x multisample video mode.
  ! Failed. SDL error: Couldn't find matching GLX visual
  > Trying standard video mode.
  > OpenGL driver information:
     Vendor: Tungsten Graphics, Inc
     Renderer: Mesa DRI Intel(R) 945GME GEM 20090114 x86/MMX/SSE2
     Version: 1.4 Mesa 7.5-rc2
  > Intializing glew.
  > Testing OpenGL extensions.
  ! Missing OpenGL extensions EXT_texture_compression_s3tc.
  ! Unable to set screen mode.

---

### Post by Vadi on 2009-05-20
I'd recommend emailing their support about this.

---

### Post by minderbinder on 2009-05-20
This is the reply I got from hotheadgames:

Unfortunately, Intel chipsets implement texture compression in software. This isn't a problem in Windows, but because the algorithms for texture compression are patented, it means the Intel drivers for linux lack this feature and thus don't work with the game. If you can find drivers that implement texture compression, you'll be able to run it, otherwise I'm afraid you're out of luck. As the owner of two EeePCs (900 and 901) running Debian, I'm sorry to be the bearer of bad news. :(

Are there drivers available that will work or did I spend 15 bucks on a game I can't play?

---

### Post by Vadi on 2009-05-20
Um, yeah. Didn't know that would be an issue, I'm on nVidia drivers here. There's only one set of Intel drivers for Linux, unfortunately.

---

### Post by minderbinder on 2009-05-21
I definitely recommend trying the demo for any game from Hothead Games. Their technical support for Linux is non-existent. My computer meets all of the system requirements listed on their site but the program will not run on my computer. I've asked for a refund or a Windows license and have been ignored.

---

### Post by Vadi on 2009-05-21
You don't need to obtain a windows license separately: [http://www.hotheadgames.com/pafaq.php#multiplat](http://www.hotheadgames.com/pafaq.php#multiplat)

---

### Post by minderbinder on 2009-05-21
Thanks Vadi, that makes my day! If their tech support would have sent me that link I would be eager to buy Episode 3 when it comes out.

---

### Post by minderbinder on 2009-05-24
They have now removed intel graphics from the list of supported hardware on Linux. It won't install in Windows 7 and I don't trust their tech support to help at all so I guess I'll be playing on my Mac.

---

