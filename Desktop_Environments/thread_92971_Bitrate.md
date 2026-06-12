---
title: "Bitrate"
date: 2005-11-20
forum: Desktop Environments
---

### Post by lucidite on 2005-11-20
Hey,

I have to re-rip all my cds & have to do it in mp3 format since that's the only thing that my portable CD player accepts. I've run into 2 problems with using Sound Juicer:

1) Even with the mp3 command line added & the 128 bitrate put into it, all my tracks are approx. 32 kpbs when they're ripped. Is that normal?

2) The speed of ripping is only at 0.6x. I tried the "apt-get abcde" but it doesn't seem to make any difference. 

Anything that could help me?

---

### Post by daller on 2005-11-21
have you tried kaudiocreator?

---

### Post by lucidite on 2005-11-21
No, I didn't because. What do I have to put in the command line so that I can rip in mp3 format?

---

### Post by daller on 2005-11-21
[QUOTE=lucidite]No, I didn't because. What do I have to put in the command line so that I can rip in mp3 format?[/QUOTE]

kaudiocreator has a GUI frontend!

You just have to install "gstreamer0.8-misc" and "gstreamer0.8-mad"

...And then choose "lame" as the ripper in kaudiocreator...

---

### Post by lucidite on 2005-11-22
Thanks! It worked.

And sorry for the previous post -- the first sentence was supposed to be "No, I didn't because I haven't been able to figure out how to configure it". Stupid me trying to play with computer late at night... 

Thanks again!

---

