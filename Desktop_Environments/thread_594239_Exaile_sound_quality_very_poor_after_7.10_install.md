---
title: "Exaile sound quality very poor after 7.10 install"
date: 2007-10-27
forum: Desktop Environments
---

### Post by davebgimp on 2007-10-27
I've used Exaile for good long while with no problems. However, I've noticed with 7.10, I'm getting very muted sound from it. I compare a track's quality in Exaile against Rhythmbox and VLC and find that there's really a pretty strong quality loss as far as volume. I've checked my settings, putting exaile to use alsa and everything else I could think of but every other program I use plays a track 2-3 times louder and with much more quality. Has anyone else noticed this or perhaps fixed it? I'd hate to have to stop using Exaile. It's treated me well for while now.

---

### Post by TeaSwigger on 2007-10-28
My usual disclaimers about being a long ways from an expert, and I've never seen nor used Exhaile, but sound quality loss would drive me bonkers. Hm. So you've set it to alsa, that's good. My first hunch is: are there any reprocessing "enhancement" features enabled? Or anything which may involve such, like having it set to mixdown or something other than stereo 2.0. If so get rid of them. Double check you're getting the real unmolested signal piped to the mixer. Hm second idea: what is it using in the "mixer" (gnome volume control? kmix? alsamixer?), and can you set that? Third, check all the "mixer" settings. Luck fixing it so you can enjoy your favorite audio player.

---

### Post by davebgimp on 2007-10-28
Believe me, I'm hitting all the settings I could find in exaile, alsamixer, gstreamer-properties, etc. For some reason (and this is recent to the 7.10 release), the sound is very sub-par.

---

### Post by davebgimp on 2007-10-28
Further fooling around has not fixed the problem, but I have narrowed it down to bass. Exaile is giving me really crappy bass while in any other program, it's exactly as it should be. Can't figure out why. :confused:

---

### Post by Fli on 2007-10-28
This happened to me with mpd and ncmpc. The problem was that the software volume was set too high and was distorting. I put that down to about 80% and it works fine for me.

---

### Post by FG123 on 2007-10-29
FIX: Straight from the Exaile home page: [http://www.exaile.org/](http://www.exaile.org/)

If you use this release on Gutsy, you may noticed lower than usual volume limits. This is because of the equalizer in the gst-plugins-bad package (we&#8217;re not quite sure why yet). If you aren&#8217;t happy with the volume you are getting, you can try turning the equalizer all the way up, or start exaile with the --no-equalizer option.

So, running **exaile --no-equalizer** should do the job. I've had the problem before.

---

### Post by davebgimp on 2007-10-29
Thanks for your help, that does seem to have made a very noticeable difference.

---

### Post by phenest on 2007-11-11
One of the reasons for using Exaile (which I prefer over Rhythmbox) was the equalizer. Will this ever be fixed?

---

### Post by phenest on 2007-11-11
Ok. I see Exaile and gstreamer bad is fixed, but when does this make it to Gutsy? I guess I'll have to do a manual install

---

### Post by mister harbies on 2008-01-04
I found a work around to up ALL the tabs on the equaliser to 20db. I am Deaf, and I i use this as a gauge as a maximum for those who are not Deaf. I think Exaile has the maximum right.... so for those who are complaining about the sound volume.... maybe check with an ear specialist.... you might have lost some hearing?


Yo?

---

