---
title: "modutils, alsa and gnome ( I have sound problems )"
date: 2005-03-28
forum: Desktop Environments
---

### Post by pwab on 2005-03-28
Hi,

First off:   KUDO's;  Ubuntu is GREAT! I'm coming from gentoo, where I got sick of the delay caused by having to recompile everything (that seemed like a bonus some time ago  8) ) Ubuntu ( and debian in general, I suppose ) seems like an excellent alternative.

My problem: I have an old brooktree video capture card in my machine that I've never been able to use at all. Ubuntu, suprisingly, detected it just fine and now the modules required to work with it are loaded at startup. The installer however did NOT detect my Soundblaster AWE card that I've been using for ages.

I DID read the ALSA help and I can get the soundcard up and running. (I can play mp3's with XMMS) However none of the gnome apps can use the soundcard. They all use the first sound-device (which is actually my Brooktree card's and to be able to use my SB you need to use the second wave device.)

So:
[list]
[*]how do you configure gnome so that the esd use the second wave device?
[*]how should I use modutils properly to load the required modules for the soundblaster? I just edited /etc/modules.conf (even though it says you shouldn't)
[*]should i be using esd at all? I came across a lot of people saying it sucks. What are the alternatives?
[*]if my first questions were daft, how do I swap around the two wave devices so that my SB:AWE is the first device?
[/list]

Friendly Regards,
p!

---

