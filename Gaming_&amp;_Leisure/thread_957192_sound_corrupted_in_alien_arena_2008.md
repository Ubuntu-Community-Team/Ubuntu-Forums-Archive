---
title: "sound corrupted in alien arena 2008"
date: 2008-10-24
forum: Gaming &amp; Leisure
---

### Post by jcer93705 on 2008-10-24
Hello, i had alien arena older version installed from synaptic package sound work great. I am using 8.10 ubuntu and even the older version ubuntu i never could get the alien arena sound working without the crazy corrupted sound. Anyways installing by synaptic package sound works in the older alien arena. But since theres a 2008 version of alien arena, i decided to remove the older alien arena and then downloaded from the web extract it, i clicked on crx and it worked flaless but no sound then i typed crx.sdl the sound turned on but doesn't sound clear but courrupted, how can i fix this?

---

### Post by MaxIBoy on 2008-10-24
This might help:
[http://corent.proboards42.com/index.cgi?board=aatech&action=display&thread=3181](http://corent.proboards42.com/index.cgi?board=aatech&action=display&thread=3181)

---

### Post by Irritant on 2008-10-24
Also try setting the sampling rate to 48khz in the game options menu.

---

### Post by munkee on 2008-10-25
I have no sound at all in the game.:(  I have carried out some checks and found the following from the log when the game is run.

> ------- sound initialization -------
/dev/dsp: No such file or directory
SNDDMA_Init: Could not open /dev/dsp.

I have an Asus Xonar D2X soundcard, but also an ATI Radeon 4870 graphics card and a USB mic (as part of my webcam).  I have noted that the Radeon card has a Realtek sound chip to support HDMI connections.  Is it possible that it could be picking up one of the other audio devices instead of the Xonar card?

Can I edit the sound configuration to correctly select the right sound chip and server (pulseaudio in my case)?  Any advice would be greatly appreicated. Thanks

---

### Post by Azure.Rise on 2008-10-25
I got the sound working by running crx.sdl instead of the regular one, but for some reason I can't get the game to launch from gnome. Also, this may be obvious but I'll state it anyways, but many games have all sorts of problems with compiz so you may wanna disable that first by running "metacity --replace" in the command line.No quotes of course.

---

### Post by munkee on 2008-10-26
No joy with disabling compriz sadly (using metacity command).  Still no sound in AA2008. :( Thanks for the advice.

---

