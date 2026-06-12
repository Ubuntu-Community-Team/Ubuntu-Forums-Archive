---
title: "Equalizing All Audio Output"
date: 2012-01-04
forum: Desktop Environments
---

### Post by Pimentel on 2012-01-04
Hy everyone!
 
Does anyone know a real-time equalizer app/plugin that will apply the filter to the sound card output? It's intended to apply a bass boost everywhere like in gaming, flash, media players and so on.
 
I'm looking forward getting rid of Windows on my Desktop, but I can't find a Linux replacement for the built-in equalizer from Realtek's Utility software.
 
Please, help!
 
Thanks.

---

### Post by blueshead on 2012-01-04
..

---

### Post by kostkon on 2012-01-04
There is PulseAudio Equalizer. It's not being actively developed anymore, but it works just fine.

Check [here]("http://www.webupd8.org/2011/04/system-wide-pulseaudio-equalizer.html").

If you don't want to add the PPA mentioned in the post, you can grab the .deb file directly from it (and install it by double-clicking on it).

For 11.10:
[https://launchpad.net/~nilarimogard/+archive/webupd8/+files/pulseaudio-equalizer_2.7.0.2-2%7Ewebupd8%7Eoneiric3_all.deb]("https://launchpad.net/~nilarimogard/+archive/webupd8/+files/pulseaudio-equalizer_2.7.0.2-2%7Ewebupd8%7Eoneiric3_all.deb")
For 11.04:
[https://launchpad.net/~nilarimogard/+archive/webupd8/+files/pulseaudio-equalizer_2.7.0.2-2%7Ewebupd8%7Enatty3_all.deb]("https://launchpad.net/~nilarimogard/+archive/webupd8/+files/pulseaudio-equalizer_2.7.0.2-2%7Ewebupd8%7Enatty3_all.deb")

Hope that helps.

---

### Post by Pimentel on 2012-01-04
> **kostkon said:**
> There is PulseAudio Equalizer. It's not being actively developed anymore, but it works just fine.

Check [here]("http://www.webupd8.org/2011/04/system-wide-pulseaudio-equalizer.html").

If you don't want to add the PPA mentioned in the post, you can grab the .deb file directly from it (and install it by double-clicking on it).

For 11.10:
[https://launchpad.net/~nilarimogard/+archive/webupd8/+files/pulseaudio-equalizer_2.7.0.2-2%7Ewebupd8%7Eoneiric3_all.deb]("https://launchpad.net/~nilarimogard/+archive/webupd8/+files/pulseaudio-equalizer_2.7.0.2-2%7Ewebupd8%7Eoneiric3_all.deb")
For 11.04:
[https://launchpad.net/~nilarimogard/+archive/webupd8/+files/pulseaudio-equalizer_2.7.0.2-2%7Ewebupd8%7Enatty3_all.deb]("https://launchpad.net/~nilarimogard/+archive/webupd8/+files/pulseaudio-equalizer_2.7.0.2-2%7Ewebupd8%7Enatty3_all.deb")

Hope that helps.

Thanks a lot, kostkon! That`s exactly what I was looking for! :D

It does the job pretty well and with very little CPU overhead. Awesome!

Sorry mods for posting it on the wrong section, I just noticed my mistake.

See ya`ll!

---

