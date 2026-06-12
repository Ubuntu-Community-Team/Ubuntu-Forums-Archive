---
title: "Display resolution dosent work"
date: 2011-11-19
forum: Desktop Environments
---

### Post by stewi1014 on 2011-11-19
[FONT=Times New Roman][SIZE=2]hello,[/SIZE][/FONT][SIZE=2]
[/SIZE][FONT=Times New Roman][SIZE=2]I put Ubuntu on an old desktop that was gathering dust in my dad's office and figured it would be cool to plug it to the TV (because i don't have a monitor for it). The TV has a VGA plug and its resolution is 1366 x 768. however when i set the resolution on Ubuntu to 1360 x 768 the display has got this reddish/pinkish tinge to it and the top and left sides are chopped off by 2 cm and there is a 2 cm black gap on the bottom and right sides of the TV. and the closest resolution is 1024 x 768 but that looks super stretched and fuzzy[/SIZE][/FONT][FONT=Times New Roman][SIZE=2]

EDIT: just a link to a display settings program with advanced settings like screen position would help a lot.
[/SIZE][/FONT]

---

### Post by stewi1014 on 2011-11-19
bump.
any one got any ideas?

---

### Post by papibe on 2011-11-19
Hi stewi1014.

Try adjusting the TV settings with the remote. Most TVs have options to crop/zoom the signal.

What is your graphic card?
What is your TV brand and model?

Regards.

---

### Post by stewi1014 on 2011-11-20
TV brand is JVC and model is lt-z37sx5
graphic card is Asus n13219 d33005

i did some research and found the TV only supports the resolutions 1024 x 768 and 800 x 600 on the VGA plug
:(

i also just swapped out the old computer that i connected to the TV and replaced it with a better one that was hosting my servers (i put the specs for the new one on top of post). i am now just screwing around with the s-video plug on the video card, i may be getting somewhere but quite slowly...

EDIT: s-video dosent work, altho it is not stretched, all the sides are chopped off by about 20 pixels.

---

### Post by papibe on 2011-11-20
I'm afraid S-Video is just a bit better that RCA cables. I think it has a resolution limit is 1024x768.

Regards.

---

### Post by stewi1014 on 2011-12-07
i guess ill put up with the fatness until we get a new TV...

---

### Post by mcduck on 2011-12-07
> **papibe said:**
> I'm afraid S-Video is just a bit better that RCA cables. I think it has a resolution limit is 1024x768.

Regards.

Much less than that, it's 640x480, interlaced video at 60Hz. Not something you'd want for desktop use, only for watching a movie or something.

(You will probably get an option for resolutions up to 1024x768 when using analog video connectors like composite or s-video, but that's just to allow you to maintain an usable resolution for your desktop when mirroring it into the TV. The actual video is then just scaled down to the analog TV resolution the S-Video is actually able to handle)

Anyway, what comes to the original topic of the thread, image position is pretty much something the TV itself should handle. Also pretty much every TV with a compute rinput also has a specific mode that displays the image exactly in it's original form, without any processign or scaling done by the TV itself. Using that mode and the 1360x768 should give pretty much perfect image (the 6-pixel black area you'll get that way is too small to be noticeable).

However the pinkish color issue sounds a bit more problematic, if the TV's own color settings aren't able to correct the colors then it's most likely either because of broken VGA cable, or broken connector on either the computer or the TV. Try with another cable, if possible.

---

