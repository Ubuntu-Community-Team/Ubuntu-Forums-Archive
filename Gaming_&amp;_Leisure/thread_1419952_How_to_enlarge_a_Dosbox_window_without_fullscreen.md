---
title: "How to enlarge a Dosbox window without fullscreen?"
date: 2010-03-02
forum: Gaming &amp; Leisure
---

### Post by learningcurb on 2010-03-02
Hi, I'm trying to play some games in Dosbox in windowed mode, but with a larger window.  I don't want to use fullscreen because then I can't switch between the Dosbox session and email and web browser without a lot of hassle.

I did some searching for advice such as [http://www.reloaded.org/forum/index.php?showtopic=753](http://www.reloaded.org/forum/index.php?showtopic=753) and [http://www.gog.com/en/forum/tex_murphy_series/can_i_resize_the_dosbox_window](http://www.gog.com/en/forum/tex_murphy_series/can_i_resize_the_dosbox_window) but tweaking scaler, output or hwscale options doesn't seem work on my machine.  So what settings do I need to change? :\  Thanks.

---

### Post by molokaicreeper on 2010-03-03
Have you consulted the DosBox Wiki?  Maybe you can find it there?

[http://www.dosbox.com/wiki/Dosbox.conf#Sections](http://www.dosbox.com/wiki/Dosbox.conf#Sections)

Since you're not specifying what computer you're using, I guess not much help can be given, sorry.  Here is another page that may help (see "VIDEO" section):

[http://vogons.zetafleet.com/viewtopic.php?t=10739](http://vogons.zetafleet.com/viewtopic.php?t=10739)

I hope that works with your machine, good luck!

Liliana

---

### Post by learningcurb on 2010-03-03
Hey again. Thanks for the [http://vogons.zetafleet.com/viewtopic.php?t=10739](http://vogons.zetafleet.com/viewtopic.php?t=10739) link.  I took another look at the configuration file after using config -writeconf to write it out a fresh file.  It turns out that windowresolution was the variable I forgot to change. I changed the following settings and now it works:

```

windowresolution=1024x768
output=opengl
hwscale=2.00

```

And here's the full [sdl] section of my .dosboxrc:

```
[sdl]
# fullscreen -- Start dosbox directly in fullscreen.
# fulldouble -- Use double buffering in fullscreen.
# fullresolution -- What resolution to use for fullscreen: original or fixed size (e.g. 1024x768).
# windowresolution -- Scale the window to this size IF the output device supports hardware scaling.
# output -- What to use for output: surface,overlay,opengl,openglnb.
# autolock -- Mouse will automatically lock, if you click on the screen.
# sensitiviy -- Mouse sensitivity.
# waitonerror -- Wait before closing the console if dosbox has an error.
# priority -- Priority levels for dosbox: lowest,lower,normal,higher,highest,pause (when not focussed).
#             Second entry behind the comma is for when dosbox is not focused/minimized.
# mapperfile -- File used to load/save the key/event mappings from.
# usescancodes -- Avoid usage of symkeys, might not work on all operating systems.

fullscreen=false
fulldouble=false
fullresolution=1024x768
windowresolution=1024x768
output=opengl
hwscale=2.00
autolock=true
sensitivity=100
waitonerror=true
priority=higher,normal
mapperfile=mapper.txt
usescancodes=true
```

---

### Post by learningcurb on 2010-03-03
Hmm, actually hwscale seems to be unnecessary.  I was wondering why it didn't appear in the default configuration file.  Anyway, it seems that windowresolution is the main variable.  Also, output needs to be set to overlay or opengl. Scaling won't work when output is set to surface.

Another related link: [http://vogons.zetafleet.com/viewtopic.php?t=8591&postdays=0&postorder=asc&start=20&sid=759f5bc212eb4cb77b16945445edf3de](http://vogons.zetafleet.com/viewtopic.php?t=8591&postdays=0&postorder=asc&start=20&sid=759f5bc212eb4cb77b16945445edf3de)

---

### Post by zarnivop2 on 2012-12-13
This thread is gold. I was looking for this answer for quite a while! Thanks, everyone. Love from Israel! :love:

---

### Post by Nightcaper on 2013-04-18
This helped me with a problem only somewhat related with DOSBox, and taught me to pay more attention to configuration settings. Thanks!

---

