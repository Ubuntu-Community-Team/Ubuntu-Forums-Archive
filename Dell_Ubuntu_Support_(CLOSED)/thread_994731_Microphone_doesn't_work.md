---
title: "Microphone doesn't work"
date: 2008-11-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aklofas on 2008-11-27
Both internal/external microphone doesn't work. This has been a long standing issue from way back to 8.04. There seems to be a fix at [http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-hardy-lum.git;a=commit;h=f323b03701097f485540e876d27be5cf29820229](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-hardy-lum.git;a=commit;h=f323b03701097f485540e876d27be5cf29820229) WTF! Why is this *still* an issue!

Andrew

---

### Post by supermikey on 2008-11-28
Had the same problem. Download the alsa-firmware from medibuntu and then go to volume control and make sure to add capture, capture 1, capture 2, digital, mux, mux 1, and mux2 to your options (I don't know why, but until I had unmuted all of these and turned them up, my mic didn't work either). Make sure that digital input source is digital mic 1, Input source #1 is Mic, #2 & #3 are front mic. Again I don't know if this just cause my 1420n is messed up or tweaked something somewhere, but mine won't work unless I leave them with these settings exactly. FTW. Included screenshots. Hope this helps!!

---

### Post by skyline_GT_R34 on 2008-12-12
Fantastic! So simple a "procedure" (!) finally succeeds for me in fixing this ("last") annoying issue that remains in my list of bugs/not working things!! 

I only have the capture and the digital inputs and not the mux(es), even if the card is an Hda intel, too, but that's it!

Thank you very much! ;)

---

### Post by skyline_GT_R34 on 2009-01-02
I have to do a remark: this "method" worked for me only the first time and I don't know why, now :?:.
Anyway, the ultimate solution has been to enable PulseAudio :P for the entire sound capabilities (playback and recording)!!! and restarting ubuntu...
In fact in spite of all the tweaks I made in alsamixer or with the 'volume icon gui' I obtained nothing entirely working (for example I had audacity not signalling any error, and recording, but not playing...).
So unlike many people in trouble with pulseaudio and wanting to remove it, it was my safety!! ;)

---

