---
title: "DV playback in Totem - xine"
date: 2005-05-05
forum: Desktop Environments
---

### Post by fsman on 2005-05-05
I'm using totem-xine (gstreamer doesn't play dvd's very well).
I'm doing video editing with Kino. However, I can't play the resulting video as totem doesn't seem to have the dvc codec installed.

I get the following error

"Video codec 'dvc ' is not handled. You might need to install additional plugins to be able to play some types of movies"

Any idea how to get totem-xine to place dv codec files?

---

### Post by abies on 2006-06-16
totem doesn't play dv for me either, but mplayer does.  what's up with that?

i guess that means you can convert dv files to something totem will play using mencoder.  that will save some disk space as well.  it took me a while to get the options figured out, and what i eventually settled on is this:

mencoder input_filename -o output.avi -oac mp3lame -ovc xvid -xvidencopts fixed_quant=4 -ofps 24

setting up this stuff was pretty well explained on the Ubuntu Wiki, [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

