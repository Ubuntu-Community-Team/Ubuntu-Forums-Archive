---
title: "dell dimension 4600 no sound"
date: 2009-09-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dst_66 on 2009-09-30
Hi,
 
I have installed Ubuntu 9.04 on my dell dimension 4600 and there is no sound. Previous version worked just fine.
 
The sound card is Sound Blaster Live 5.1.
I disabled pulse and use ALSA only as was recommended on one of Ubuntu forums.
No luck.
I don't want to go back. What do I do to resolve the issue?

---

### Post by khelben1979 on 2009-09-30
[Check this thread]("http://ubuntuforums.org/showthread.php?t=499814").

---

### Post by dst_66 on 2009-09-30
Thank you for you quick reply.
 
In the link you sent someone recommended: "the program gnome-sound-properties has a drop down box so you can select the device you wish to use. Does that work?"
 
I've tried it already it did not help.

---

### Post by dst_66 on 2009-10-01
More comments:
cat /proc/asound/modules returns
0 snd_intel8x0
1 snd_emu10k1x

But asoundconf list returns
Names of available sound cards:
ICH5

I should see Live as well. For some reasons Ubuntu does not see it here.
Any help?

---

### Post by khelben1979 on 2009-10-01
> **dst_66 said:**
> More comments:
cat /proc/asound/modules returns
0 snd_intel8x0
1 snd_emu10k1x

But asoundconf list returns
Names of available sound cards:
ICH5

I should see Live as well. For some reasons Ubuntu does not see it here.
Any help?

From that list I can see that the emu10k1x sound driver isn't used as default.

[alsaconf]("http://wiki.debian.org/alsaconf") is a good program, unfortunately it's not part of Ubuntu. It's part of [ALSA]("http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture"). If you get this application, you should have sound working in no time!

---

### Post by dst_66 on 2009-10-01
I am sorry what application should I get?

---

### Post by khelben1979 on 2009-10-01
> **dst_66 said:**
> I am sorry what application should I get?

alsaconf.

---

### Post by dst_66 on 2009-10-01
Well... I got the latest ALSA on my machne. My guess is something's wrong with the driver for emu10k1x and I don't know how to resovle that.

---

### Post by khelben1979 on 2009-10-01
> **dst_66 said:**
> Well... I got the latest ALSA on my machne. My guess is something's wrong with the driver for emu10k1x and I don't know how to resovle that.

Downgrade to the previous working version of Ubuntu might be the easiest thing to do.

One other alternative is to check out this [Matrix:Vendor-Creative Labs]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs") page and determine if you're using the correct driver. I used the ```
modprobe sb
``` to get my Sound Blaster Live card working a few years ago before I replaced it with an Sound Blaster Audigy 2 ZS which I've got at the present.

---

