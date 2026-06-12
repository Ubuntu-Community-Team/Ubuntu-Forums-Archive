---
title: "beryl two-texture support"
date: 2007-03-19
forum: Desktop Effects &amp; Customization
---

### Post by SGoodyer on 2007-03-19
Just got Beryl files etc and did beryl-manager for compatibility test and this came up:


Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

I have dual wide-screen setup but haven't gotten it working right (alt monitor just mirrors). Was thinking that having them both plugged in would make it do this?

Using flgrx with aiglx on my X800XT PE

Also if open source ATI drivers are better could someone possibly direct me to them? Looked for hours but can only find the ones offered by ATI (ati.com)

I used Envy to install my drivers (which it got from ati)

---

### Post by Ubuntiac on 2007-04-20
Hmm...

I'm getting this too only on a very different setup...

Kubuntu Feisty Final
Onboard 3d card using openchrome flawlessly (glxgears are super smooth)
Same error message when I type in beryl
typing beryl-manager makes the screen go black and returns me to the kde login screen...:confused:

---

