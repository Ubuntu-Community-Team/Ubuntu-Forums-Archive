---
title: "GStreamer problems with DX50 header files"
date: 2005-12-13
forum: Desktop Environments
---

### Post by iradi8 on 2005-12-13
For some reason I cannot get Totem or other Gstreamer based apps to play my AVI files that I have encoded with Lavc and set the DX50 header on. I just tried an AVI that I made with XViD and that has whatever header identifies it as XViD, and that plays fine. So it appears to me that it is the DX50 Header. I intend to reset the header on one of the files to XVID ( or whatever the appropriate is) and try it again. But I can't do that tonight. 

That said I wanted to post this anyway and see if anyone has any thoughts as to what I should do. I set the DX50 ffourcc header on purpose so that my DIVX compatible DVD player would use DIVX to play the files. The files are compatable with DIVX but they player was too stupid to use it without the DX50 set.  I would hate to have to go through and reset the ffourcc header on all my files just to play them in Breezy.

I did find that Mplayer would play them OK, but I prefer to use Kaffiene as my player and that likes to use the gstreamer engine in breezy. I haven't been able to get it to use the xine engine successfully. But that really doesn't strike me as a fix anyway, just a work around. I am hoping by posting this someone can come up with a fix. Or in lieu of a fix perhaps tell me how to get Kaffeine to use the Xine engine for real.

TIA :confused:

---

### Post by iradi8 on 2005-12-14
:D Well it looks like I solved my problem. I thought I had installed everything GStreamer under the sun. But today I gound a new(?) gstreamer-ffmpeg option in Synaptic. I installed that and lo-and-behold playing my DX50 AVI's is working. Thanks be to the great Ubuntu 'puter gods!

Now if those same great Ubuntu 'puter gods could put a working transcode ffmpeg plugin in there. then we would be cooking with gas. But alas, that is part of the "Multiverse". So off I trudge to find a way to convert my LEGAL DiVX files into DVD compatable MPEG2's

---

