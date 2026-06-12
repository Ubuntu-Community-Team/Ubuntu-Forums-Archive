---
title: "OGG Tag support &amp; amarok"
date: 2005-10-18
forum: Desktop Environments
---

### Post by sneakerski on 2005-10-18
Hello guys, new ubuntu user/forum member

Just a little background about myself, i've been an linux-only user for about 20 months now, and had to try out Ubuntu to see what all the rage was about (I'm a gentoo guy at heart).

OK, now my questions:
first off, this is a fresh breezy install
I added the non-copyright-friendly repo but keep it disabled unless i'm installing media-based stuff

I installed amarok, and it flashes the logo but crashes. Played around with gstreamer and xine configurations, can't get it to start. any suggestions? (this is my favorite music player, nothing else comes close)

In my hunt for something close to amarok, i found Banshee. But the default dependencies/build is cool enough to not support ogg-tag reading (wtf?). Any help there? (just for reference, Muine and Rhythmbox read ogg tags just fine)

another thing, easytag doesn't support ogg tag editing? (wtf?) but i think that's something that should be reported to the devs, not some kind of broken dependency. (i miss my USE flags, but the quick installs are quite nice :???: ...can't win)

thanks everybody

---

### Post by Dr. Nick on 2005-10-18
I can be of some help, also the messanger of some bad news.

amaroK doesnt seem to work for many who uses the precompiled version, I had trouble and a quick search will show alot of other trouble over the past few days, Ive heard using the CVS is better but havent gotten around to it yet so cant vouch or it personally.

About Easy Tag, what version do you have? My 1.99.7 seems to handle ogg tags just fine. If you cant get it for some reason then install tagtool from synaptic, its a pretty good app for mp3 and ogg tags and works for me aswell.

Heres to hoping a new amaroK of solution to our problems happens soon, best alternate I found is Quod Libet, Reminds me of RythmBox but on steroids :)

I played with gentoo, one thing that looked real cool about it was the USE Flags, would be nice if their was some way to compile amaroK against gtk aswell as qt so it looked more uniform. MY expierence is limited since I tried Stage 1 and it took forever :)

---

### Post by sneakerski on 2005-10-19
hmm, yea
i finally got amarok to build, geez, what a mess that was.
my custom built version works, thankfully, after all the trouble i went through to build it :)

---

