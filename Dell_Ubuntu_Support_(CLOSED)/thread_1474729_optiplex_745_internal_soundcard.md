---
title: "optiplex 745 internal soundcard?"
date: 2010-05-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by thinking on 2010-05-06
hi all

i did an update to 10.04 lucid and i have the following problem on my
dell optiplex 745

technically i think the sound driver works better than before
im using headphones all the time which worked before the update without
a problem
the headphones itself work as usual but it seems that the optiplex itself
has a built in speaker
thus if i increase the sound volume music im listening too can also be heard
from the optiplex itself
until lucid i didnt event know that such hardware is built into the box

btw: it really sounds like the music i hear and not some old 8-bit game speaker music

so anyone has an idea whats the problem or how i can solve this?
i only want my headphones to play but not the box itself

thx all


[solution]
i installed "gnome alsa mixer" and changed a few sliders
dont know which one did the trick or why cause it seemd not working at the beginning
but gnome alsa mixer helped

---

### Post by thinking on 2010-05-07
bump

---

### Post by dfehrer on 2011-05-05
Thanks thinking, that worked great!  I was having the same problem with my Optiplex 745 running Ubuntu 10.04.

It appears the specific slide you have to turn up in ALSA Mixer is the "Mono" slide.  I'm pretty new to Ubuntu so I don't really know what I'm talking about, but it could be because the default driver/sound output is for Stereo, which somehow doesn't jive with the internal speaker, which must be Mono.

For other noobs like me, here's what I typed into the terminal to get ALSA Mixer:

sudo apt-get install gnome-alsamixer

Then I just opened it in the Applications dropdown and turned the Mono slider up and off mute and viola! Sweet.

---

### Post by MakavelliRo on 2011-05-13
Did any of you have problems like no sound, in the previous versions?

---

### Post by jamesknight on 2012-01-04
Yes that works absolutely fine on my dell optiplex 745 with ubuntu 10.04 LTS. thanks heaps for posting this.. googling at other places did not help..

---

