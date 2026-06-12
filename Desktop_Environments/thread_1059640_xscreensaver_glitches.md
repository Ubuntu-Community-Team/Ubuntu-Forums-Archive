---
title: "xscreensaver glitches"
date: 2009-02-03
forum: Desktop Environments
---

### Post by PhilCash on 2009-02-03
G'day All,

Perhaps I originally posted in the wrong forum as there were no replies, so I'll try this forum.

Running 8.10 and exasperated with the inability to configure the gnome screensaver to display my photo collection in other than 10 second flash card format through f-spot; I have installed xscreensaver and am using GLSlideshow to do the job.

But...there always seems to be a 'But' doesn't there? But, each transition between photos is spoiled by being accompanied by a series of text messages along the lines of:
constant subroutine main::S_IWGRP redefined at /usr/bin/xscreensaver-getimage-file line 38

Can anyone advise me how to:
1. keep using xscreensaver and get rid of the error messages,
2. alter the gnome/f-spot screensaver configuration settings,
3. set the gnome screensaver/GLSlideshow to use photos from my directory, or
4. setup some screensaver to display photos from selected directories with my choice of display duration, transition etc.

Cheers,
Phil

---

### Post by PhilCash on 2009-02-06
An update:

I have prevented the text messages from being written to the screen by editing the .xscreensaver file in my home directory and setting the captureStderr and overlayStderr parameters both to False.

This hides the problem, but I still notice a hesitation when xscreensaver-GLSlideshow loads each new image, particularly for large (500kb+) images. I suspect that there is still a minor problem under the surface but have little idea as to how to resolve it.

Cheers,
Phil

---

