---
title: "No Audio on new Aspire One 10inch (D150) 9.04"
date: 2009-02-15
forum: General Help
---

### Post by DrLegoHair on 2009-02-15
I just purchased a new 10" AA1 and got Ubuntu 9.04 running on it easily (installed using an old SD card).  I actually have everything working nicely except the audio.  I get no sound at all.  I have downloaded the latest ALSA drivers, compiled and installed them to no avail.  I have edited /etc/modprobe.d/options.

When I to select the proper audio device in system>preferences>sound and hit test I get the following error

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback.

Any help is much appreciated.

Thanks

---

### Post by johnjohn2 on 2009-02-15
Have you tried pulse sound server?

If not might be worth a go!

Maybe you could try Intrepid as it is not bleeding edge things may work a little better.


Regards John

---

### Post by DrLegoHair on 2009-02-15
Tried pulse, no luck.
Loaded intrepid before jaunty but had lots of problems with it.  Jaunty works great except for audio!

---

### Post by russu52 on 2009-02-16
i suggest using linux4one (based on ubuntu 8.04). i have installed it on an 8.9" aspire one. everything works except xd card. i did as follows:

download linux4one (from [www.linux4one.it](www.linux4one.it)) it is actually an italian site, but has an english translation. download also the update.

install linux4one, and the update.

adjust to your taste - desktop, icons, etc.

note that linux4one is lightweight for the ssd versions, so you will have to do some settings. it's all gui, and since i am hopeless, and i managed, so everyone can!!

---

