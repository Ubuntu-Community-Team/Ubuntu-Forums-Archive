---
title: "[Kubuntu] XBMC errors after upgrading kernel"
date: 2013-08-04
forum: Desktop Environments
---

### Post by daviddoji on 2013-08-04
Yesterday I updated and upgraded my HTPC. I also erased the old kernels and packages suggested by the terminal.Now, when I open XBMC, videos play not so well. Voices and subtitles are synchronized but images are lagging behind 2-3 seconds.According to system monitor, my pc is not overloaded nor the RAM is fully used.Before the update, everything was perfect.I'm using the recommended nvidia propietary drivers with vdpau libraries. Using Mplayer, everything is fine.Any suggestions?

---

### Post by TheFu on 2013-08-04
Force a reinstall of the proprietary nVidia drivers. This should force a relink to the kernel.  After every kernel install, I have to do this to get thing working again properly too.  I have a script, but since my XMBC box is ATI, it doesn't help you.  I don't purge the drivers first, just a --reinstall is enough.

I've stopped patching my XBMC box until there is an issue or 6 months. It isn't on the internet.  Basically, once I got it working the way I wanted for all the media, I try not to touch it.  Right now everything is working ... except Amazon Video Streaming.  I know that can work - a Mint13 box here does it perfectly, but I've been unable to get any of 3 different Ubuntu installs to work at all with that streaming provider.

---

