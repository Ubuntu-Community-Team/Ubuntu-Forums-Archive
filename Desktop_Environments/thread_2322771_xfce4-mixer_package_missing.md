---
title: "xfce4-mixer package missing"
date: 2016-04-30
forum: Desktop Environments
---

### Post by scotty64 on 2016-04-30
Anybody knows what has happened to xfce4-mixer in Xenial ? I always installed that one in addition to the default pulseaudio based mixer, because xfce4-mixer allowed mixing much more "close to the hardware" particularly on more complex audio cards. I know there are other mixers in the distro, but I find their GUIs not as good as xfce4-mixer.

---

### Post by scotty64 on 2016-04-30
I found the answer myself in this very disappointing thread:
[https://forum.xfce.org/viewtopic.php?id=9457](https://forum.xfce.org/viewtopic.php?id=9457)

---

### Post by kazakore on 2016-05-29
I came here for this issue plus another one I have come across on just installing Ubuntu Studio 16.04 yesterday (I can see it may take me a while to get everything running as I'd like...) Did you find a solution?

As that thread says Fedora still packages it as although it is no longer going to be maintained GStreamer0.10 has not yet been removed. Thus it should be possible to still install and use xfce4-mixer running on GStreamer0.10 on Xenial as well as I see it still have the old GStreamer packages available.

I don't use Pulse, I have qjackctl start on boot (with the PA sink although that hasn't been working so far on this install) so the PA mixer is of zero use to me! I remap the volume keys using amixer like I always did and I want an applet that gives me access to the alsa mixers (and all the mixers through a dropdown menu like xfce4-mxer had is really useful.) I don't see the fact it has stopped being developed as a good reason to stop providing it when it still serves it purpose perfectly! :(



EDIT: Well I went through the dependencies and installed from the Trusty repository via direct download and it appears to be working fine: [http://packages.ubuntu.com/trusty/x11/xfce4-mixer](http://packages.ubuntu.com/trusty/x11/xfce4-mixer)

---

### Post by ericmark4 on 2016-07-24
Bumping this thread to note that the xfce4-mixer panel plugin can be found at: [http://www.ubuntuupdates.org/package/mint_import/rafaela/import/base/xfce4-mixer](http://www.ubuntuupdates.org/package/mint_import/rafaela/import/base/xfce4-mixer)

Stumbled across it today after a fresh install of Xubuntu 16.04.1.

---

