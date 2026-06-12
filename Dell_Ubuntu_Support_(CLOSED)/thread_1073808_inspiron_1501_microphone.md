---
title: "inspiron 1501 microphone"
date: 2009-02-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pateu on 2009-02-18
hi there. i have a problem with my inspiron 1501 microphone jack and after 2 days of forum searching and trying many solutions without any problem solving, i decided to start a thread.
so, i'm running ubuntu 8.10. there were a lot of people complaining that they couldn't record, but my problem is another one. i CAN record, i can even use skype, but i can't hear what i'm saying. the thing is that i want to play the electric guitar through the laptop and headphones, and it's really important that i hear the microphone playback.
the sound card is SigmaTel STAC9200. i tried to append **options snd-hda-intel model=dell-m26** into /etc/modprobe.d/alsa-base and /etc/modprobe.d/options, but still not working. i also tried to type alsamixer in the terminal and fool around with the volumes, but still no result. in order to get the HDA Alsa mixer i had to type **alsamixer -c 0**. 
i hope there is a solution to this, i would really hate to give up ubuntu just for this problem (although i'm 4-days new, i'm really starting to like it and get used to it). thanks

in the mixer from the panel, on the recording tab there is the Capture volume. every time i open the mixer, it is muted (the icon with the microphone representing the "toggle audio recording from capture" option. even though i enable it, after i close and reopen the mixer, it is muted again. does this have anything to do with my problem?

---

