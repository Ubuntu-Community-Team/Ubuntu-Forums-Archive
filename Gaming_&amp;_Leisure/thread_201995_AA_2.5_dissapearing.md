---
title: "AA 2.5 dissapearing"
date: 2006-06-22
forum: Gaming &amp; Leisure
---

### Post by pcbodger on 2006-06-22
Hi

I downloaded and installed AA 2.5 OK but when I run it, I get the splash screen and then it goesback to the desktop and nothing happens afterwards.

Does anyone have any suggestions?

Cheers

pcbodger

---

### Post by hippy4life on 2006-06-23
have you tried running from a console?

any error messages?

---

### Post by pcbodger on 2006-06-23
Good idea...

Cheat protection disabled
open /dev/[sound/]dsp: Device or resource busy
Couldn't set video mode: Couldn't find matching GLX visual


History:

Exiting due to error


Not sure what this means...

---

### Post by keithjr on 2006-06-23
[QUOTE=pcbodger]Good idea...

Cheat protection disabled
open /dev/[sound/]dsp: Device or resource busy
Couldn't set video mode: Couldn't find matching GLX visual


History:

Exiting due to error


Not sure what this means...[/QUOTE]

The cheat protection disabled thing you can ignore, it's just noise.  The other two are a little odd.  What video card do you have and have you installed the video drivers for it (if it is nVidia you can do this with Automatix, if ATI you can find the How-To somewhere about...sorry will edit with links later).  The game might be trying to set a video res/colordepth that isn't supported.

The sound error is also odd.  Do you have anything else open that is using the sound device?  Xmms?  Totem?  

These are just educated guesses.

---

### Post by hippy4life on 2006-06-25
did you get this sorted?

if so, post what you did to fix it as other users may have the same problem :)

---

### Post by pcbodger on 2006-06-25
Hi

Been away hoovering up beer in Blackpool so not had a chance to look at this till now :)

The sound one seems sporadic so I can ignore that.

I ran Automatix and selected the Nvidia drivers for install and now I get

WARNING: ALC_EXT_capture is subject to change!
Couldn't set video mode: Couldn't find matching GLX visual

Help!!

---

### Post by pcbodger on 2006-06-27
Sorted!

sudo apt-get install nvidia-glx linux-restricted-modules-$(uname -r)
sudo nvidia-glx-config enable

[http://wiki.serios.net/wiki/Ubuntu_NVIDIA_proprietary_display_driver_installation]("http://wiki.serios.net/wiki/Ubuntu_NVIDIA_proprietary_display_driver_installation")

---

