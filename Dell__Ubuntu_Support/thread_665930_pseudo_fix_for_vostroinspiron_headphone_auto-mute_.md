---
title: "pseudo fix for vostro/inspiron headphone auto-mute problems"
date: 2008-01-12
forum: Dell  Ubuntu Support
---

### Post by ACGarib on 2008-01-12
Hi, sorry if this was already posted somewhere, but I figured out how to get sound to output to either headphones or external speakers/ amplifiers without the internal speakers for my Vostro 1500.

First, I typed: ```
gnome-volume-control
``` then went to File, change device, and made sure HDA Intel was selected instead of Sigmatel.

I then went to Edit, preferences, then enabled every option.

A new tab called switches should appear. Go there and check "line in as output".

Go back to the playback tab and make sure surround isn't muted and slide the slider up about 3/4 the way up.


Plug your amplifier or headphones into the microphone audio jack.

Now for the test. Play some music and hit mute. Hopefully the music should keep on playing on the amplifier/ headphones but be muted on the internal speakers.


The only problem with this is the treble is way too high and the bass is almost non-existent on my headphones. This makes my headphones sound like cheap earbuds. It is fine for podcasts and videos though. 

It sounds fine on my stereo. (I haven't done any comparison tests yet, but the one song I listened to sounded like it always has)


An added bonus: NO MORE STATIC!!!
Whenever I was listening to music on my stereo and there was a quiet part, I used to hear some static whenever the hard drive did something, but now it is gone.


I hope this has helped someone,

ACGarib

---

