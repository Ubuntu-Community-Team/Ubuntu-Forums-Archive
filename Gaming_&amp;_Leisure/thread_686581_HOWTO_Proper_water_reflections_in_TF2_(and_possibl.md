---
title: "HOWTO: Proper water reflections in TF2 (and possibly other source games)"
date: 2008-02-03
forum: Gaming &amp; Leisure
---

### Post by clonek on 2008-02-03
I'm assuming you are already have TF2 running. I'm simply addressing the water reflection issue. 

With the version of Wine in the default Gutsy sources (version 0.9.46) water reflections do not work. For me atleast, on maps like 2fort the water appeared brown and wasn't transparent at all.  

Installing the latest version of Wine (0.9.54) fixes this problem for me.

Go to [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb) and follow the instructions there to add the Wine sources to apt.

After installing the sources run:

sudo apt-get update
sudo apt-get upgrade

That will upgrade wine to the latest version.

From a terminal window run:

wine regedit

Browse to HKEY_CURRENT_USER\Software\Wine\Direct3D and verify the following values are present.

OffScreenRenderingMode = fbo
PixelShaderMode = enabled
UseGLSL = Enabled
VertexShaderMode = hardware
VideoMemorySize = 512 (or whatever your video card memory is in MBs)

If they aren't there, right click the right pane and select New > String Value and enter the missing value. 

In TF2 ensure that you have "Reflect All" set in your video settings. Reflect World might work as well if you're having performance issues. I haven't tried it myself.

That should hopefully do it. Obviously enabling these reflections will give a performance hit. About ~5fps or more, but worth it imo.

As a side note:
Nvidia Driver Version: 169.09
Video Card: Nvidia 8800GT


Some before and after screenshots:

---

